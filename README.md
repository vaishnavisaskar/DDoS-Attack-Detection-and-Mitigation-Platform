# 🛡️ DDoS Attack Detection and Mitigation System

A Python-based network security project designed to monitor network traffic, detect abnormal traffic patterns, identify potential Distributed Denial of Service (DDoS) activities, and apply mitigation techniques in an isolated laboratory environment.

## 📌 Project Overview

Distributed Denial of Service (DDoS) attacks attempt to overwhelm network resources or servers with excessive traffic, resulting in service disruption.

This project aims to develop a laboratory prototype that continuously monitors network traffic, analyzes packet behavior, detects suspicious traffic patterns, generates security alerts, and applies controlled mitigation measures.

The system uses Python, Scapy, Suricata, Zeek, Wireshark, and Linux networking tools for network monitoring, anomaly detection, and traffic management.

## 🎯 Objectives

- Monitor and capture network packets in real time.
- Analyze TCP and UDP traffic patterns.
- Calculate packets per second (PPS) and bandwidth utilization.
- Identify suspicious TCP SYN traffic patterns.
- Detect abnormal UDP traffic spikes.
- Identify suspicious source IP addresses.
- Generate automated security alerts.
- Apply firewall-based blocking and traffic rate limiting.
- Visualize network traffic and security events through Grafana.

## 🏗️ System Architecture


       Lab Network Traffic
                |
                v
       Packet Collection
          (Scapy)
                |
                v
       Network Analysis
    (Python / Wireshark)
                |
                v
       Security Monitoring
     (Suricata / Zeek)
                |
                v
       Detection Engine
                |
         +------+------+
         |             |
         v             v
    Anomaly Alert   Mitigation
                       |
                +------+------+
                |             |
                v             v
             Firewall     Rate Limiting
            (iptables)       (tc)
                |
                v
         Monitoring System
        (Prometheus)
                |
                v
          Grafana Dashboard

## ⚙️ Technologies Used

| Technology | Purpose |
|---|---|
| Python 3 | Detection engine and automation |
| Scapy | Network packet capture and analysis |
| Suricata | Network intrusion detection |
| Zeek | Network security monitoring |
| Wireshark | Packet inspection |
| Linux `iptables` | Firewall-based mitigation |
| Linux `tc` | Traffic rate limiting |
| Prometheus | Metrics collection |
| Grafana | Monitoring dashboard |
| Ubuntu Linux | Detection server |
| Kali Linux | Controlled laboratory traffic generation |

## ✨ Key Features

### 1. Network Traffic Monitoring
- Capture network packets using Scapy.
- Monitor source and destination IP addresses.
- Identify TCP and UDP protocols.
- Calculate packet counts and packet sizes.

### 2. DDoS Anomaly Detection
- Detect abnormal packet rates.
- Identify potential TCP SYN-flood patterns.
- Detect unusual UDP traffic spikes.
- Monitor suspicious source IP addresses.
- Compare traffic against configurable thresholds.

### 3. Security Alert Generation
- Generate alerts for suspicious traffic.
- Record timestamps and source IP addresses.
- Maintain security event logs.
- Classify detected anomalies by severity.

### 4. Mitigation System
- Apply firewall rules to block approved suspicious lab IPs.
- Implement traffic rate limiting using Linux `tc`.
- Maintain mitigation activity logs.
- Support removal of mitigation rules.

### 5. Monitoring Dashboard
- Display packets per second.
- Monitor bandwidth utilization.
- Visualize TCP and UDP traffic.
- Display security alerts.
- Track mitigation activities.

## 🖥️ Laboratory Environment

The project is designed to run in an isolated virtual network.

| Virtual Machine | Operating System | Responsibility |
|---|---|---|
| VM 1 | Kali Linux | Controlled traffic source |
| VM 2 | Ubuntu Linux | Packet monitoring and detection |
| Host | Windows | Virtual machine management |

Example laboratory IP configuration:

- Kali Linux: `192.168.100.10`
- Ubuntu Server: `192.168.100.20`
- Network: `192.168.100.0/24`

**Note:** Configure both virtual machines using a VMware Host-only network. These are example addresses; adjust them to your actual lab configuration.

## 📂 Project Structure

```text
DDoS-Detection-and-Mitigation/
│
├── detector/
│   ├── packet_capture.py
│   ├── traffic_analyzer.py
│   └── detection_engine.py
│
├── mitigation/
│   ├── firewall.py
│   └── rate_limiter.py
│
├── monitoring/
│   ├── metrics_exporter.py
│   └── grafana-dashboard.json
│
├── integrations/
│   ├── suricata_parser.py
│   └── zeek_parser.py
│
├── config/
│   └── thresholds.json
│
├── logs/
│   └── alerts.json
│
├── tests/
│   └── test_detection.py
│
├── screenshots/
│
├── docs/
│   └── architecture.png
│
├── requirements.txt
├── README.md
└── LICENSE
```

