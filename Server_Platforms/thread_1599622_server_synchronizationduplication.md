---
title: "server synchronization/duplication"
date: 2010-10-18
forum: Server Platforms
---

### Post by satimis on 2010-10-18
Hi folks,

Host - Ubuntu 1010 desktop 64 bit
VM - Ubuntu 1010 LAMP server 64 bit (w/o GUI)
virtualizer - Oracle VirtualBox

What I'm going to explore is as follows:-

Server-1 - LAMP, a working server on VM-1
Server-2 - LAMP, for redundancy on VM-2

While Server-1 is working all working data will be synchronized/duplicated on Server-2 simultaneously.  When Server-1 is down for whatever cause the network will be switched automatically to Server-2.  No interruption will be caused.  Server-2 will continue to work.  Then Server-1 can be repaired/upgraded/reconfigured etc.


I followed "The Perfect Server - Ubuntu 10.10 [ISPConfig 3]";
[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3)

to install LAMP server on Server-1(VM-1).  Just finished installation.  I'm prepared to clone Server-1(VM-1) as Server-2(VM-2) and then to follow following link;

How To Set Up A Loadbalanced High-Availability Apache Cluster Based On Ubuntu 8.04 LTS
[http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04](http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04)

to proceed installing loadbalanced High Availability on the LAMP server.


I have following questions in doubt:-

1)
I only have 2 servers (VM-1 and VM-2) for the redundancy setup.  Whether I must install 4 servers (4 VMs) to proceed.

2)
In case of only 2 servers (2 VMs) are required for my case whether I can clone Server-1(VM-1) as Server-2(VM-2)?  OR Server-2(VM-2) must be a base server without Apache, MySQL, PHP, etc. installed?

Please shed me some light.  TIA

B.R.
satimis

---

