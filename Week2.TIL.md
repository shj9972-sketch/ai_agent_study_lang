# TIL

## 2026-09-21

### 
생성형 ai란? 
1. 정의
학습된 분포에서 다음 토큰을 확률적으로 샘필링하는 모델 -> 예측개념
2. 핵심 단위
토큰 - 평균 한국어 1글자 = 2~3토큰
3. Context Window
한 요청에 담을 수 있는 토큰 총량(입출력)
4. 확률에 따라 랜덤으로 선택됨 -> 출력을 보장할 수 없음
5. temperature ---> 완벽하게 결정론적이 않음 : 확률 분포의 모양을 바꿈, 올라갈수록 분포가 완만해짐
6. Top K: 갯수 기반
7. Top P: 누적 상위 확률 기반
8. max_token:출력 길이 상한 - 비용 직결, 작업 별로 빡빡하게 설정을 권장
9. stop: 특정 문자열 만나면 중단, 구조화 출력에서 유용.

####
Lang-chain 이란? 
1. Messages
(1) systemmessage: 페르소나/제약설정
(2) humanmessage: 사용자 입력
(3) aimessage: 모델 응답
(4) toolmessage: 도구 실행 결과

2. LCEL - 파이프 연산자로 체인 구성
    단계          입력         출력
(1) prompt      변    채워진 프롬포트
(2) llm         프롬포트   aimessage
(3) stroutputparser aimessage  str

3. Runnavble 컴포넌트
(1) RunnablePassthrouh: 입력을 그대로 전달 (분기 합류용)
(2) RunnableLamda: 임의 함수를 runnable로 래핑
(3) RunnableParllel: 여러 체인 병렬 실행 -> dict 합치기
(4) RunnableBranch: 조건 분기 처리
(5) .with_config(...): run_name, tags, callbacks 주입

##### 
1. 프롬포트 템플릿: 동일한 프롬포트 패턴을 여러 입력에 재사용할 때 사용
2. output parser: 가장 단순한 형태의 파서. str부분만 추출
