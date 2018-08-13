# SampleIntent

#### Intent 클래스를 사용하여 Activity간에 데이터를 주고받는것이 가능하며 간단한 예제를 작성하였다.

##### 1.데이터를 주고받기 위해서 **요청코드**를 정의해야한다.
```java
  public static final int REQUEST_CODE_MENU = 101;
```
##### 2.startActivityForResult 함수에 **요청코드** 넣어 Activity를 생성한다.
```java
startActivityForResult(intent, REQUEST_CODE_MENU);
```

##### 3. 생성된 Activity에서는 종료되기 전에 Intent를 생성하여 반환값을 넣고 Activity를 종료한다. 이 때 **RESULT_OK** or **RESULT_CANCELED** 등을 사용하여 정상종료되었는지도 전달해줄 수 있다.
```java
 Intent intent = new Intent();
        intent.putExtra("name", "mike");
        setResult(RESULT_OK, intent);

        finish();
```

##### 4. 호출한 Activity에서는 onActivityResult() 메소드를 overriding해주고 이안에서 **요청코드**와 **RESULT_OK**를 확인하여 반환된 값을 확인할 수 있게된다.
```java
if(requestCode == REQUEST_CODE_MENU) {
      Toast.makeText(getApplicationContext(),
        "onACtivityResult 메소드 호출됨, 요청 코드 : " + requestCode +
      ", 결과코드 :" + resultCode, Toast.LENGTH_LONG).show();

      if(resultCode == RESULT_OK) {
        String name = data.getExtras().getString("name");
        Toast.makeText(getApplicationContext(), "응답으로 전달된 name : " + name, Toast.LENGTH_LONG).show();
      }
    }

```

