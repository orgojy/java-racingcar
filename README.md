# 자동차 경주 게임

## 기능 요구사항

* 초간단 자동차 경주 게임을 구현한다.
* 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
* 사용자는 입력받은 자동차로 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
* 전진하는 조건은 0에서 9 사이에서 random 값을 구한 후 random 값이 4이상일 경우이다.
* 자동차의 상태를 화면에 출력한다. 어느 시점에 출력할 것인지에 대한 제약은 없다.
* 각 자동차에 이름을 부여할 수 있다. 자동차 이름은 5자를 초과할 수 없다.
* 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
* 자동차 이름은 쉼표(,)를 기준으로 구분한다.
* 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한명 이상일 수 있다.

## 프로그래밍 요구사항

* 모든 로직에 단위 테스트를 구현한다. 단, UI(System.out, System.in) 로직은 제외
    * 핵심 로직을 구현하는 코드와 UI를 담당하는 로직을 구분한다.
    * UI 로직을 InputView, ResultView와 같은 클래스를 추가해 분리한다.
* 자바 코드 컨벤션을 지키면서 프로그래밍한다.
    * 참고문서: https://google.github.io/styleguide/javaguide.html 또는 https://myeonguni.tistory.com/1596
* else 예약어를 쓰지 않는다.
    * 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
    * else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.
* indent(인덴트, 들여쓰기) depth를 2를 넘지 않도록 구현한다. 1까지만 허용한다.
    * 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    * 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메소드)를 분리하면 된다.
* 함수(또는 메소드)의 길이가 15라인을 넘어가지 않도록 구현한다.
    * 함수(또는 메소드)가 한 가지 일만 잘 하도록 구현한다.

## 기능 구현 목록

- 자동차의 위치 정보인 `CarName` 구현
    - [ ] `CarName`는 1글자 이상, 5글자 이하 문자열을 가진다.
- 자동차의 위치 정보인 `CarNames` 구현
    - [ ] `CarNames`는 1개 이상 `CarName`으로 생성한다.
- 자동차의 위치 정보인 `CarPosition` 구현
    - [ ] `CarPosition`는 0또는 양의 정수를 가진다.
- 자동차 경주를 구성하는 기본 단위인 `Car` 구현
    - [ ] `Car`는 이름 정보인 `CarName`를 가진다.
    - [ ] `Car`는 위치 정보인 `CarPosition`를 가진다.
    - [ ] `Car`는 생성시 초기값으로 `CarPosition`의 숫자 0을 가진다.
    - [ ] `Car`는 `RandomIntMovementPolicy`의 정책에 맞으면 이동이 가능하다.
    - [ ] `Car`이 우승했는지 확인이 가능하다.
- 자동차 경주를 같이하는 자동차 그룹 `Cars` 구현
    - [ ] `Cars`를 초기화하기 위한 이름 `CarNames`를 전달 받아 `Cars`의 `Car`를 초기화한다.
    - [ ] 전달 받은 `CarNames`는 비어있지 않아야한다.
    - [ ] `Cars`를 움직일 수 있다.
    - [ ] `Cars`를 움직이기 위해서는 자동차 경주에 사용하는 `RandomIntMovementPolicy`를 적용한다.
    - [ ] 경주에서 우승한 `Car` 또는 `Car`들을 검색이 가능하다.
- 자동차 경주에 필요한 랜덤 생성 유틸 `RandomGenerator` 구현
    - [ ] 0에서 9사이에 랜덤 정수를 반환한다.
- 자동차 경주의 조건을 정의하는 `RandomIntMovementPolicy` 구현
    - [ ] 0에서 9까지 값 중 4이상의 값을 가지면 전진이 가능하다.
    - [ ] 전략의 변경을 고려해서 `MovementPolicy` 인터페이스로 다형성을 활용한다.
- 자동차 경주를 시작할 정보를 입력받을 콘솔 `InputConsole` 구현
    - [ ] 자동차 경주에 참여할 `Cars`의 이름 `CarNames`을 입력받는다.
    - [ ] 자동차 경주에서 움직임을 시도할 횟수를 입력받는다.
- 자동차 경주 현황을 화면에 출력하는 콘솔 `OutputConsole` 구현
    - [ ] 각 회차 `Cars`의 각 `Car`의 `CarName`과 `CarPosition` 현황을 출력한다.
