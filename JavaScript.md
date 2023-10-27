# JavaScript
-  ## 엄격모드
     -JavaScript의 엄격 모드는 JavaScript에서 느슨한 모드를 해제하고, 제한된 규칙과 표준을 따르도록 하는 설정 방법이다.

     -엄격모드를 사용하기위한 구문은 "use strict"(또는'use strict') 쓰고 다른 구문을 작성하기 전에 써야한다.

    
    -⚠주의할점 반드시 최상단에 위치시켜야한다.
    그렇지 않으면 엄격모드가 실행되지 않을수도 있다. 그리고 use strict위에는 주석만 가능하다.

    -만약 브라우저 콘솔에서 "use strict" 모드를 활성화하려면 "use strict";을 입력하고 Shift+Enter를 누르거나 코드를 함수 래퍼로 감싸면 된다.

    -사용예시
    ``` javascript
    "use strict";
     ...
    ```
- 함수에서 strict선언

    ``` javascript
    (function() {
    'use strict';
    ...
    })()
    ```
- ## 변수
   -변수에는 var,let,const 3가지종류의 변수가있다. 한번 각변수에대해 알아보자.


   ## var
- var는 '변하는 수' 즉 데이터를 나타내며, 변수를 선언하고 초기화할 수 있으며 중복 선언이 가능하다.
  
  _var의 중복선언은_
  ``` javascript
  var x = 1;
  var y = 1;

  var x = 50;
  var y = 0;
  console.log('x : ', x) 
  console.log('y : ', y)
  ```
  이런식으로 나타낼수 있는데 설명을하자면 처음에x에서 1선언을 한 상태에서 x에50을 또 선언할수가 있다.그럼 출력은 x = 50과y = 0이나온다.
  
- 함수 레벨 스코프
  > var의 특징중 함수레벨 스코프는 var 변수를 블록 밖에서 만들면 어디서나 쓸 수 있는 전역 변수가 된다.

  ``` javascript
  var x = '원래 값';

  if (true) {
    var x = '변경된값';
  }

  console.log(x); // 변경된값
  ```
  이런식으로 var로 선언된 x가 코드블록에서 선언된 모습이고 x는 전역변수로 인식되어 또다른 값으로 재할당 되는 상황이다.

- 변수 호이스팅
  > 변수 호이스팅이란 
   자바스크립트에서 변수 선언문을 코드의 맨 위로 끌어올려져서 먼저 처리되는 자바스크립특의 특징이다.

  -사용예시
  ``` javascript
  console.log(name) // undefined
  var name = 'A'  
  ```
  위에 코드를 보면 name을 출력하는데 에러가 안나고 defined가 뜬다.
  왜냐하면 실행시점에 호이스팅이되어 var변수가 최상단에 선언되기 떄문이다.

  ``` javascript
  var name; 실햏시점에서 호이스팅되어 최상단에 위치함
  console.log(name)
  name = 'A'

  ```
  호이스팅에 단점으로는 코드의 동작을 예측하기 어렵게 만들어 가독성과 디버깅을 어렵게 할 수 있는 단점을 가지고있다.

   ## let
- 변수 중복 선언 불가
  > let과 var의 차이중 하나는 중복선언이 불가능 하다는것이다.
  ``` javascript
  let x = 1;
  let x = 4;
  ```
  이런식으로 중복해서 쓸수가 없었어 에러가난다.
- 블록 레벨 스코프
  > 코드블록 내에서선언된 변수는 코드블록 내에서만 유효하고 코드블록 외부에서는 참조할수없다. 한만디로 코드블록 안에 선언한 변수는 지역변수이다.

  ``` javascript
  let aaa = 123; // 전역 변수
  {
  let aaa = 456; // 지역 변수
  let bbb = 456; // 지역 변수
  }

  console.log(aaa); // 123
  console.log(bbb); // is not defined
  ``` 
  위에코드와 같이 전역변수 aaa를 설정하고 {} 내에서 aaa와bbb를 설정한후 
  aaa를 출력하면 전역변수값이 출력되고 bbb는 참조할 수 가없어 에러가걸린다.

- 호이스팅
  > let 호이스팅은 var와 달리 let키워드로 선언된 변수는 선언문 이전에 참조하면 참조에러가 발생한다.왜냐하면 let 키워드로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(Temporal Dead Zone; TDZ)에 빠지기 때문이다.

  ``` javascript
  let aaa = 1; // 전역 변수
  {
  console.log(aaa); // ReferenceError: aaa is not defined
  let aaa = 2; // 지역 변수
  }
  ```
  위에코드에서 전역변수 aaa와 지역변수 aaa기ㅏ 모두 let으로 선언되었기 때문에 지역변수 aaa가 호이스팅되면서일시저 사각지대(TDZ)에 빠진다.      따라서 전역변수 aaa의 값은출력되지 않고 참조 에러가 뜬다.
  
  ## const 
