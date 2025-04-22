# aws-high-availability-architecture
# 🏗️ AWS High Availability Architecture

This project demonstrates a **high availability setup on AWS** using:
- Amazon EC2 with Auto Scaling
- Amazon RDS with Multi-AZ deployment
- Elastic Load Balancer
- Amazon Route 53
- Public & Private Subnets inside a VPC

---

## 📌 Architecture Overview

![Architecture](architecture.png)

### Key Components:
- **EC2 Instances**: Application servers in Public Subnets
- **RDS (Multi-AZ)**: Primary DB + Standby replica in Private Subnets
- **Auto Scaling Group**: Ensures scalability and availability
- **Elastic Load Balancer**: Distributes traffic to healthy EC2 instances
- **Route 53**: Handles DNS and domain resolution
- **VPC & Subnets**: Secure networking environment

---

## 💻 Sample Application

A simple PHP + MySQL app is included in the `/app` folder:

- Connects to RDS endpoint
- Inserts & reads data from a table

You can deploy this on EC2 instances after installing Apache + PHP + MySQL client.

---

## 🚀 How to Use

1. Launch infrastructure using AWS Console or Terraform
2. Deploy PHP app on EC2
3. Set up RDS with Multi-AZ
4. Use Route 53 for custom domain routing

---

## 📚 Tech Stack
- AWS EC2, RDS, VPC, ELB, Route 53
- PHP, Apache, MySQL
![image](https://github.com/user-attachments/assets/61f429fb-6df9-44aa-a0b1-25537779085e)
he primary components of the preceding architecture are as follows:

Elastic Load Balancing
AWS routes user traffic through Elastic Load Balancing. A load balancer distributes workloads across multiple compute resources, such as virtual servers. In this sample use case, the Elastic Load Balancer forwards client requests to application servers.

Application servers
Application servers interact with RDS DB instances. An application server in AWS is typically hosted on EC2 instances, which provide scalable computing capacity. The application servers reside in public subnets with different Availability Zones (AZs) within the same Virtual Private Cloud (VPC). .

RDS DB instances
The EC2 application servers interact with RDS DB instances. The DB instances reside in private subnets within different Availability Zones (AZs) within the same Virtual Private Cloud (VPC). Because the subnets are private, no requests from the internet are permitted.

The primary DB instance replicates to another DB instance, called a read replica. Both DB instances are in private subnets within the VPC, which means that Internet users can't access them directly
