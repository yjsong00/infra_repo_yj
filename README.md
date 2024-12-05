# infra_repo_yj

# 프로젝트명: Kubernetes 기반 API 서버 배포

## 2. 인프라 구성

## 2.1 API 서버 배포
- API 서버는 NodePort 타입의 서비스로 외부에서 접근. 기본 포트는 8000이며, 노드 포트는 32639

## 2.2. 인프라 구성도
![에스티씨랩구성도 (1)](https://github.com/user-attachments/assets/b5ce48e9-0faa-44f8-867a-a3543c41c257)


## 3. 구축 완료 보고
- **문제발생** : 미니큐브의 ip 노드포트로의 접근이 안됨
- 포트 포워딩을 통한 api-server의 **로컬 접속, db 연동**도 잘 됨.
  
  : apiserver와 db는 문제 없음
  <img width="514" alt="스크린샷 2024-12-06 오전 2 56 40" src="https://github.com/user-attachments/assets/9650e785-42f6-46e9-b51e-943579f34172">

  <img width="647" alt="스크린샷 2024-12-05 오전 8 20 28" src="https://github.com/user-attachments/assets/e246bac1-9247-4f5a-b366-774131337d0f">

- 문제 해결을 위해 강제로 접근이 가능한 url을 얻기로 함, 다음 커멘드를 사용
  
  : Docker 엔진을 통해서 minikube 클러스터를 구축하게 되면 external IP를 할당받지 못해서 외부 접근이 안되는 문제가 지속적으로 발생한다고 함
  ```bash
  minikube service my-svc --url
  ```
  
  <img width="592" alt="스크린샷 2024-12-06 오전 2 52 30" src="https://github.com/user-attachments/assets/70809806-329c-45d9-9674-6b04a8522c3b">

