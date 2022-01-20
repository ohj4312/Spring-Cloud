# MicroService 와 Spring Cloud
- Microservice 란?
- Microservice와 SOA
- Spring Cloud란?
- 필수 SW 설치

<br>

## Software Arcitecture
### IT System이 발전되어 온 과정
- 1960s ~ 1980s : Fragile(깨지기 쉬운 시스템), Cowboys
  - Mainframe 시대, 하드웨어(높은 비용)가 중심이 되는 시대
- 1990s ~ 2000s : Robust, Distributed
  - 분산화된 서비스로 안정적이고 높은 서비스를 제공하기 시작
- 2010s ~ : Resilient/Anti-Fragile, Cloud Native
  - 확장성, 안정성 강화, 탄력성! Devops 문화 등장
  - Anti-Fragile : 다른 개발 시스템/환경에 비해 시스템 변화가 적고 변화에 바로 적응할 수 있고 , 비용이 저렴한 특성이 있다.

<br>

### Antifragile 특징
- AutoScaling  
  - 자동 확장성을 갖는다는 특징이다. 
  - 시스템을 구성하고 있는 인스턴스를 하나의 AutoScaling 그룹으로 묶어서 그룹에서 유지되어야 하는 최소 인스턴스 지정할 수 있고 사용량에 따라 자동으로 인스턴스를 증가할 수 있는 환경.
  - 관리자나 운영자에 의해 처리되는 것이 아니라 CPU, 메모리, 네트워크, DB 사용량이나 조건에 따라 자동으로 처리할 수 있다.
- Microservices 
  - Cloud Native Architecture , Cloud Natvie Application의 핵심
  - 기존 시스템들이 하나의 거대한 형태로 구축되어 서비스되었다고 하면 Microservice는 전체 서비스를 구축하고 있는 개별 모듈이나 기능을 독립적으로 개발하고 배포하고 운영할 수 있도록 세분화된 서비스.
- Chaos engineering 
  - 시스템이 급격하고 예측하지 못한 상황에도 견딜 수 있고, 신뢰성을 갖기 위해 운영중인 소프트웨어의 시스템의 실행 방법 혹은 규칙이다.
  - 시스템의 변동, 예견된 불확실성, 예견되지 않는 불확실성, 카오스 불확실성에 대해 안정적으로 서비스를 제공할 수 있도록 구축되어야 한다는 것을 의미
- Continuous deployment
  - CI/CD와 같은 배포 파이프라인
  - CI/CD는 지속적인 통합, 지속적인 배포!
  - Cloud Native Application은 작게는 수십개, 많게는 수백개 이상의 microservice로 도메인이 분리되어 개발되는 경우가 일반적이다.
  - 수백개의 microservice를 빌드,테스트,배포 작업을 수작업으로 한다면 작업시간이 심하게 지체될 수 있다. 
  - 이를 해결하기 위해 자동화된 시스템구축이 필요하고, 하나의 작업에서 다른 작업으로 연계되는 과정을 파이프라인으로 연결시켜놓으면 작은 변화 뿐만 아니라 전체적인 시스템 업그레이드 작업에서도 빠르게 적용 가능하다.

<br>

## Cloud Native Architecture
### 확장 가능한 아키텍처
- 시스템의 수평적 확장에 유연
- 확장된 서버로 시스템의 부하 분산, 가용성 보장
  - 시스템 확장을 위한 Scaling은 Scale-up (하드웨어 사양을 높인다.) , Scale-out( 같은 사양의 서버(인스턴스)를 여러대 배치 )가 있다.
  - 일반적으로 하드웨어 비용이 증가하지만 Cloud Native Architecture에서는 cloud를 제공하는 업체로부터 가상의 서버, 가상의 스토리지, 가상의 네트워크를 빌려서 사용함으로써 비용 최소화, 반납이 가능한 구조가 되었다.
- 시스템 또는 서비스 애플리케이션 단위의 패키지 (컨테이너 기반 패키지)
- 모니터링

<br>

### 탄력적 아키텍쳐
- 서비스 생성-통합-배포, 비즈니스 환경 변화에 대응 시간 단축 
  - CI/CD 자동화 파이프라인을 통해 처리
- 분할된 서비스 구조
  - 전체 어플리케이션을 구성하는 도메인 특성에 따라 서비스 경계를 구분하고 개발해야 한다.
  - 서로 분리된 서비스 간의 원활한 통신을 위해 각각의 서비스는 종속성을 최소화 시켜야 한다.
  - 상태를 갖지 않는 서비스를 제공하도록 노력해야 한다.
  - 전체 어플리케이션을 구축하는 microservice들은 자신들이 배포될 때 자신의 위치를 등록해서 다른 서비스, 외부 시스템에서 검색해서 사용할 수 있다.
