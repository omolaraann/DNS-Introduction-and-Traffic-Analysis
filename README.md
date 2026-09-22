# 🌐 DNS Introduction and Traffic Analysis

A practical cybersecurity lab focused on understanding, capturing, analysing, and documenting **Domain Name System (DNS) traffic** using Kali Linux, `dig`, TShark, and Wireshark-compatible packet captures.

This project demonstrates how DNS requests move between a client and a recursive resolver, how different DNS record types are queried and returned, how EDNS information appears in DNS packets, and how packet-level evidence can be examined from a digital forensics perspective.

The lab also applies basic evidence-handling principles by preserving packet captures, calculating SHA-256 hashes, extracting structured DNS transaction data, and maintaining command outputs as supporting forensic evidence.

---

## 🧭 Project Overview

DNS is a fundamental component of network communication. Before a system can communicate with many internet services using a domain name, that domain must be resolved into information such as an IPv4 address, IPv6 address, or mail-exchange record.

This lab investigates DNS traffic generated while querying:

* **A records** - IPv4 addresses
* **AAAA records** - IPv6 addresses
* **MX records** - mail-exchange information

The traffic was captured and subsequently analysed at packet level to identify:

* DNS clients and resolvers
* Source and destination IP addresses
* UDP ports
* DNS transaction IDs
* Query names
* Query types
* Response codes
* Answer counts
* Returned DNS records
* TTL values
* EDNS/OPT information
* Recursive-resolution indicators
* Query/response timing
* DNS communication patterns
* Potential forensic indicators
* Evidence integrity through SHA-256 hashing

---

## 🎯 Objectives

The primary objectives of this lab were to:

🔹 Understand the role of DNS in network communication

🔹 Generate controlled DNS queries using `dig`

🔹 Capture DNS traffic for forensic analysis

🔹 Analyse DNS packets using TShark

🔹 Examine DNS A, AAAA, and MX queries and responses

🔹 Correlate live DNS resolution results with packet-capture evidence

🔹 Identify the DNS resolver involved in the transactions

🔹 Examine EDNS and OPT records

🔹 Analyse DNS response behaviour

🔹 Identify basic forensic indicators within the captured traffic

🔹 Preserve packet captures and analytical outputs as evidence

🔹 Calculate SHA-256 hashes for evidence integrity

🔹 Produce structured forensic documentation from raw network evidence

---

## 🖥️ Laboratory Environment

The analysis was performed in a Kali Linux environment.

| Component                     | Details       |
| ----------------------------- | ------------- |
| Operating System              | Kali Linux    |
| DNS Testing Tool              | `dig`         |
| Packet Analysis Tool          | TShark        |
| Packet Capture Format         | PCAP / PCAPNG |
| Primary DNS Resolver Observed | `8.8.8.8`     |
| DNS Protocol                  | DNS over UDP  |
| DNS Port                      | UDP/53        |
| Query Domain                  | `example.com` |
| Query Types                   | A, AAAA, MX   |
| Evidence Hashing              | SHA-256       |

---

## 📁 Repository Structure