-  중복 선언과 재할당 불가능
   > const는 한 번만 선언하고 재할당을 통해 바꿀수없다.
   
     코드를 보고 자세하게 설명하자면 
    ```javascript
    const name = 'A';
    console.log(name); //A

    const name = 'B';
    console.log(name);//Identifier 'B' has already been declared
 
    name = 'C';
    console.log(name);// Assignment to constant variable

    ```
    첫번쨰 name에서 A를 초기화해서 이부분은 잘 작동된다.하지만 이미 위에서 선언된 name변수를 또 다시 선언하려고 하는데 const는 재선언이 불가능 하므로 오류가 뜨고 마지막 줄에서는 name에 C라는 새로운 값을 재할당을 해서 오류가난다 이유는 const에서 재할당도 불가능하기 떄문이다.

- 블록 레벨 스코프와 호이스팅은 let과 유사하다.

- ## 상수
  상수는 반복 숫자 값을 정의해 오류를 줄이며 코드를 명확하게 만든다.
- ## const 상수선언
   const는 변수를 선언하는데 사용되며 한 번 선언한 후에 값의 변경이나 재선언이 불가능한다. 주로 값이 변경되어서는 안 되는 상수나 함수 선언에 사용된다.
   
   또한 상수를 선언할떄 상수임을 구분할수있도록 대문자나 언더바를 이용해서 표기한다.

   ```javascript
   const PI = 3.14;
   const A = 12.5;
   ```
- ## UI Event
  대표적인 event 종류인,Keyboard Event,Mouse Event,Focus Event,Blur Event,Form Event에 대해 알아보자

  ## Keyboard Event
- 키보드 이벤트는 사용자가 키를 누르거나 놓을 떄 발생하는 이벤트이다.<br>
  키보드 이벤트의 종류로 keydown,keyup,keypress가 있는다.
  > keydown:키를 눌렀을떄 발생하는 이벤트이다.<br>
  > keyup:키를 눌렀다 떼었을떄 발생하는 이벤트이다.<br>
  > keypress:키를 누를 때와 떼는 순간 모두 이벤트가 실행되며, 문자 입력과 관련된 키에 대한 이벤트이다.

  코드는 이런식으로 사용하면 된다.
  ```javascript
  document.addEventListener('keydown', function(event) {
  if (event.keyCode === 13) {
     alert('Enter 키가 눌렸습니다.');
  }
   });
  ```

  이런식으로 적으면 되고 keydown 부분에 keyup이나keypress 을 바꿔서 쓰면된다.그리고 여기서 addEventListener는 이벤트 핸들러를 등록하고
   이벤트를 처리하기 위한 메서드이다.

  몇가지 Keyboard Event를 설명하자면 
   > keyCode:키보드에서 눌린 키의 ASCII 코드 값을 나타낸다.<br>
     charCode:문자 키가 눌렸을 때 해당 문자의 유니코드 코드 포인트를 나타내는 속성이다.<br>
     ctrlKey, altKey, shiftKey,metaKey 이것들은이 키를 누르면 true를 반환을 한다.

  ## Mouse Event
- 마우스 이벤트는 mouseEvent 객체에 등록된 html 요소와 마우스가 상호작용했을 때 발생하는 이벤트이다.
  > mousedown,mouseup:요소 위에서 마우스 왼쪽을 누를 떄,마우스 버튼 누르고 있다가 뗄떄 발생한다.<br>
  mouseover,mouseout:마우스 커서가 요소 바깥에 있다가 요소 안으로 움직일 때 커서가 요소 위에 있다가 요소 밖으로 움직일 때 발생한다.<br>
  mousemove:요소에서 마우스를 움직였을떄 발생한다.<br>
  click:요소를 클릭했을떄 발생한다.<br>
  dblclick:요소를 더블 클릭했을떄 발생한다.<br>
  contextmenu:마우스 오른쪽버튼을 눌렀을떄 발생한다.

- 마우스 버튼<br>
  > 마우스 클릭 관련 이벤트에서는 어떤 버튼이 사용되었는지를 알려주는 button 프로퍼티를 사용한다. click은 왼쪽 contextmenu는 오른쪽버튼을 나태낸다.

  >그래서 button프로퍼티는 click,contextmenu 이벤트에는 사용하지않고 mousedown,mouseup 이벤트를 다룰 때 어떤 마우스 버튼을 사용했는지 정확하게 파악하려면 event.button을 이벤트 핸들러에서 사용해야 한다.<br>
  이런 이벤트에서는 여러 마우스 버튼을 사용할 수 있고, button 프로퍼티를 이용하여 어떤 버튼이 동작했는지 정확히 파악할 수 가있다.
