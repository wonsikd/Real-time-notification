# Real-time-notification

### 본 프로젝트는 보유 종목에 대한 실시간 공시 및 뉴스를 가져올 수 있게한 프로그램입니다.
### 파일은 '국내펀드보유내역.xlsx'와 같은 양식을 지닌 파일이 있으면 작동이 가능합니다.
### 회사에서 사용한 프로그램이므로 회사 엑셀파일의 양식에 맞추느라 직접 사용하실 경우 약간의 수정이 필요합니다.(해당 양식은 capital IQ 양식입니다.)
### 실제 사용하실 경우, get_corp_list(self) 함수에서 data1,data2,data3 를 수정하셔야합니다.
### 회사의 니즈를 맞춰 양식 및 필요한 공시를 가져오기 위해 조건이 다소 일반적이지 않음은 양해부탁드립니다.
### 프로그램 실행시, dart api키는 필수로 필요하므로 api 키를 받아와주시면 되겠습니다.
### 전체적인 알고리즘은 다음과 같습니다.

1. class 실행
2. 보유종목 엑셀파일을 열어 종목 저장 및 종목에 따른 업종 딕셔너리 생성
3. 보유종목에 따라 하나씩 dart에서 공시를 가져옵니다.
4. 이후 공시를 전부 가져오면, 네이버 실시간 뉴스를 가져옵니다.(중복뉴스 및 유사 뉴스는 임베딩을 통해 유사도를 측정 후 제거해주었습니다.)
5. 3-4과정을 프로그램이 꺼지지 않는 한 계속 반복합니다. 과부하를 막기위해 sleep을 걸어줘 240초 마다 서칭을 하게끔 해주었습니다.