- 자동차 경주 게임을 구성하는 `CarRacingGame` 구현
    - [ ] `InputConsole`와 `OutputConsole`를 활용하여 콘솔을 구성한다.
    - [ ] `Cars`를 초기화하여 자동차 경주 게임을 시작한다.

## 게임 실행 예시

> 경주할 자동차 이름을 입력하세요(이름은 쉼표(,)를 기준으로 구분).    
> pobi,crong,honux  
> 시도할 회수는 몇회 인가요?  
> 5
>
> 실행결과  
> pobi : &#45;    
> crong : &#45;  
> honux : &#45;
>
> pobi : &#45;&#45;  
> crong : &#45;  
> honux : &#45;&#45;
>
> pobi : &#45;&#45;&#45;    
> crong : &#45;&#45;  
> honux : &#45;&#45;&#45;
>
> pobi : &#45;&#45;&#45;&#45;  
> crong : &#45;&#45;&#45;  
> honux : &#45;&#45;&#45;&#45;
>
> pobi : &#45;&#45;&#45;&#45;&#45;  
> crong : &#45;&#45;&#45;  
> honux : &#45;&#45;&#45;&#45;&#45;
>
> pobi, honux가 최종 우승했습니다.
>> > > > > > Stashed changes

* * *

# 문자열 계산기

## 기능 요구사항

* 사용자가 입력한 문자열 값에 따라 사칙연산을 수행할 수 있는 계산기를 구현해야 한다.
* 입력 문자열의 숫자와 사칙 연산 사이에는 반드시 빈 공백 문자열이 있다고 가정한다.
* 나눗셈의 경우 결과 값을 정수로 떨어지는 값으로 한정한다.
* 문자열 계산기는 사칙연산의 계산 우선순위가 아닌 입력 값에 따라 계산 순서가 결정된다. 즉, 수학에서는 곱셈, 나눗셈이 덧셈, 뺄셈 보다 먼저 계산해야 하지만 이를 무시한다.
* 예를 들어 2 + 3 * 4 / 2와 같은 문자열을 입력할 경우 2 + 3 * 4 / 2 실행 결과인 10을 출력해야 한다.

## 프로그래밍 요구사항

* 메소드가 너무 많은 일을 하지 않도록 분리하기 위해 노력해 본다.

## 기능 구현 목록

- 연산에 필요한 피연산자 `ArithmeticOperand` 정의
    - [ ] 정수로 구성된 피연산자 생성
- 덧셈, 뺄셈, 곱셈, 나눗셈 계산에 필요한 연산자 `ArithmeticOperator` 정의
    - [ ] 덧셈, 뺄셈, 곱셈, 나눗셈으로 구성된 Enum 생성
    - [ ] 덧셈, 뺄셈, 곱셈, 나눗셈이 아닌 연산자는 IllegalArgumentException 발생
- 1회 연산에 필요한 수식 `ArithmeticExpression` 정의
    - [ ] 1개 연산자 `ArithmeticOperator`와 2개 피연산자 `ArithmeticOperand`로 구성된 수식 생성
- 1회 연산 결과를 저장할 값 `ArithmeticResult` 정의
    - [ ] 정수로 구성된 결과값 생성
- 연산에 필요한 전체 수식에 대한 객체 `InputExpression` 정의
    - [ ] null이거나 빈 공백 문자일 경우 IllegalArgumentException 발생
- 계산에 필요한 전체 수식을 입력받기 위한 콘솔 `InputConsole` 구현
    - [ ] 계산에 필요한 수식을 사용자에게 입력받는 기능
- 입력받은 수식에 대한 결과를 출력하는 콘솔 `OutputConsole` 구현
    - [ ] 입력받은 계산의 결과를 출력하는 기능
- 계산에 필요한 전위/중위/후위 표기법 변환 유틸 `NotationUtils` 구현
    - [ ] 중위 표기법을 후위 표기법으로 변경
    - [ ] 전위/중위/후위 표기법을 Stack으로 변경
- 문자열 수식을 계산하는 문자열 계산기 `StringCalculator` 구현
    - [ ] 중위 표기법 수식 계산
    - [ ] 좌에서 우로 순서대로 진행하며 계산

## 게임 실행 예시

> 수식을 입력해주세요:  
> 2 + 3 * 4 / 2  
> = 10  
> 1 + 3 * 4 / 2  
> = 8  
> ...