- shift, alt, ctrl, meta 프로퍼티
   >마우스 이벤트는 이벤트가 발생할 때 함께 누른 보조키가 무엇인지를 알려주는 프로퍼티를 지원한다. 지원하는 보조키로는 shiftKey,altKey,ctrlKey, 이와같다. 이런한 키가눌려있으면 프로포티 값은'true'가되고 이것을 활용하여 특정 행동을 제어할 수 있다.

   -사용예시
   ```javascript
    button.onclick = function(event) {
    if (event.ctrlKey && event.shiftKey) {
      alert('와우!');
    }
   ```
   이런식으로 쓰면 ctrl+shift키와 마우스 왼쪽 버튼을 같이 클릭했을떄만 작동을한다.
- screenX,screenY
   > 사용자 모니터 화면으로 좌표를 나타내고 모니터 왼쪽 상단이 (0,0)이다.
- pageX,pageY
   > 전체 문서를 기준으로 좌표를 표시하고 페이지 스크롤에 영향을 받아 위치가 변할 수 있다.
- clientX,clientY
   > 웹 페이지가 표시되는 브라우저 화면 영역을 기준으로 좌표를 표시한다.  그렇기에 스크롤바가 움직여도 clientX,clientY의 값은 동일하다.
- offsetX, offsetY
   > 이벤트가 발생한 DOM 요소를 기준으로 좌표를 나타내고. 해당 요소의 왼쪽 상단 모서리 부분의 offsetX, offsetY의 값은 (0, 0)일 것이다.

  ## Focus,blur Event
-  focus 이벤트는 요소가 포커를 받을떄 발생하고 blur는 포커스를 잃을때 발생한다. 또 elem.focus()를 사용하면 요소에 포커스를 주고 elem.blur()를 사용하면 요소의 포커스를 제거할 수 있다.<br>
  
   -사용예시
   ```javascript
     const myInput = document.getElementById('myInput');
       myInput.onfocus = function() {
      alert('입력 필드에 포커스가 맞춰졌어요!');
    };
   ```
   blur : blur핸들러는 이메일이 올바르게 입력되었는지 확인하고, 에러 메시지를 표시한다.<br>
     focus: focus 핸들러는 에러 메시지를 숨겨주고 이메일이 올바르게 입력되었는지 확인하는 작업은  blur 핸들러에서 이루어진다..
 -  focusout event는 이벤트 요소가 포커스를 잃을려소 할떄 실행되는 이벤트 핸들러이다. 그럼 blur이벤트랑 같은거라 생각할수있는데 이 둘의 차이점은  blur 이벤트는 버블링이 되지않지만 focusout이벤트는 버블링이 된다는점이다.

     그렇다면 여기서 버블링이 무엇인지 궁금해 할텐데 버블링 이란 이벤트가 발생한 요소부터 부모 요소를 거슬러 올라가면서 계속 전파되는 것을 의미한다. 이것은 마치 물속에서 거품이 아래서부터 위로 올라가는 것과 비슷한 동작을 한다.
    ## Form Event
  -  Form Event는 HTML 폼 요소와 관련된 이벤트로 사용자가 폼을 작성하거나 제출할 때 발생하는 이벤트이다.r그럼 form event의 조유에대해 알아보자.
  - submit
    > 폼이 제출될 때 발생하고 이벤트 핸들러를 사용하여 폼 데이터의 유효성을 검사하고 서버로 데이터를 제출할 수 있다.
  - reset
    > 폼이 재설정될 때 발생한다. 이벤트 핸들러를 사용하여 입력된 데이터를 초기 상태로 되돌릴 수 있다.
  - change
    > 폼 요소에서 값이 변경될 때 발생한다.주로 select,checkbox,radio 등에서 사용자의 선택을 감지하거나 입력 필드에서 값 변경을 감지하는 데 사용된다. 
  - input 
    > 폼 요소에서 값이 입력될 때 발생한다. 주로 입력 필드에서 사용자의 텍스트 입력을 실시간으로 처리하는 데 사용된다.
  - focus 
    > 폼 요소에 포커스가 갔을 때 발생하고 이벤트 핸들러를 사용하여 사용자가 폼 요소에 집중할 때 추가 동작을 수행할 수 있다.
  - blur 
    > 폼 요소에서 포커스가 벗어날 때 발생하고 이벤트 핸들러를 사용하여 사용자가 폼 요소를 떠날 때 추가 동작을 수행할 수 있다.

    -사용예시
    간단하게 submit을 사용하여 자바스크립트 코드 예시만 보여주자면
    ```javascript
        document.getElementById('myForm').onsubmit = function() {
          alert('폼이 제출되었습니다.');
          return false;
        };
    ```
    그럼 위에 코드를 보면 myForm이라는 ID를 가진 form 요소를 찾고 onsubmit은 HTML 폼 요소에서 발생하는 이벤트로 폼이 제출될 때 실행할 함수를 정의함으로서 폼이 제출되었습니다 가 출력되고 마지막에 return false는폼 제출시 페이지의 새로고침을 방지하기 위해 사용되었다.
  
    