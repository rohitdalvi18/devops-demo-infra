# DevOps Demo Infrastructure

Infrastructure repository for DevOps Demo project containing EKS provisioning Infrastructure as Code (Terraform/CloudFormation) and Kubernetes manifests with overlays.

## 🏗️ Architecture Overview

This repository implements a comprehensive DevOps pipeline with automated infrastructure provisioning and deployment workflows for AWS EKS environments. The infrastructure supports multiple deployment environments with blue-green deployment strategies.

## 🚀 Features

- **Infrastructure as Code**: Terraform/CloudFormation templates for AWS EKS cluster provisioning
- **Kubernetes Manifests**: Application deployment configurations with environment-specific overlays
- **Automated CI/CD Pipelines**: GitHub Actions workflows for continuous integration and deployment
- **Blue-Green Deployment**: Zero-downtime deployment strategy implementation
- **Multi-Environment Support**: Separate workflows for QA, UAT, and production environments
- **Nightly Builds**: Automated testing and deployment validation


## 🔄 CI/CD Workflows

### **Nightly Build Pipeline**
Automated nightly deployment routine that validates infrastructure and application deployments:
- Triggers on push to master/dev branches or manual dispatch
- Builds and tests Docker images
- Deploys to temporary EC2 for smoke testing
- Pushes validated images to AWS ECR
- Deploys to QA environment

### **Environment-Specific Deployments**

#### **QA Environment**
- Automated deployment to QA environment
- Integration testing and validation
- Environment-specific configuration management

#### **UAT Environment**
- User Acceptance Testing deployment pipeline
- Pre-production validation
- Stakeholder approval workflows

### **Blue-Green Deployment Strategy**

#### **Deploy to Green**
- Deploys new version to green environment
- Performs health checks and validation
- Maintains blue environment as fallback

#### **Promote Green to Blue**
- Switches traffic from blue to green environment
- Zero-downtime deployment completion
- Automated rollback capabilities

## 🛠️ Prerequisites

- AWS Account with appropriate IAM permissions
- Docker installed locally
- kubectl configured for EKS access
- Terraform CLI (if running locally)
- GitHub repository secrets configured

## 📊 Monitoring & Observability

### **Prometheus & Grafana Stack**

This infrastructure includes a comprehensive monitoring solution using Prometheus for metrics collection and Grafana for visualization.

#### **Prometheus Configuration**

- **Node Exporter**: System-level metrics collection (CPU, memory, disk I/O)
- **Custom Application Metrics**: Business logic and performance monitoring
- **Scrape Interval**: 10-second metric collection frequency
- **Remote Write**: Integration with Grafana Cloud for centralized metrics storage

#### **Grafana Dashboards**

- **Infrastructure Monitoring**: Real-time system resource utilization
- **Application Performance**: Request latency, throughput, and error rates
- **Deployment Tracking**: Blue-green deployment status and health metrics
- **Custom Alerts**: Slack/email notifications for critical thresholds

#### **Access Points**

| Service | URL | Credentials |
|---------|-----|-------------|
| **Prometheus** | `http://your-domain:9090` | No authentication |
| **Grafana** | `http://your-domain:3000` | admin/admin (default) |
| **Node Exporter** | `http://your-domain:9100/metrics` | Metrics endpoint |

#### **Monitoring Features**

- **Real-time Metrics**: Live system and application performance data
- **Historical Analysis**: Time-series data for trend analysis
- **Alerting Rules**: Automated notifications for threshold breaches
- **Custom Dashboards**: Tailored visualizations for different stakeholders
- **Integration**: Seamless connection with CI/CD pipeline monitoring


## 🚦 Deployment Environments

| Environment | Purpose | Trigger | Deployment Strategy |
|-------------|---------|---------|-------------------|
| **QA** | Quality assurance testing | Automated on merge | Direct deployment |
| **UAT** | User acceptance testing | Scheduled | Staged deployment |
| **Production** | Live environment | Manual approval | Blue-green deployment |



## 📝 License

This project is licensed under the MIT License

---