- 무상태 통신 프로토콜 
- 서비스의 추가와 삭제 자동으로 감지
- 변경된 서비스 요청에 따라 사용자 요청 처리(동적 처리)

<br>

### 장애 격리
- 특정 서비스에 오류가 발생해도 다른 서비스에 영향 주지 않음
  - 장애 복구에 뛰어나다.

<br>


## Cloud Native Applcation
- Cloud Native Architecture에 의해 설계되고 구현되는 Application
  - Cloud Native ARchitecture의 특징, Anti-Fragile 의 특징을 갖는다.

<br>

### Cloud Native Applcation 구현 형태
1. Microservice로 개발된다.
2. CI/CD 시스템에 의해 자동 통합, 빌드, 테스트, 배포 과정을 거친다.
3. DevOps, Microservice에 문제 발생시 바로 수정하여 다시 배포하는 과정을 반복하는 형태를 갖는다.
4. Containers, 하나의 어플리케이션을 구성하는 Microservice들을
 Cloud 환경에 배포하고 사용하기 위해 Container 가상화 기술을 사용한다.

<br>

### Cloud Native Applcation 특징
- CI/CD
  - 지속적인 통합(Continuous Integration)
    - 하나의 어플리케이션을 여러 팀, 여러 개발자가 개발될 때 결과물을 통합되기 위한 형상 관리를 뜻할 수도 있고, 통합된 코드를 빌드하고 테스트하는 과정 자체를 뜻하기도 한다.
    - 통합 서버, 소스 관리(SCM), 빌드 도구, 테스트 도구
    - ex) Jenkins, Team CI, Travis CI
  - 지속적인 배포
  - CD는 두가지 의미가 있다. ( 지속적인 전달, 지속적인 배포 )
    - Git과 같은 소스 저장소에 업로드된 코드를 패키지화 된 형태의 결과물을 실행환경에 어떻게 배포하는지에 따라 달라진다.
    - Continuous Delivery (CD) : 패키지화된 결과물을 실행환경에 수작업 배포하는 과정이 필요한 경우
    - Continuous Deployment (CD) : 운영자, 관리자의 개입없이 실행환경까지 자동화되어 있는 경우
    - Pipe Line 
  - 카나리 배포와 블루그린 배포 ( 배포 전략 )
    - 카나리 배포 : 전체 사용자의 95%사용자가 이전 버전의 서비스를 사용하게 하고, 5%의 사용자만이 새로운 버전의 서비스를 사용하게 한다.
    - 블루그린 배포 : 이전 버전(블루)의 사용자 트래픽과 거의 동일하게 점진적으로 새버전(그린) 서비스를 채택한다.
- Devops ( Development + Operations )
  - 개발 조직과 운영 조직의 통합을 의미하며 이를 통해 고객의 요구사항을 빠르게 반영하고 만족도 높은 서비스를 제공하고자 한다.
  - 개선사항, 오류사항 관련을 필요에 따라 바로 반영, 수정할 수 있다.
  - 고객의 요구사항에 맞는 에러 없는 프로덕트를 완성하기 위해 자주 테스트, 피드백, 업데이트 과정을 거쳐 지속적으로 개발과정이 진행된다.
  - Cloud Native Application은 Devops환경에 맞춰 서비스 단위를 작은 단위로 나눠 더 자주 통합, 테스트, 배포하는 구조가 될 수 있다.
- Container 가상화
  - Cloud Native Architecture의 핵심
  - Cloud 환경으로 이전함으로써 적은 비용으로 탄력성 있는 시스템을 구축하게 되었다.
  - 하드웨어 가상화, 서버 가상화에 비해 적은 리소스를 사용하여 가상화 서비스를 구축할 수 있다.
   <img src="./img/ContainerDeployment.png">
    - 전통적인 방식 : hw위에 운영체제, app 운영 방식
    - 하드웨어 가상화 방식 : 운영체제 위에 Hypervisor, 위에 가상머신(시스템이 가지고 있는 물리적인 하드웨어 - post system을 쪼개서 사용하는 개념) 가동해서 독립적인 운영체제를 가지고 실행될 수 있다. 즉, 각각의 가상머신에 application을 운영할 수 있다. 단, post 운영체제에 많은 부하를 주고, 확장에 한계가 있다.
    - Container 가상화 : 운영체제 위에 Container 가상화를 기동하기 위한 소프트웨어 서비스를 작동하고 컨테이너 가상화에서는 공통적인 라이브러리, 리소스를 공유해서 사용한다. 각자 필요한 부분에 대해서만 독립적인 영역에서 실행할 수 있는 구조이다. 더 적은 리소스를 사용하고, 서비스들은 가볍고 빠르게 운영할 수 있다는 특징을 가지고 있다.



<br>

## 12 Factors
Cloud Native Application을 구축함에 있어서 고려해야 할 12가지 항목

