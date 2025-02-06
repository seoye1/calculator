## The challenge

바닐라 js로 만드는 계산기

![](./계산기.gif)

## What I learned

### ✅`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

웹페이지가 모바일 환경에서도 적절하게 표시되도록 설정

📍 주요 속성

- width=device-width → 뷰포트(화면 너비)를 디바이스의 화면 너비에 맞춤
- initial-scale=1.0 → 초기 확대/축소 배율을 1.0(기본 크기)로 설정

### ✅ readonly

읽기 전용 텍스트 입력 필드를 만든다. (텍스트 칸에 입력 불가)

```html
<input type="text" name="output" readonly>
```

### ✅ onclick 이벤트

onclick은 HTML 요소에 클릭 이벤트를 설정하는 속성<br>
사용자가 클릭하면, onclick 속성에 설정된 JavaScript 코드가 실행됨

```html
<input type="button" value="1" onclick="document.forms.output.value+='1'">
```

버튼을 클릭하면, output이라는 이름을 가진 입력 필드의 값에 "1"이 추가됨. (문자열이 결합됨.)

**Q. 왜 =이 아니라 +=를 사용할까?**
A. = 연산자는 값을 단순히 덮어쓰는 방식인데, +=는 기존 값에 새로운 값을 추가하는 방식이므로, 버튼을 클릭할 때마다 기존 값 뒤에 "1"을 계속 추가할 수 있기 때문.

### ✅ eval() 함수

eval()은 문자열로 된 JavaScript 코드를 실행하는 함수
주어진 문자열을 실제로 실행 가능한 코드로 평가해서 실행됨.

📍 문법

```js
eval(string);
```

string: 실행할 JavaScript 코드가 담긴 문자열

📍 예시

```js
<input type="button" class="operator result" value="=" onclick="document.forms.output.value=eval(document.forms.output.value)">
```

사용자가 이 버튼을 클릭하면, 현재 입력된 수식을 계산하고 결과가 표시됨.

---

### ✅ 수직 중앙 정렬

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* 화면 높이에 맞게 부모 요소 높이를 설정 */
}
```
📍 **왜 height가 있어야 하는가?**
display: flex;와 justify-content: center;, align-items: center; 속성은 자식 요소를 부모 요소 안에서 가로와 세로 모두 중앙에 배치하려는 것인데, 이때 부모 요소의 크기가 필요함.
부모 요소의 크기가 정해지지 않으면 자식 요소가 부모 요소의 크기를 기준으로 중앙에 오지 않아서, 부모 요소의 최소 높이를 명시해줘야 함.
height: 100vh;는 뷰포트(화면) 높이의 100%로 설정. 즉, 화면 전체 높이를 부모 요소의 높이로 설정.

📍 **왜 vh를 사용하는가?**
vh는 뷰포트 높이의 **1%**를 의미해. 100vh는 화면 전체 높이를 의미하므로, 부모 요소가 화면 전체 높이에 맞게 늘어나게 됨.
이렇게 하면 반응형 디자인이 가능해져서, 화면 크기에 맞게 항상 중앙 정렬이 유지됨.

### ✅ 반응형 디자인

화면 크기에 따라 웹 페이지의 레이아웃과 콘텐츠가 자동으로 조정되어, 모든 디바이스에서 잘 보이도록 만드는 디자인 기법
%, vw, vh 같은 상대적인 단위를 사용함.

### ✅ grid-template-columns: repeat(4, 65px);

4개의 열을 만들고, 각 열의 너비를 65px로 설정

### ✅ grid-auto-rows: 65px;

각 행의 높이를 65px로 설정

### ✅ filter: brightness();

요소의 밝기를 조정
- 기본값: brightness(1) — 원래 밝기
- 값이 1보다 클 경우: 밝기가 더 밝아짐
- 값이 1보다 작을 경우: 밝기가 더 어두워짐
```css
element {
  filter: brightness(값);
}
```

### ✅ grid-column과 grid-row
grid-column: 가로(열) 방향에 대해 설정.
grid-row: 세로(행) 방향에 대해 설정.

span을 사용하여 몇 개의 행을 차지할지 지정할 수 있다.
```css
 grid-column: span 4; /*요소가 현재 위치에서 4개의 열을 차지하도록 설정*/
```