```text
DNS-Introduction-and-Traffic-Analysis/
│
├── 📄 README.md
├── 📄 .gitignore
│
├── 📁 Screenshots/
│   ├── 🖼️ A Record Baseline and DNS Query.png
│   ├── 🖼️ AAAA Record Baseline and DNS Query.png
│   ├── 🖼️ Consolidated DNS Transaction Table.png
│   ├── 🖼️ DNS Baseline_to_PCAP Correlation Findings.png
│   ├── 🖼️ DNS Communication and Infrastructure Analysis.png
│   ├── 🖼️ DNS Flags and Recursion Analysis.png
│   ├── 🖼️ DNS Packet Capture and PCAP Acquisition.png
│   ├── 🖼️ DNS Packet Level.png
│   ├── 🖼️ DNS Query Behavior Analysis.png
│   ├── 🖼️ DNS Resolver Configuration.png
│   ├── 🖼️ DNS Response Status and Answer Counts.png
│   ├── 🖼️ DNS packet field extraction.png
│   ├── 🖼️ Detailed AAAA DNS Query and EDNS OPT Analysis Packet3.png
│   ├── 🖼️ Detailed AAAA DNS Query and EDNS OPT AnalysisPacket3b.png
│   ├── 🖼️ Detailed AAAA DNS Response and EDNS OPT AnalysisPacket4.png
│   ├── 🖼️ Detailed AAAA DNS Response and EDNS OPT AnalysisPacket4c.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis Frame 2.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis Frame1.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis Frame2b.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis Frame2c.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis.png
│   ├── 🖼️ Detailed DNS Query and EDNS OPT Analysis1.png
│   ├── 🖼️ Detailed MX DNS Query and EDNS OPT AnalysisPacket5.png
│   ├── 🖼️ Detailed MX DNS Query and EDNS OPT AnalysisPacket5b.png
│   ├── 🖼️ Detailed MX DNS Response and EDNS OPT AnalysisPacket6.png
│   ├── 🖼️ Detailed MX DNS Response and EDNS OPT AnalysisPacket6b.png
│   ├── 🖼️ Detailed MX DNS Response and EDNS OPT AnalysisPacket6c.png
│   ├── 🖼️ EDNS Field Extraction Validation.png
│   ├── 🖼️ EDNS and DNSSEC Field Analysis.png
│   ├── 🖼️ Lab Workspace Preparation.png
│   ├── 🖼️ Live A Record Query.png
│   ├── 🖼️ Live AAAA Record Query.png
│   ├── 🖼️ Live DNS Capture Evidence Preservation.png
│   ├── 🖼️ Live DNS Capture.png
│   ├── 🖼️ Live DNS Traffic Capture Validation.png
│   ├── 🖼️ Live MX Record Query.png
│   ├── 🖼️ Live NS Record Query.png
│   ├── 🖼️ MX Record Baseline and DNS Query.png
│   ├── 🖼️ NS Record Baseline and DNS Query.png
│   ├── 🖼️ Network Capture Interface Verification.png
│   ├── 🖼️ SHA-256 DNS Capture Integrity Verification.png
│   ├── 🖼️ Tool and Version Verification.png
│   ├── 🖼️ Tool and Version Verification2.png
│   ├── 🖼️ Upstream DNS and Network Interface Verification.png
│   ├── 🖼️ Working Copy Creation.png
│   └── 📄 .gitkeep
│
├── 📁 evidence/
│   ├── 📦 dig_dns.pcap
│   └── 📦 fresh_dig_dns.pcapng
│
├── 📁 reports/
│   ├── 📄 dig_example_A.txt
│   ├── 📄 dig_example_AAAA.txt
│   ├── 📄 dig_example_MX.txt
│   ├── 📄 dig_example_NS.txt
│   ├── 📄 dig_example_short.txt
│   ├── 📄 dns_answer_records.txt
│   ├── 📄 dns_baseline_pcap_correlation.txt
│   ├── 📄 dns_capture_hashes.txt
│   ├── 📄 dns_communication_analysis.txt
│   ├── 📄 dns_consolidated_transactions.txt
│   ├── 📄 dns_forensic_indicator_check.txt
│   ├── 📄 dns_query_behaviour.txt
│   ├── 📄 final_dns_forensic_summary.txt
│   ├── 📄 fresh_dns_capture_hash.txt
│   ├── 📄 fresh_dns_packet_summary.txt
│   ├── 📄 resolv_conf.txt
│   └── 📄 resolvectl_status.txt
│
└── 📁 working/
    └── 📦 dig_dns_working.pcap
```

### 🗂️ Directory Overview

| 📁 Directory / File | 🔍 Description                                                                                                                                                                                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 📄 `README.md`      | Main project documentation containing the assignment overview, methodology, tools, investigation process, findings, evidence summary, and conclusion.                                                                                                               |
| 📁 `Screenshots/`   | Contains the supporting screenshots captured throughout the investigation, including workspace preparation, DNS configuration, baseline queries, packet capture, packet-level analysis, EDNS analysis, evidence preservation, correlation, and forensic assessment. |
| 📁 `evidence/`      | Contains the preserved DNS packet-capture evidence used during the investigation.                                                                                                                                                                                   |
| 📁 `reports/`       | Contains extracted DNS results, packet-analysis outputs, communication analysis, baseline correlation, integrity records, forensic indicator checks, and the final DNS forensic summary.                                                                            |
| 📁 `working/`       | Contains the working copy of the supplied DNS packet capture used during analysis.                                                                                                                                                                                  |
| 📄 `.gitignore`     | Defines temporary, working, system, and other files that should not be added to version control.                                                                                                                                                                    |

---

## 🔬 DNS Traffic Captured

A controlled DNS capture was generated containing three DNS query/response transactions.

The capture contains **six DNS packets**:

```text
Client → Resolver   A query
Resolver → Client   A response

Client → Resolver   AAAA query
Resolver → Client   AAAA response

Client → Resolver   MX query
Resolver → Client   MX response
```

The observed client was:

