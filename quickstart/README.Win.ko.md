# Windows 환경에서 QuickStart 실행하기
Pinpoint는 공식적으로는 Linux와 OS X를 지원한다. 하지만 Pinpoint와 HBase 모두 Java 기술을 사용하고 있기 때문에 QuickStart를 Windows에서도 실행할 수 있다. 여기에서는 Windows 환경에서 Cygwin을 사용하지 않고 HBase와 Pinpoint를 실행하는 것에 대해 설명한다.

## 시작하기

```git clone https://github.com/naver/pinpoint.git```로 Pinpoint를 다운로드 하거나 zip 파일로 프로젝트를 [다운로드](https://github.com/naver/pinpoint/archive/master.zip)하고 압축을 해제한다.

```cd pinpoint```를 하고  ```mvn install -Dmaven.test.skip=true```를 실행하여 maven으로 Pinpoint를 설치한다.

### 설치 및 HBase 시작하기
**[Apache 다운로드 사이트](http://apache.mirror.cdnetworks.com/hbase/)에서 HBase 0.94.x 버전을 다운로드 받는다.

**다운로드 받은 파일을 quickstart\hbase 디렉토리에 압축을 풀고 디렉토리 이름을 hbase로 변경하여 ```quickstart\hbase\hbase``` 로 만든다.

**준비 - ```quickstart\bin\prepare-hbase-win.cmd```를 실행하여 quickstart\support\hbase-win에 있는 Windows용 HBase 명령어(.cmd) 파일들을 quickstart\hbase 디렉토리에 복사한다. 해당 HBase 명령어는 HBase 0.98.x 버전에 포함되어 있는 것들이다.

**HBase 시작 - ```quickstart\bin\start-hbase.cmd``` 실행

**테이블 초기화** - ```quickstart\bin\init-hbase.cmd``` 실행

### Pinpoint 데몬 시작하기

**Collector** - ```quickstart\bin\start-collector.cmd``` 실행

**Web UI** - ```quickstart\bin\start-web.cmd``` 실행

**TestApp** - ```quickstart\bin\start-testapp.cmd``` 실행

### 상태 확인
HBase와 3개 데몬이 실행한 후 Pinpoint 인스턴스를 테스트하려면 아래 주소로 접속한다.

* Web UI - http://localhost:28080
* TestApp - http://localhost:28081

TestApp UI를 사용하여 Pinpoint로 추적 데이터를 전송하고, Pinpoint Web UI를 통해 해당 데이터들을 확인할 수 있다. TestApp은 *TESTAPP*에 *test-agent*로 등록된다.

## 종료하기

**HBase** - ```quickstart\bin\stop-hbase.cmd``` 실행

**Collector** - ```quickstart\bin\stop-collector.cmd``` 실행

**Web UI** - ```quickstart\bin\stop-web.cmd``` 실행

**TestApp** - ```quickstart\bin\stop-testapp.cmd``` 실행