1. 코드 베이스 – Base Code
   - 자체 Repostory에 저장된 각 Microservice에 대한 단일 코드베이스를 뜻함. 
   - 버전 제어, 형상 관리가 주 목적이다.
   - 이후 배포하기 위해 코드의 통일된 관리가 중요하다.
2. 종속성(의존성) 배제 – Dependency Isolation
   - 각 Microservice는 자체 종속성을 가지고 패키지되어 있기 때문에 전체 시스템에 영향을 주지 않는 상태로 변경되고 수정될 수 있어야 한다.
3. 환경 설정의 외부관리 - Configurations
   - 구성 정보, 코드 외부에서 구성 관리 도구를 통해 Microservice에 필요한 작업을 제어하는 것이다.
   - 동일한 배포가 올바른 구성이 적용된 환경에서 전파될 수 있다.
4. 서비스 지원 – Linkable Backing Services
   - 보조 서비스 (DB,Cahce,Broker 등)를 이용하여 Microservice가 가져야 할 기능을 추가로 지원한다.
   - 프로그램에서 필요한 Backing System Resource를 분리함으로써 서로 코드 Dependecy를 갖지 않게 된다. 
5. 빌드,릴리즈, 실행 환경 분리 – Stages of Creation
   - 필요한 상태에 대해 개발 서버에서 만들어진 코드를 배포하기 위해 실행 단계까지 옮기는 과정을 엄격하게 분리해야 한다.
   - 고유한 ID로 태그를 가져야 하며, rollback 기능을 지원해야 하며, CI/CD 시스템을 이용한 자동화된 서비스를 구축해야 한다.
6. 상태관리 프로세스 (stateless 프로세스) – Stateless Processes
   - 각각의 Microservice는 실행중인 다른 service와 분리되어 자체 process에서 운영될 수 있어야 한다. (독립성)
   - 하나의 Microservice는 다른 Microservice와 분리되어 독립적으로 실행될 수 있는 상태여야 한다.
   - 필요한 자원이 있다면 Cache, Data Store를 통해 외부와 데이터 동기화를 한다. 
7. 포트 바인딩 – Port Binding
   - 각각의 Microservice는 자체 포트에서 노출되는 인터페이스 및 기능과 함께 자체 포함되어 있는 기능이 있어야 한다.
   - 다른 Microservice와의 격리를 위함이다.
8. 동시성 - Concurrency
   - Microservice는 아주 많은 수의 service를 동일한 process를 복사해서 확장해나간다.
   - 하나의 service가 여러개의 인스턴스에 동일한 형태로 복사되어 운영됨으로써 부하분산을 이루어낸다. (동시성을 갖는다.)
9. 폐기 가능 – Disposability
   - service 인스턴스 자체가 삭제가 가능해야 한다.
   - 확장성 기회를 높여야 한다.
   - 정상 종료를 할 수 있는 상태여야 한다.
10. Development 단계와 Production 단계 구분 – Development & Production Parity
    - 응용 프로그램의 수명주기 전반에 걸쳐 최대한 많은 서비스 access를 방지해서 다른 작업과 종속적이지 않은 상태를 유지해야 한다.
11. 로깅 - Logs
    - Microservice에 의해서 생성된 로그를 이벤트 스트림으로 처리해야 한다.
    - 하나의 시스템 안에서 구성되고 있는 로그를 출력하는 로직은 기존의 어플리케이션 로직과 분리되어 어플리케이션이 실행되지 않는 상태더라도 로그는 정상적으로 작동하는 상태여야 한다.
    - 이를 위해 별도의 서비스, 모니터링 도구를 사용할 수 있다.
12. Admin 프로세스 – Admin Processes For Eventual Processes
    - 현재 운영되고 있는 모든 Microservice들을 어떤 상태로 사용되며, 리소스가 사용되는 것을 파악하기 위한 적절한 관리도구가 필요하다.
    - 리포팅 기술이 포함되어야 하며, 데이터 정리 및 데이터 분석 기술이 포함될 수 있따. 

### Pivotal의 + 3 Factors

2. API first
   - 모든 Microservice는 API 형태로 서비스가 제공되어야 한다.
   - API 구축시 사용자가 어떤 형태로 사용하는지 먼저 고려해야 한다.
14. Telemetry
    - 모든 지표는 수치화, 시각화되서 관리되어야 한다. 
15. Authentication and authorization
    - API를 사용함에 있어서 인증이 필수여야 한다.
    - Microservice가 분리되어 있는 상태로 개발된다고 하더라도 구현하는 Microservice는 적절한 인증을 가지고 있는 리소스, 서비스,외부시스템에서 데이터를 전달, 교환이 가능해야 한다.

<br>

## Monolithic vs Microservice

<br>

## Microservice Architecture 란?

<br>

## SOA vs MSA

<br>

## Microservice Architecture Structures

<br>

## Spring Cloud란?


