# Enterprise Network: L3 Switching & VLAN Segmentation

![GNS3](https://img.shields.io/badge/GNS3-v2.2.54-blue)
![Cisco IOU](https://img.shields.io/badge/Tech-Layer%203%20Switching-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

## About
This project implements a distributed enterprise network. Developed for the *Tecnologias de Ligação* course at **ISEC**, the simulation focuses heavily on **Multilayer Switching (L3)** and complex **VLAN structures**.

The goal was to interconnect a Headquarters (RSC) with 7 remote campuses while maintaining strict traffic segmentation and redundancy.

## Key Technical Highlights

### 1. Switching & VLANs (Layer 2/3)
* **Layer 3 Switching:** Core routing at the Headquarters (RSC) is handled by L3 switches (`RSC-SR1`, `SR2`, `SR3`) performing inter-VLAN routing.
* **PVLANs (Private VLANs):** Implemented at the HQ to isolate specific subnets using Promiscuous, Community, and Isolated ports.
* **Q-in-Q (VLAN Tunneling):** Used to transport VLAN tags across the WAN for the ECMA and RE campuses (Double Tagging).
* **Security:** Features like Port Security, BPDU Guard, and Root Guard are enforced.

### 2. WAN & Routing
* **OSPF:** The primary routing protocol, utilizing a Multi-area design (Backbone Area 0 + Stub Areas for remote poles).
* **Redundancy (HSRP):** Configured on the L3 switches to ensure Gateway availability for the VLANs.
* **WAN Technologies:**
    * **MPLS ATOM:** Layer 2 VPN connection for the CID campus.
    * **Frame Relay:** Hub-and-Spoke topology.
    * **Multilink PPP:** Aggregated serial links for bandwidth efficiency.

## Topology Overview
The network centers around the **RSC (Headquarters)**, which aggregates connections from:
* **Campus Poles:** CE, CCS, ECMA, CID, BCRD, CML, RE.
* **Internet:** Redundant ISP connections with primary and backup links.
