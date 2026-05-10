# 🛡️ Cloud-Native SOC Analyst Lab: AWS Honeypot & Splunk Integration

A cloud-native cybersecurity project focused on deploying a publicly exposed Windows honeypot on AWS to capture and analyze real-world brute-force attacks using Splunk Cloud SIEM.

---

## 🧠 Features

- ☁️ AWS EC2 Honeypot Deployment
- 🪟 Windows Server 2025 Target Machine
- 🔓 Public Exposure using RDP (3389) & ICMP
- 📡 Real-time Log Collection using Splunk Universal Forwarder
- 🔐 SSL Encrypted Log Transmission to Splunk Cloud
- 🌍 Geolocation-based Threat Intelligence
- 📊 Splunk Dashboards & Visualizations
- 🛡️ Failed Login & Attack Pattern Analysis
- 📈 SPL Query-based Security Insights

---

## 🛠️ Tech Stack

### Infrastructure
- AWS EC2
- AWS VPC
- AWS Security Groups

### Operating System
- Windows Server 2025

### SIEM & Monitoring
- Splunk Cloud (SaaS)
- Splunk Universal Forwarder

### Analysis
- SPL (Splunk Processing Language)
- Geolocation Lookups

---

# 🏗️ Architecture & Data Flow

1. Deployed a Windows VM in AWS Stockholm Region.
2. Opened RDP Port 3389 and ICMP to the public internet.
3. Installed Splunk Universal Forwarder on the VM.
4. Forwarded Windows Security Event Logs to Splunk Cloud.
5. Analyzed brute-force attacks using SPL Queries and Dashboards.

---

# 🚀 Key Findings

- 📌 Total Attack Events Captured: **1,031**
- ❌ Failed Login Attempts: **934**
- 🌍 Top Attacking Countries:
  - Andorra — 779
  - Mexico — 52
  - Germany — 47
- 🎯 Most Targeted Username: `Administrator`
- ⏱️ Honeypot discovered within minutes of deployment

---

# 📸 Screenshots

## ☁️ AWS Environment

### AWS Interface
![AWS Interface](Evidences/AWS%20interface.png)

### AWS EC2 Instance
![AWS Instance](Evidences/AWS%20instance.png)

### Windows VM
![Windows VM](Evidences/AWS%20VM%20windows%2010.png)

---

## 🔓 Firewall & Connectivity

### Windows Firewall Configuration
![Firewall](Evidences/settingwindow.png)

### ICMP / Ping Verification
![Ping](Evidences/Checkingping.png)

---

## 📡 Splunk Forwarder Setup

### Splunk Universal Forwarder
![Splunk Forwarder](Evidences/SplunkFarwader.png)

---

## 📊 Splunk Analysis Dashboard

### Splunk Dashboard
![Dashboard](Evidences/SplunkDashboard.png)

### Attack Cluster Map
![Cluster Map](Evidences/ClusterMap.png)

### Login Attempt Analysis
![Login Attempts](Evidences/loginattempt.png)

### Statistical Analysis
![Statistics](Evidences/Statistic%20Data.png)

### Pie Chart Visualization
![Pie Chart](Evidences/PieChart.png)

### Line Chart Visualization
![Line Chart](Evidences/LineChart.png)

### Final Splunk Report
![Splunk Report](Evidences/SplunkReport.png)

---

# 📜 Sample SPL Queries

## 🌍 Geolocation Map Query

```spl
index="honeypot_logs" EventCode=4625 
| iplocation Source_Network_Address 
| geostats count by Country
```

## 📊 Success vs Failure Analysis

```spl
index="honeypot_logs" (EventCode=4624 OR EventCode=4625)
| eval Result=if(EventCode=4624, "Successful Login", "Failed Attempt")
| stats count by Result
```

---

# 🧹 Cleanup & Security Hygiene

To avoid unnecessary cloud costs and maintain security hygiene:

- ✅ Terminated AWS EC2 Instance
- ✅ Deleted Attached EBS Volumes
- ✅ Revoked Splunk Cloud Credentials
- ✅ Removed Forwarder Configuration

---

# 📄 Report

Included detailed report:

- `24-Hour Honeypot Threat Intelligence Report.pdf`

---

# 📄 License

This project is intended for educational and cybersecurity research purposes only.
