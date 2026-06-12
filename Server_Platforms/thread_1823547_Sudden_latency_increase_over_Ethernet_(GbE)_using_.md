---
title: "Sudden latency increase over Ethernet (GbE) using NFS v3"
date: 2011-08-12
forum: Server Platforms
---

### Post by davidpb on 2011-08-12
Hi, I'm doing some experiments on high perfomance storage using 10 ubuntu 10.04 LTS servers as my test clients, with the storage mounted on the clients using nfs-common (NFS v3). I have been testing using an open source tool called msmeter from sourceforge, based on iometer.

I have a mix of Ubuntu 0.04.01 LTS and 10.04.02 LTS server. After trying various different swtches, switch configurations and storage configurations, the latency all my 10.04.1 LTS clients when reading files has more than doubled, while my 10.04.02 clients remain unaffected.

When testing the latency, the latency value ramps up from normal (20ms) to poor (50ms) after several measurements, as if a buffer is being overun of filled, e.g.

rd1 started
test000 1024k   5  read    105.88 MB/s, Latency 20.12 ms  
test000 1024k   7  read    104.29 MB/s, Latency 20.13 ms  
test000 1024k   7  read    105.25 MB/s, Latency 20.16 ms  
test000 1024k   2  read    102.89 MB/s, Latency 20.16 ms 
test000 1024k   4  read    103.54 MB/s, Latency 53.36 ms  
test000 1024k   9  read    105.15 MB/s, Latency 53.30 ms
test000 1024k   2  read    100.24 MB/s, Latency 53.32 ms  
test000 1024k   7  read    104.59 MB/s, Latency 53.30 ms 

While clients without the problem give consistent latency measurements of 20 to 26ms.

Without any adjustment on my part, the network interface or stack on my 10.04.01 LTS clients has gone into a state with increased latency. This is independant of the storage server, switch settings and it persists after network restart, hard reset and an update to ubuntu from 10.04.1 LTS to 10.04.03 LTS.

Has anyone seen this before or know how to fix it?

Each server has the same hardware and using ifconfig, ethtool, lshw and lscpi all the networtk settings appear the same.

e.g servers rd1 and rd3 have the latrency problem, but rd9 does not.

user@rd1:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid
user@rd1:~$ uname -a
Linux rdch100 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux

user@rd3:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid
user@rdch3:~$ uname -a
Linux rdch130 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

user@rd9:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid
user@rdc9:~$ uname -a
Linux rdch190 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

$ mount.nfs -V
mount.nfs (linux nfs-utils 1.1.6)
rduser@rdch100:~$

$ lspci
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet (rev 20)
        Subsystem: Dell Device 02a5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at da000000 (64-bit, non-prefetchable) [size=32M]
        Capabilities: <access denied>
        Kernel driver in use: bnx2
        Kernel modules: bnx2

$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: NetXtreme II BCM5716 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 20
       serial: bc:30:5b:d6:d3:de
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=bnx2 driverversion=2.0.2 firmware=5.2.3 NCSI 2.0.11 ip=192.168.20.90 latency=0 multicast=yes

$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

---

### Post by caralb on 2012-01-04
Hi Davidpb,

It seems I am having the same problem as you. I work at a networking lab with GbE and NFS running on an Ubuntu 10.04 server . Most of my colleages updated to Lucid so they have no problems, but I kept running Ubuntu Hardy due to compatibility problems with other software. It takes me about 10 seconds to open/store a file on the server, it makes my work very difficult sometimes. 

Did you find some solution? I am looking for info on the internet but without any success yet. I will let you know I I find something.

Thank you for your help, greetings from Argentina!


Carlos

---

### Post by davidpb on 2012-01-05
Hi Carlos,

My problem was a down due to bios and the motherboard chipset. The TCP window size had become corrupted and stored in the motherbaord non-volatile memory, I belive it was due to a problme with extended TCP window size. The TCP window size could could not be reset or written using any command line or bios settings. Fortuantely my servers were in warranty and the manufacturer repalced all 7 the motherboards.

My problem doubled the latency, but was still only aboout 50ms. Your storage problem sounds more serious. Dou you have large files? Are you using default nfs mount options, is it a time out problem?

Sorry I can't give you any soultion for this, Dave.

---

