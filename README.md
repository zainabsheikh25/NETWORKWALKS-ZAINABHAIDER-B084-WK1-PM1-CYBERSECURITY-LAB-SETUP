# 🔐 Cybersecurity Lab Environment Setup

Building an isolated virtual lab for ethical hacking practice using VirtualBox and Kali Linux.

## Project Overview
I set up a virtual cybersecurity lab with VirtualBox and Kali Linux on a private NAT Network, so more machines can be added later for authorized security testing.

## Lab Configuration
| Component | Configuration |
|---|---|
| Host OS | [Windows version] |
| Host RAM | [your RAM, e.g. 8 GB] |
| Hypervisor | VirtualBox 7.2.14 |
| Security OS | Kali Linux 2026.2 |
| Kali RAM | 2048 MB |
| Network | NAT Network (NatNetwork) |
| Network Address | 10.0.0.0/24 |
| Kali IP | 10.0.0.2/24 (static) |
| Gateway | 10.0.0.1 |
| DNS | 10.0.0.1, 8.8.8.8 |

## Setup Steps

### 1. Tools
Installed 7-Zip and VirtualBox 7.2.14.

### 2. NAT Network
Created a NAT Network named NatNetwork with prefix 10.0.0.0/24 and DHCP enabled.

![NAT Network](1-nat-network.png)

### 3. Kali VM Network
Attached Adapter 1 of the Kali VM to NatNetwork.

![Kali network settings](2-kali-network-settings.png)

### 4. Static IP
Set the Kali IPv4 method to Manual: 10.0.0.2, netmask 24, gateway 10.0.0.1.

![IP and ping](3-kali-ip-and-ping.png)

### 5. Shared Folder
Shared the Windows Downloads folder with Kali. It appears in Kali at /media/sf_Downloads.

![Shared folder](4-shared-folder.png)

### 6. Clipboard and Drag & Drop
Both set to Bidirectional in the VM settings.

![Clipboard and drag/drop](5-clipboard-dragdrop.png)

### 7. Snapshot
Took a snapshot of the finished configuration.

![Snapshot](6-snapshot.png)

## Verification
| Test | Command | Result |
|---|---|---|
| IP address | `ip a` | 10.0.0.2/24 shown |
| Gateway | `ping 10.0.0.1` | Replies received |
| Internet + DNS | `ping google.com` | Replies received |
| Shared folder | `ls /media/sf_Downloads` | Windows files listed |

## Problems Encountered and Solutions
1. **Kali was on plain NAT, not the NAT Network.** Fixed by attaching Adapter 1 to NatNetwork.
2. **Static IP did not apply at first.** Kali still had a DHCP address (10.0.0.3). Fixed by setting the manual IPv4 settings and reconnecting.
3. **DNS failed although pinging 8.8.8.8 worked.** Fixed by adding the gateway 10.0.0.1 as a DNS server.

## What I Learned
- The difference between NAT and NAT Network
- How to set and verify a static IP in Kali Linux
- Why snapshots are useful before experiments
- Documenting problems and fixes is part of the work

## Ethical Use
This lab is for education and authorized testing only.

## Tools
- 7-Zip: https://7-zip.org/download.html
- VirtualBox: https://virtualbox.org/wiki/Downloads
- Kali Linux: https://kali.org/get-kali

## Author
Zainab Haider
Networkwalks Cybersecurity Program, Week 1
