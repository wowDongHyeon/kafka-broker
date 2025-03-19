# Docker를 사용한 Kafka 브로커

이 프로젝트는 Docker와 Docker Compose를 사용하여 Kafka 브로커를 설정합니다. Zookeeper와 Kafka 서비스를 포함하고 있습니다.

## 사전 준비

- Docker Desktop이 설치되어 있어야 합니다.
- Docker Compose는 Docker Desktop에 포함되어 있습니다.

## 시작하기

### 저장소 클론

```bash
git clone <repository-url>
cd <repository-directory>
```

### 서비스 실행

1. **서비스 시작**

   Docker Compose를 사용하여 Zookeeper와 Kafka 서비스를 시작합니다.

   ```bash
   docker-compose up -d
   ```

   이 명령어는 서비스를 백그라운드 모드로 시작합니다.

2. **서비스 접근**

   - **Zookeeper**: 포트 `2181`에서 사용 가능.
   - **Kafka**: 포트 `9092`에서 사용 가능.

### 서비스 중지

서비스를 중지하려면 다음 명령어를 실행하세요:

```bash
docker-compose down
```

### 추가 설정

- `docker-compose.yml` 파일에는 Spring Boot 애플리케이션에 대한 주석 처리된 섹션이 포함되어 있습니다. 이 섹션을 포함하려면 주석을 해제하고 구성할 수 있습니다.

### 환경 변수

- **Zookeeper**: `ALLOW_ANONYMOUS_LOGIN=yes`
- **Kafka**:
  - `KAFKA_BROKER_ID=1`
  - `KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper:2181`
  - `ALLOW_PLAINTEXT_LISTENER=yes`
  - `KAFKA_CFG_LISTENERS=PLAINTEXT://0.0.0.0:9092`
  - `KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092`

## 참고 사항

- 포트 `2181`과 `9092`가 다른 애플리케이션에 의해 사용 중이지 않은지 확인하세요.
- Spring Boot 애플리케이션 섹션은 현재 주석 처리되어 있습니다. 필요에 따라 주석을 해제하고 구성하세요.

## 라이선스

이 프로젝트는 MIT 라이선스에 따라 라이선스가 부여됩니다. 자세한 내용은 LICENSE 파일을 참조하세요. 