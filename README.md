# AWS VPC Setup with Public and Private Subnets

## Overview
This guide walks through setting up an AWS Virtual Private Cloud (VPC) with both public and private subnets. It also includes setting up route tables, an Internet Gateway (IGW), a NAT Gateway, a web server, and a database server running MariaDB.

## Steps to Follow

### 1. Create a VPC
- Set up a VPC in North Virginia (us-east-1) with the CIDR range 10.0.0.0/16.

### 2. Set Up Subnets
- Private Subnet: 10.0.1.0/24
- Public Subnet: 10.0.2.0/24

### 3. Configure Route Tables
- Create separate route tables for public and private subnets and associate them accordingly.

### 4. Attach an Internet Gateway
- Create an Internet Gateway (IGW) and attach it to the VPC.

### 5. Deploy a NAT Gateway
- Launch a NAT Gateway in the public subnet so the private subnet can access the internet securely.

### 6. Update Route Tables
- Public Route Table: Direct internet traffic (0.0.0.0/0) through the IGW.
- Private Route Table: Route outbound traffic (0.0.0.0/0) through the NAT Gateway.

### 7. Launch a Web Server
- Deploy an EC2 instance in the public subnet.
- Attach a Security Group that allows HTTP (port 80) and SSH (port 22) access.
- Install and configure a web server (Apache or Nginx).

### 8. Deploy a Database Server
- Launch another EC2 instance in the private subnet.
- Install MariaDB and configure it for secure access.
- Attach a Security Group that allows only SSH (port 22) and database connections (port 3306) from the web server.

### 9. Verify Web Server Access
- Get the public IP of the web server and check if it is accessible from a browser.

### 10. Securely Connect to the Database Server
- SSH into the Web Server and confirm access to the Database Server.

## Expected Results
Web Server should be accessible over the internet.
Database Server should only be accessible from the Web Server.