```text
192.168.232.128
```

The DNS resolver was:

```text
8.8.8.8
```

The communication used:

```text
UDP/53
```

The three DNS transactions were matched using their DNS transaction IDs.

| Query         | DNS ID   | Query Type | Result           |
| ------------- | -------- | ---------- | ---------------- |
| `example.com` | `0x253e` | A          | 2 IPv4 addresses |
| `example.com` | `0x32af` | AAAA       | 2 IPv6 addresses |
| `example.com` | `0x5ea3` | MX         | MX value `.`     |

---

## 🌍 A Record Analysis

The A-record transaction requested the IPv4 addresses associated with `example.com`.

The DNS query was sent from the local client to:

```text
8.8.8.8:53
```

The response returned:

```text
104.20.23.154
172.66.147.243
```

Both records had a TTL of:

```text
300 seconds
```

The response used the same transaction ID as the query:

```text
0x253e
```

This allowed the request and response to be correlated directly within the packet capture.

The response had:

```text
RCODE = 0
RA = True
RD = True
```

indicating a successful DNS response with recursion available and recursion desired.

---

## 🛰️ AAAA Record Analysis

The AAAA transaction was used to identify IPv6 addresses associated with `example.com`.

The response returned:

```text
2606:4700:10::ac42:93f3
2606:4700:10::6814:179a
```

Both records had a TTL of:

```text
300 seconds
```

The transaction ID was:

```text
0x32af
```

The query and response were therefore directly correlated using the DNS transaction identifier.

The response also returned:

```text
RCODE = 0
RA = True
RD = True
```

---

## ✉️ MX Record Analysis

The MX query requested mail-exchange information for:

```text
example.com
```

The transaction ID was:

```text
0x5ea3
```

The response returned an MX preference of:

```text
0
```

with the exchange represented by:

```text
.
```

The value observed in the packet capture was consistent with the live DNS query performed during baseline testing.

The TTL observed in the live baseline query differed from the TTL in the captured packet. This is expected behaviour because DNS TTL values are dynamic and decrease as cached records age.

---

## ⚙️ EDNS / OPT Analysis

The DNS packets also contained EDNS information through the OPT pseudo-record.

The analysis identified the following EDNS characteristics:

| EDNS Attribute            | Observation   |
| ------------------------- | ------------- |
| EDNS Version              | 0             |
| DNSSEC OK / DO            | False         |
| Extended RCODE            | 0             |
| Query UDP Payload Size    | 1472          |
| Response UDP Payload Size | 512           |
| Additional OPT Record     | Present       |
| EDNS Option Data          | None observed |

EDNS allows DNS implementations to extend the capabilities of the traditional DNS protocol while retaining compatibility with the existing protocol structure.

The presence of an OPT record therefore provides additional protocol-level information that can be useful during packet analysis.

---

## 🔎 DNS Communication Analysis

The communication analysis established a clear client-to-resolver relationship.

```text
192.168.232.128
        │
        │ UDP/53
        ▼
     8.8.8.8
```

Three different ephemeral client source ports were observed:

```text
42371
34860
40274
```

The destination port for each DNS request was:

```text
53
```

Responses originated from:

```text
8.8.8.8:53
```

and were sent back to the corresponding client source ports.

This behaviour is consistent with normal UDP-based DNS request/response communication.

---

## ⏱️ Transaction Timing

The complete capture lasted approximately:

```text
0.451421448 seconds
```

The observed response times were approximately:

| Transaction | Response Time |
| ----------- | ------------: |
| A           |     145.38 ms |
| AAAA        |      91.06 ms |
| MX          |      91.69 ms |

Each request received a corresponding response within the captured period.

No retransmitted DNS query was observed in this six-packet sample.

---

## 🧪 Query Behaviour

The capture contained only one queried domain:

```text
example.com
```

The domain was queried using three DNS record types:

```text
A
AAAA
MX
```

Each query appeared once within the capture.

There was no evidence within this limited capture of:

🔹 Repeated high-frequency DNS queries

🔹 Large volumes of DNS traffic

🔹 Multiple queried domains

🔹 Multiple external DNS resolvers

🔹 DNS response failures

🔹 Truncated DNS responses

The small size of the capture is important when interpreting these observations. The absence of an indicator within six packets does not establish that the indicator could never occur on the system.

---

## 🕵️ Forensic Indicator Assessment

A basic forensic indicator check was performed against the captured DNS traffic.

The analysis examined:

* DNS response codes
* Query names
* DNS conversations
* Packet count
* Resolver destination
* Query frequency

