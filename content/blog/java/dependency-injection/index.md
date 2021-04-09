---
title: 의존 객체 주입(Dependency Injection)
date: "2021-02-17T23:17:00.000Z"
---

# DI(Dependency Injection)
dependecy가 있는 resource를 외부에서 주입받는 기법으로 유연성과 테스트 용이성을 높여준다. 
## * 장점
자원을 직접 명시하기 보단 의존 객체 주입 사용하자. 또, 사용하는 resource에 따라 동작이 달라지는 클래스에는 정적 유틸리티 클래스나 싱글턴 방식 적합하지 않다.
불변을 보장하고 같은 resource를 사용하는 여러 client가 의존 객체들을 안심하고 공유 할 수 있기도 하다.
## * 단점
denpendency가 매우 많은 큰 프로젝트에서 코드를 어지럽게 만드기도 한다. Dagger, Guice, Spring 등의 의존 객체 주입 프레임워크를 사용하면 어질러짐을 해소 할 수 있다.

<br><br>
# 팩토리 메소드 패턴(Factory Method Pattern)
DI의 변형으로 팩토리를 생성자에 넘겨주는 방식이다. 여기서 팩토리란 호출 시, 특정 타입의 인스턴스를 반복해서 만들어주는 객체다.
## * Supplier\<T> 인터페이스
자바 8에서 소개된 인터페이스로 팩토리를 완벽하게 표현한 예이다.  
Supplier\<T>를 파라미터로 받는 메소드는 일반적으로 bounded wildcard type을 사용해 팩토리의 타입 매개변수 제한해야 한다. 자신이 명시한 타입의 하위 타입은 생성할 수 있는 팩토리를 넘길 수 있다.

```java
Mosaic create(Supplier<? extends Tile> tileFactory){
    ...
}
```
 ex) client가 제공한 팩토리가 생성한 Tile들로 구성된 Mosaic를 만드는 메소드
 


<br><br>
# reference
* Joshua Bloch, 『Effective Java 3rd Edition』, 인사이트(2020), p28-30



