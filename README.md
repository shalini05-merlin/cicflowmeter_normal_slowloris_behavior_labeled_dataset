cicflowmeter_normal_slowloris_behavior_labeled.csv
This dataset contains network traffic flows captured from a controlled Software‑Defined Networking (SDN) environment, designed to model realistic botnet‑based Slowloris attacks.

🔬 Generation Environment
Testbed: Mininet with 24 hosts and 3 OpenFlow switches, controlled by the Ryu SDN controller.

Attack Scenario: Multiple distributed hosts (simulating a botnet) target a single HTTP server (h24) with Slowloris attacks, while benign background traffic is also generated.

Traffic Capture: Raw Ethernet PCAP files collected directly from the server using tcpdump.

Feature Extraction: PCAPs processed with CICFlowMeter to produce 84 bidirectional flow features (over 343,000 samples).

🧠 Behaviour‑Driven Labelling
Labels are not based on IP addresses or static rules, but on network flow behaviour characteristic of Slowloris botnet attacks. A flow is labelled as malicious if it simultaneously satisfies:

Protocol: TCP only.

Destination Port: 80 or 443 (HTTP/HTTPS).

Flow Duration: >30 seconds (persistent connection).

Packet Count: Few forward packets (<10).

Payload Size: Small total forward payload (<500 bytes).

TCP Flags: Presence of PSH and ACK flags (partial data, session kept alive).

Additionally, botnet coordination is validated by requiring multiple unique source IPs targeting the same destination IP. This ensures that only distributed, synchronised attack behaviour is labelled as malicious, eliminating false positives from single‑host anomalies.

📁 File Details
Filename: cicflowmeter_normal_slowloris_behavior_labeled.csv

Size: ~188 MB

Samples: ≈343,000

Features: 84 (from CICFlowMeter) + binary label (0 = normal, 1 = Slowloris attack)

🎯 Intended Use
This dataset is suitable for training and evaluating machine learning models for intrusion detection, particularly in research on adversarial robustness and behaviour‑based detection. 