All three DNS responses returned:

```text
RCODE = 0
```

The observed resolver reported recursion availability.

The only query name identified was:

```text
example.com
```

The capture contained six DNS packets representing three complete query/response pairs.

Based on the limited sample, the traffic demonstrated a straightforward DNS resolution pattern rather than a high-volume or complex DNS communication pattern.

This assessment is intentionally limited to the available evidence and should not be interpreted as a determination about DNS activity outside the captured timeframe.

---

## 🔗 Baseline-to-PCAP Correlation

Live DNS resolution was performed separately using `dig` and compared with the packet-capture results.

The A-record results observed during baseline testing matched the addresses recovered from the packet capture:

```text
104.20.23.154
172.66.147.243
```

The AAAA-record results also matched:

```text
2606:4700:10::ac42:93f3
2606:4700:10::6814:179a
```

The MX response value was also consistent with the captured result.

The MX TTL differed between the baseline query and the packet capture, which is expected because TTL values change over time as DNS records age in caches.

This correlation provided an additional validation point between live DNS resolution and packet-level evidence.

---

## 🧾 Evidence Integrity

The primary fresh DNS capture is:

```text
evidence/fresh_dig_dns.pcapng
```

The capture contains:

```text
Packets:       6
File size:     1,140 bytes
Duration:      0.451421448 seconds
```

SHA-256:

```text
a7551c00dea38d2332391df578f6ebfa2ec4164f7475778e78dedc1d4ee28904
```

The SHA-256 value was calculated and documented as part of the evidence-handling process.

Hashing provides a reproducible integrity value that can be recalculated later to determine whether the file contents have changed.

---

## 📦 Reference Evidence

The repository also contains:

```text
evidence/dig_dns.pcap
```

This is the supplied/reference DNS packet capture used during the lab.

Its SHA-256 hash is:

```text
9a7c1b95aa6d60f8ac0ee9a79e06ae51145bb7768974526546316cd3dc91375d
```

A working copy was also retained:

```text
working/dig_dns_working.pcap
```

The working copy was verified to have the same SHA-256 hash as the supplied reference capture.

---

## 🛠️ Tools Used

### 🐧 Kali Linux

The primary analysis environment used for executing DNS queries, packet capture, command-line analysis, and evidence handling.

### 🔍 `dig`

Used to generate controlled DNS queries and retrieve:

* A records
* AAAA records
* MX records
* NS records
* Short-form DNS responses

### 🦈 TShark

Used for command-line packet analysis and structured extraction of:

* DNS transaction IDs
* Query names
* Query types
* Response codes
* Answer counts
* IP addresses
* IPv6 addresses
* TTL values
* EDNS fields
* Source/destination information
* UDP ports
* Query timing

### 🧪 Packet Capture

PCAP and PCAPNG files were retained as primary network evidence for subsequent analysis.

### 🔐 SHA-256

Used to establish cryptographic integrity values for packet-capture evidence.

---

## 📋 Analysis Outputs

The `reports/` directory contains individual outputs generated during the investigation.

### 📄 DNS Query Outputs

```text
dig_example_A.txt
dig_example_AAAA.txt
dig_example_MX.txt
dig_example_NS.txt
dig_example_short.txt
```

These files contain the results of controlled DNS lookups.

### 📄 Packet Analysis Outputs

```text
fresh_dns_packet_summary.txt
dns_answer_records.txt
dns_consolidated_transactions.txt
dns_communication_analysis.txt
dns_query_behaviour.txt
dns_forensic_indicator_check.txt
```

These contain structured information extracted from the packet captures.

### 📄 Correlation and Integrity Outputs

```text
dns_baseline_pcap_correlation.txt
dns_capture_hashes.txt
fresh_dns_capture_hash.txt
final_dns_forensic_summary.txt
```

These document evidence correlation, hashing, and the consolidated findings.

### 📄 Local DNS Configuration

```text
resolv_conf.txt
resolvectl_status.txt
```

These preserve relevant local DNS resolver configuration and status information observed during the investigation.

---

## 🧠 Key Findings

The investigation established the following from the captured evidence:

🔹 DNS communication occurred between the local client `192.168.232.128` and resolver `8.8.8.8`.

🔹 DNS requests were transmitted using UDP port 53.

🔹 Three DNS query types were observed: A, AAAA, and MX.

🔹 All three DNS queries received corresponding responses.

🔹 All observed responses returned `RCODE 0`.

🔹 The A query returned two IPv4 addresses.

🔹 The AAAA query returned two IPv6 addresses.

