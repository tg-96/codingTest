### 문제
> x축과 y축으로 이루어진 2차원 직교 좌표계에 중심이 원점인 서로 다른 크기의 원이 두 개 주어집니다. 반지름을 나타내는 두 정수 r1, r2가 매개변수로 주어질 때, 두 원 사이의 공간에 x좌표와 y좌표가 모두 정수인 점의 개수를 return하도록 solution 함수를 완성해주세요.
> ※ 각 원 위의 점도 포함하여 셉니다.

```java
import java.util.*;

class Solution {
    public long solution(int r1, int r2) {
        double r2_y;
        double floor;
        double r1_y;
        double ceil;
        long answer = 0;
        
        for(int x = 0; x < r2; x++ ){
            if(x == 0){
                answer += r2-r1+1;
            }
            else if(x >= r1){
                r2_y = Math.sqrt(Math.pow(r2,2)-Math.pow(x,2));
                floor = Math.floor(r2_y);
                answer += floor;
            }
            else if(x < r1 ){
                r2_y = Math.sqrt(Math.pow(r2,2)-Math.pow(x,2));
                floor = Math.floor(r2_y);
                
                r1_y = Math.sqrt(Math.pow(r1,2)-Math.pow(x,2));
                ceil = Math.ceil(r1_y);
                
                answer += floor-ceil+1;
            }
        }
        return answer*4;
    }
}
```

## 주의할점
처음에 계속 test 7,8,9,10 에서 안됐다. 아마도 testcase의 r1,r2가 값이 클때 인것 같았다.
코드가 아무리 봐도 틀려보이는게 없었다. 혹시나 해서 x*x를 Math.pow(x,2)로 고쳤는데 됐다.
값이 클때는 x\*x보다는 Math.pow(x,2)를 사용해야 한다.
