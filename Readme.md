## FLEX & Grid Class

### 2020.03.03 

참고 페이지 : https://studiomeal.com/archives/197

![image](https://user-images.githubusercontent.com/43080040/76209471-4a7a0e80-6245-11ea-9644-53054319a5ff.png)

2020.03.09 시작~

GRID는 특히 Firefox에서 할 것!

---

## FLEX 정리

### 1. 배치의 흐름

Flex 레이아웃을 만들기 위한 기본적인 HTML구조는 parent > child 구조이어야 한다.

```html
<div class="container">
	<div class="item">helloflex</div>
	<div class="item">abc</div>
	<div class="item">helloflex</div>
</div>
```

```css
.container{
	display:flex;
}
```

![image](https://user-images.githubusercontent.com/43080040/77759720-8d771700-7078-11ea-945c-9b765eabdb51.png)



- 배치 방향 설정

`flex-direction` : 배치되는 축을 설정한다.

```css
.container {
	flex-direction: row;
	/* flex-direction: column; */
	/* flex-direction: row-reverse; */
	/* flex-direction: column-reverse; */
}
```

![image](https://user-images.githubusercontent.com/43080040/77760019-0ecea980-7079-11ea-9278-c9d6fb32d9d3.png)



- 줄 넘김 처리

`flex-wrap` : 기본값인 nowrap은 삐져나가게 된다.

```css
.container {
	flex-wrap: nowrap;
	/* flex-wrap: wrap; */
	/* flex-wrap: wrap-reverse; */
}
```

![image](https://user-images.githubusercontent.com/43080040/77760132-3faede80-7079-11ea-8af9-c497ccf10f47.png)



- `flex-direction` + `flex-wrap`

`flex-flow` : flex-direction과 flex-wrap을 한번에 쓸 수 있는 속성이다.

```css
.container {
	flex-flow: row wrap;
	/* 아래의 두 줄을 줄여 쓴 것 */
	/* flex-direction: row; */
	/* flex-wrap: wrap; */
}
```

---

### 2. 전체 아이템 정렬

- `justify` : 메인축 방향
- `align` : 수직축 방향

- 메인축 방향 정렬

`justify-content` : 메인축 방향으로 아이템들을 정렬

```css
.container {
	justify-content: flex-start;
	/* justify-content: flex-end; */
	/* justify-content: center; */ /* 가운데 정렬 */
	/* justify-content: space-between; */
	/* justify-content: space-around; */
	/* justify-content: space-evenly; */
}
```

 ![image](https://user-images.githubusercontent.com/43080040/77760916-7df8cd80-707a-11ea-972b-5b7e09b94ae5.png)



- 수직축 방향 정렬

`align-items` : 수직축 방향으로 아이템을 정렬한다.

```css
.container {
	align-items: stretch;
	/* align-items: flex-start; */
	/* align-items: flex-end; */
	/* align-items: center; */
	/* align-items: baseline; */
}
```



- 가운데 정렬

```css
justify-content: center;
align-item: center;
```

![image](https://user-images.githubusercontent.com/43080040/77761207-07100480-707b-11ea-9350-baa55b2a98f7.png)



- 여러행 정렬

`align-content` : flex-wrap: wrap;이 설정된 상태에서, 아이템들의 행이 2줄 이상 되었을 때의 수직축 방향 정렬을 결정하는 속성이다.

```css
.container {
	flex-wrap: wrap;
	align-content: stretch;
	/* align-content: flex-start; */
	/* align-content: flex-end; */
	/* align-content: center; */
	/* align-content: space-between; */
	/* align-content: space-around; */
	/* align-content: space-evenly; */
}
```

---

### 3. 유연한 박스 (item에 적용)

- 유연한 박스의 기본 영역

`flex-basis` : flex 아이템의 기본 크기를 설정한다. (flex-direction : row 일때는 가로크기, column일때는 세로크기)

```css
.item {
	flex-basis: auto; /* 기본값 */
	/* flex-basis: 0; */
	/* flex-basis: 50%; */
	/* flex-basis: 300px; */
	/* flex-basis: 10rem; */
	/* flex-basis: content; */
}
```

![image](https://user-images.githubusercontent.com/43080040/77762603-1ee88800-707d-11ea-82d3-8c137455608f.png)



- 유연하게 늘리기

`flex-grow` : `flex-basis` 의 값보다 커질 수 있는지를 결정하는 속성

```css
.item {
	flex-grow: 1;
	/* flex-grow: 0; */ /* 기본값 */
}
```

![image](https://user-images.githubusercontent.com/43080040/77762810-6bcc5e80-707d-11ea-951a-7bc849f8f6d9.png)

![image](https://user-images.githubusercontent.com/43080040/77762786-62db8d00-707d-11ea-8364-0471131f98c4.png)

![image](https://user-images.githubusercontent.com/43080040/77762865-81da1f00-707d-11ea-9edf-b3abcfc9056f.png)



- 유연하게 줄이기

`flex-shrink` : `flex-grow` 와 쌍을 이루는 속성이며, 아이템이 flex-basis의 값보다 작아질 수 있는지를 결정한다.

```css
.item {
	flex-basis: 150px;
	flex-shrink: 1; /* 기본값 */
}
```



- `flex-basis` + `flex-shrink` + `flex-basis`

`flex` : 축약형이다.

```css
.item {
	flex: 1;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: 0%; */
	flex: 1 1 auto;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: auto; */
	flex: 1 500px;
	/* flex-grow: 1; flex-shrink: 1; flex-basis: 500px; */
}
```

---

## GRID

기본 HTML 구조

```html
<div class="container">
	<div class="item">A</div>
	<div class="item">B</div>
	<div class="item">C</div>
	<div class="item">D</div>
	<div class="item">E</div>
	<div class="item">F</div>
	<div class="item">G</div>
	<div class="item">H</div>
	<div class="item">I</div>
</div>
```

