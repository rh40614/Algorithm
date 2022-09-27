# [프로그래머스][고득점 kit] K번째 수

## 2022.09.14

### **1. 문제**

![https://postfiles.pstatic.net/MjAyMjA5MTRfMTEx/MDAxNjYzMTU2NTIyMTM1.Y0ZUKjQDMBZtwK793WzElSnCvvRQSNiHpGR2rLET92Ug.jS_A6eT_iVChl1Q5_fDK-fABdSwXTabjCdPSUngKvJ8g.PNG.dushui/image.png?type=w773](https://postfiles.pstatic.net/MjAyMjA5MTRfMTEx/MDAxNjYzMTU2NTIyMTM1.Y0ZUKjQDMBZtwK793WzElSnCvvRQSNiHpGR2rLET92Ug.jS_A6eT_iVChl1Q5_fDK-fABdSwXTabjCdPSUngKvJ8g.PNG.dushui/image.png?type=w773)

![https://postfiles.pstatic.net/MjAyMjA5MTRfMTQ1/MDAxNjYzMTU2NTQ2NDAz.tOd1pURBaRZmBKUdt260Upn9s82z3TVPmeWr3Q4ombYg.I76JSW1jg5GkNrdXuhkZQhLI46RqR-63Yyqxg3ESSiMg.PNG.dushui/image.png?type=w773](https://postfiles.pstatic.net/MjAyMjA5MTRfMTQ1/MDAxNjYzMTU2NTQ2NDAz.tOd1pURBaRZmBKUdt260Upn9s82z3TVPmeWr3Q4ombYg.I76JSW1jg5GkNrdXuhkZQhLI46RqR-63Yyqxg3ESSiMg.PNG.dushui/image.png?type=w773)

### 2. 오답

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        int i = 0;
        int j = 0;
        int k = 0;
      
        for(int a = 0; a < commands.length; a++){
            i = commands[a][0];
            j = commands[a][1];
            k = commands[a][2];
            
            Arrays.sort(array,i-1,j);
            answer[a] = array[i+k-2];  
        }
        return answer;
    }
}
```

array를 sort를 실행하니 array 자체의 구조를 변경해버려서 처음에는 제대로 작동하지만 뒤에는 제대로 작동하지 않았다.  array를 복사해서 원본을 유지하고 실행해서 성공

### 3. 통과

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        int i = 0;
        int j = 0;
        int k = 0;
      
        for(int a = 0; a < commands.length; a++){
            
            i = commands[a][0];
            j = commands[a][1];
            k = commands[a][2];
         
            int[] arr = array.clone();
            Arrays.sort(arr,i-1,j);
            answer[a] = arr[i+k-2];  
        }
       
        
        return answer;
    }
}
```

간단하게 썻지만 array 초기화가 안되서 1시간 넘게 고민했다. ㅜㅜ

### 4. 알게된점

2차 배열에 대해서 잘 몰랐는데 알 수 있었다.

2차원 배열에 접근하는 방식도 알게 되었다.