🔹 The MX query returned an MX preference of `0` with exchange `.`.

🔹 EDNS OPT records were present in the DNS transactions.

🔹 EDNS version 0 was observed.

🔹 The DNSSEC OK/DO flag was not set.

🔹 No repeated DNS queries were observed within the six-packet sample.

🔹 No DNS response failures were observed.

🔹 The captured A and AAAA answers correlated with independent live DNS resolution.

🔹 The evidence capture was successfully hashed using SHA-256.

---

## ⚠️ Scope and Limitations

This analysis is based on a controlled and deliberately small DNS traffic sample.

The fresh capture contains only:

```text
6 DNS packets
3 DNS transactions
1 queried domain
```

Therefore, the findings describe the behaviour visible within the captured timeframe only.

A short capture cannot be used to determine long-term DNS behaviour, historical activity, or the complete security posture of a host.

Similarly, the absence of DNS tunnelling, DGA-like activity, excessive DNS traffic, or other suspicious characteristics in this sample does not establish that such activity could not occur outside the captured period.

The conclusions in this repository are therefore limited to the evidence collected and analysed.

---

## 🔐 Forensic Handling Approach

The investigation followed a simple evidence-preservation workflow:

```text
📥 Collect
   ↓
📦 Preserve packet capture
   ↓
🔐 Calculate SHA-256 hash
   ↓
🔍 Analyse packets
   ↓
📊 Extract structured evidence
   ↓
🔗 Correlate with baseline DNS results
   ↓
📝 Document findings
```

The original packet evidence was retained while analytical outputs were stored separately under `reports/`.

This separation helps distinguish the network evidence itself from derived analytical results.

---

## 📚 Skills Demonstrated

This project demonstrates practical experience with:

🛡️ Network Forensics

🌐 DNS Analysis

🔍 Packet Analysis

🧪 Digital Evidence Handling

🐧 Kali Linux

🦈 TShark

🔎 Wireshark-compatible PCAP/PCAPNG analysis

🧰 `dig`

📡 UDP/DNS Traffic Analysis

🧾 DNS Record Analysis

⚙️ EDNS Analysis

🔗 Evidence Correlation

🔐 SHA-256 Evidence Hashing

📊 Structured Command-Line Data Extraction

📝 Technical Security Documentation

---

## 💡 Why This Lab Matters

DNS traffic is often overlooked because DNS queries are small and usually occur in the background. However, DNS provides valuable visibility into network behaviour.

From a security perspective, DNS traffic can help analysts investigate:

🔹 Domain resolution activity

🔹 Command-and-control infrastructure

🔹 Malware communication patterns

🔹 DNS tunnelling

🔹 Domain-generation activity

🔹 Suspicious resolver usage

🔹 Abnormal query volumes

🔹 Failed or unusual DNS responses

🔹 Network configuration issues

This lab establishes the foundational packet-analysis skills required before moving into more advanced DNS threat-hunting and forensic investigations.

---

## 🚀 Potential Next Steps

Future extensions of this project could include:

🔹 Capturing larger DNS datasets

🔹 Comparing normal and suspicious DNS behaviour

🔹 Analysing DNS tunnelling techniques

🔹 Investigating DNS TXT records

🔹 Detecting unusually long DNS queries

🔹 Analysing high-entropy domain names

🔹 Examining NXDOMAIN patterns

🔹 Investigating DNS beaconing

🔹 Comparing UDP DNS with TCP DNS

🔹 Analysing DNS over HTTPS (DoH)

🔹 Analysing DNS over TLS (DoT)

🔹 Building automated DNS anomaly detection scripts

🔹 Developing a DNS forensic timeline

🔹 Integrating DNS analysis with SIEM or threat-intelligence workflows

---

## 🏁 Conclusion

This project demonstrates a complete, evidence-driven workflow for basic DNS traffic analysis.

Controlled DNS queries were generated, network traffic was captured, DNS transactions were reconstructed, record-level answers were extracted, EDNS information was examined, resolver communication was identified, baseline results were correlated with packet evidence, and cryptographic hashes were generated to support evidence integrity.

The analysis showed a small set of successful DNS transactions involving A, AAAA, and MX records for `example.com`, with all observed responses returning successfully.

The resulting packet captures, command outputs, analytical evidence, configuration information, and integrity records have been retained in this repository to provide a reproducible record of the investigation.

---

### 🔖 Project Focus

**DNS • Network Forensics • Packet Analysis • Cybersecurity • Digital Evidence • Threat Hunting • Kali Linux • TShark • Wireshark • DNS Investigation**
