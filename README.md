# Sharjeel Ansari — ML Platform & MLOps Engineer
 
> Building production-grade ML infrastructure at the intersection of DevOps, distributed systems, and machine learning.
 
---
 
## 🔭 What I'm Building Now
 
**[Aegis AI](https://github.com/sharjeel6392/aegis-ai)** — *open source, in progress (Week 1 of a 16-week build)*

AI-powered incident investigation and root cause analysis for Kubernetes and cloud-native infrastructure. On-call engineers spend the first 20–40 minutes of an incident correlating alerts, logs and metrics by hand before diagnosis even starts. Aegis does that part.

- Ingests **Prometheus Alertmanager** and **Grafana** webhooks, normalising every source into one alert shape
- Correlates alerts with logs, metric spikes and recent deployment events inside a configurable window
- **RAG over runbooks and past incidents** (Qdrant) feeding a **LangGraph** agent that can query Prometheus, pull logs, and inspect deployments
- Emits a structured RCA — probable cause, confidence score, impacted services, timeline, recommended remediation — audited in Postgres
- Async-first: **FastAPI** + SQLAlchemy async + **arq** on Redis; real Postgres in tests via testcontainers, not SQLite
- Self-hostable on EKS or GKE via a single-command Helm install

*Built in the open from the first commit — the alternatives (PagerDuty AIOps, Moogsoft, Datadog AI) are closed, expensive, and locked to their own ecosystems.*
 
---
 
## ✅ Shipped
 
**[ASIE — Automated Sentiment Intelligence Engine](https://github.com/sharjeel6392/asie)** — *complete, verified on a live AWS cluster*

A production-grade NLP MLOps system that closes the loop: drift triggers retraining, evidence decides promotion, GitOps ships it, and a scheduled job rolls it back if it degrades.

- Reproducible training pipelines with **MLflow** and **DVC**, immutable model promotion
- Kubernetes-native serving on **Amazon EKS** via Helm — HPA, PodDisruptionBudgets, IRSA, zero-downtime rollouts measured at 150/150 requests
- **4-signal drift detection engine** — input distribution, label distribution, confidence shift, shadow disagreement — without ground truth labels
- Alerting pipeline: **Prometheus → Alertmanager → structured webhook events**, with a staleness metric so a dead drift worker can't masquerade as a healthy one
- **GitOps delivery** with ArgoCD — deploying a model is a commit, rolling back is `git revert`
- **Progressive delivery** with Argo Rollouts — 20% → 50% → 100% ALB traffic splitting, each step gated on a Prometheus analysis that aborts on its own
- **Evidence-based promotion** — offline F1 decides *better*, live traffic decides *safe* (sample count, soak, failure rate, p95)
- IaC with **Terraform**: VPC, private subnets, NAT Gateway, RDS Postgres, S3, ECR — no SSH key material anywhere, access via SSM Session Manager
- Whole lifecycle behind one script: `./asie.sh up | pause | resume | down` — full rebuild from an empty AWS account in ~25 minutes

*The result worth reading is the one I didn't plan: drift crossed the threshold, retraining ran, the new model **lost** to the incumbent — and nothing deployed. The gate isn't decoration.*
 
---
 
## 🛠 Stack
 
**Languages**
 
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-121011?style=flat-square&logo=gnu-bash&logoColor=white)
 
**ML & Data**
 
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![DVC](https://img.shields.io/badge/DVC-945DD6?style=flat-square&logo=dvc&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langgraph&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-DC244C?style=flat-square&logo=qdrant&logoColor=white)
 
**Infrastructure & MLOps**
 
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Argo Rollouts](https://img.shields.io/badge/Argo_Rollouts-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apache-airflow&logoColor=white)
 
**Cloud & Observability**
 
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
 
---
 
## 📌 Featured Projects
 
| Project | Stack | Description |
|---|---|---|
| [Aegis AI](https://github.com/sharjeel6392/aegis-ai) | Python · FastAPI · LangGraph · Qdrant · Postgres · Redis | *In progress* — open-source AI incident investigation and RCA for Kubernetes |
| [ASIE](https://github.com/sharjeel6392/asie) | Python · EKS · Helm · Terraform · ArgoCD · Airflow · Prometheus | Closed-loop NLP MLOps platform — drift detection, evidence-gated promotion, canary delivery, automated rollback |
| [Vehicle Insurance MLOps](https://github.com/sharjeel6392/vehicle-insurance-prediction) | Python · FastAPI · S3 · GitHub Actions | Full MLOps pipeline with CI/CD deployment to EC2 via ECR |
| [GPT-2 from Scratch](https://github.com/sharjeel6392/gpt2-like-llm-model) | Python · PyTorch | Transformer architecture built from the ground up |
 
---
 
## ✍️ Writing
 
I document every milestone of what I build on Medium — system design decisions, tradeoffs, and lessons from running this stuff for real. ASIE is written up end to end; Aegis AI is being documented as it's built.
 
📖 [medium.com/@sharjeel6392](https://medium.com/@sharjeel6392)
 
Selected articles:
- [I Stopped Building ML Notebooks — And Started Building Systems](https://medium.com/@sharjeel6392/i-stopped-building-ml-notebooks-and-started-building-systems-ed1feca45774)
- [From EC2 to EKS: What Changes When You Hand Control to an Orchestrator](https://medium.com/@sharjeel6392/from-ec2-to-eks-what-changes-when-you-hand-control-to-an-orchestrator-eb67a3e66492)
- [MLflow Done Properly: What .mlruns Doesn't Tell You](https://medium.com/@sharjeel6392/mlflow-done-properly-what-file-mlruns-doesnt-tell-you-c02a8b6a73fc)
 
---
 
## 📬 Connect
 
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sharjeel-ansari/)
[![Medium](https://img.shields.io/badge/Medium-000000?style=flat-square&logo=medium&logoColor=white)](https://medium.com/@sharjeel6392)
 
📍 Bengaluru, India · Open to relocation · **Open to MLOps / ML Platform / ML Infrastructure roles**