## 🚀 Installation and Setup

### Prerequisites

- Ubuntu Linux
- Kali Linux
- VMware Workstation
- Python 3
- pip
- Git

### Step 1: Clone the Repository

```bash
git clone https://github.com/ShindePankaj26/DDoS-Detection-and-Mitigation.git
```

```bash
cd DDoS-Detection-and-Mitigation
```

### Step 2: Update Ubuntu Packages

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 3: Install Required Packages

```bash
sudo apt install -y python3 python3-pip python3-venv \
tcpdump wireshark iproute2 iptables git curl
```

### Step 4: Create a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 5: Install Python Dependencies

```bash
pip install scapy pandas matplotlib prometheus-client
```

If a `requirements.txt` file is available:

```bash
pip install -r requirements.txt
```

## ▶️ Usage

### Start Network Packet Monitoring

```bash
sudo ./venv/bin/python detector/packet_capture.py
```

### Start the Detection Engine

```bash
python detector/detection_engine.py
```

### Start the Metrics Exporter

```bash
python monitoring/metrics_exporter.py
```

### Monitor Network Traffic

Use Wireshark to inspect captured network packets and Suricata/Zeek logs to investigate network activity.

**Note:** Run only the scripts and integrations that have been implemented in your current project version. The commands above represent the intended application structure.

## 📊 Dashboard Metrics

The Grafana dashboard is intended to display:

| Metric | Description |
|---|---|
| Packets Per Second | Number of packets received per second |
| Bandwidth Utilization | Network data transferred per second |
| TCP Traffic | TCP packet statistics |
| UDP Traffic | UDP packet statistics |
| SYN Packets | TCP SYN packet statistics |
| Suspicious IPs | Sources associated with anomalies |
| Security Alerts | Total detected anomalies |
| Mitigation Status | Active and historical mitigation actions |

## 🧪 Testing Scenarios

The following test scenarios are planned for the laboratory environment:

| Test ID | Test Scenario | Expected Result |
|---|---|---|
| TC-01 | Normal network traffic | Normal status |
| TC-02 | Controlled TCP connection increase | TCP anomaly evaluation |
| TC-03 | Controlled SYN-only traffic | SYN anomaly alert |
| TC-04 | Controlled UDP traffic increase | UDP anomaly alert |
| TC-05 | Increased packet rate | PPS anomaly alert |
| TC-06 | Approved suspicious lab IP | Firewall mitigation |
| TC-07 | Remove firewall rule | Traffic restored |
| TC-08 | Restart monitoring service | Monitoring resumes |

## 📸 Screenshots

Add your actual project screenshots to the `screenshots/` directory.

Suggested screenshots:

1. VMware laboratory network configuration.
2. Python packet capture output.
3. TCP and UDP traffic analysis.
4. SYN anomaly detection alert.
5. UDP spike detection alert.
6. Suricata security events.
7. Zeek connection logs.
8. Firewall mitigation output.
9. Grafana monitoring dashboard.

Example:

```markdown
![Packet Monitoring](screenshots/packet-monitoring.png)

![DDoS Detection Alert](screenshots/ddos-alert.png)

![Grafana Dashboard](screenshots/grafana-dashboard.png)
```

## 🔮 Future Enhancements

- Machine Learning-based network anomaly detection.
- Adaptive traffic threshold configuration.
- Real-time threat intelligence integration.
- Automated incident reporting.
- IP reputation analysis.
- Advanced traffic classification.
- Integration with SIEM platforms such as Splunk and Wazuh.
- Enhanced mitigation policies and recovery automation.

## 🔐 Security and Ethical Considerations

This project is developed strictly for educational and defensive cybersecurity research.

- Use only isolated laboratory environments.
- Test only systems and networks that you own or have explicit permission to assess.
- Never generate flooding traffic against public IP addresses.
- Apply firewall rules carefully to avoid blocking legitimate access.
- Use controlled traffic rates during testing.

## 👨‍💻 Author

**Pankaj Shinde**

Cybersecurity Engineer | Network Security Enthusiast

- GitHub: [ShindePankaj26](https://github.com/ShindePankaj26)
- LinkedIn: [Pankaj Shinde](https://www.linkedin.com/in/pankaj-prakash-shinde-421889352/)

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

⭐ If you find this project useful for learning network security and defensive cybersecurity, consider giving the repository a star.

**Disclaimer:** This project is intended for educational purposes and authorized defensive security testing only.
