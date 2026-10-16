# 볼링 게임 카타

## 출처

Uncle Bob(로버트 C. 마틴)의 [The Bowling Game Kata](http://www.butunclebob.com/ArticleS.UncleBob.TheBowlingGameKata)에서 영감을 받았습니다.

## 볼링 규칙

게임은 10프레임으로 이루어집니다. 각 프레임에서 플레이어는 두 번 공을 굴려 핀 10개를 쓰러뜨립니다. 프레임 점수는 쓰러뜨린 핀의 총합에 스트라이크와 스페어 보너스를 더한 값입니다.

스페어는 두 번의 투구로 핀 10개를 모두 쓰러뜨린 경우입니다. 그 프레임의 보너스는 다음 투구 한 번에서 쓰러뜨린 핀 수입니다.

스트라이크는 첫 투구에 핀 10개를 모두 쓰러뜨린 경우입니다. 이때 프레임은 투구 한 번으로 끝납니다. 그 프레임의 보너스는 다음 두 번의 투구 값입니다.

10번째 프레임에서 스페어나 스트라이크를 친 플레이어는 프레임을 마무리하기 위해 추가 투구를 할 수 있습니다. 단, 10번째 프레임에서는 최대 세 번까지만 굴릴 수 있습니다.

## 요구사항

메서드 두 개를 가진 `Game` 클래스를 작성하세요.

1. `void roll(int)` — 플레이어가 공을 굴릴 때마다 호출됩니다. 인자는 쓰러뜨린 핀의 개수입니다.
2. `int score()` — 해당 게임의 총점을 반환합니다.

## 시작점

Java 17 + JUnit 5 + Gradle 기준 프로젝트 뼈대입니다. 아래 세 파일을 만들고 `./gradlew test`(또는 `gradle test`)를 실행하면 첫 테스트가 실패(Red)하는 상태에서 시작합니다.

```
bowling-kata/
├── build.gradle
└── src/
    ├── main/java/bowling/Game.java
    └── test/java/bowling/GameTest.java
```

`build.gradle`

```groovy
plugins {
    id 'java'
}

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(17)
    }
}

repositories {
    mavenCentral()
}

dependencies {
    testImplementation platform('org.junit:junit-bom:5.10.2')
    testImplementation 'org.junit.jupiter:junit-jupiter'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
}

test {
    useJUnitPlatform()
    testLogging {
        events 'passed', 'failed'
    }
}
```

`src/main/java/bowling/Game.java`

```java
package bowling;

public class Game {

    public void roll(int pins) {
        // TODO: 테스트가 요구할 때 구현하세요
    }

    public int score() {
        // TODO: 테스트가 요구할 때 구현하세요
        return -1;
    }
}
```

`src/test/java/bowling/GameTest.java`

```java
package bowling;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.assertEquals;

class GameTest {

    private Game game;

    @BeforeEach
    void setUp() {
        game = new Game();
    }

    @Test
    @DisplayName("거터 게임이면 0점이다")
    void gutterGame() {
        for (int i = 0; i < 20; i++) {
            game.roll(0);
        }
        assertEquals(0, game.score());
    }

    // 다음 테스트를 하나씩 추가하며 Red → Green → Refactor 를 반복하세요.
}
```
