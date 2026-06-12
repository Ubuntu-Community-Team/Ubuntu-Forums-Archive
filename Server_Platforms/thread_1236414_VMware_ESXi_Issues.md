---
title: "VMware ESXi Issues"
date: 2009-08-10
forum: Server Platforms
---

### Post by dipeshmehta on 2009-08-10
I want to run three server OS (Windows 2003 Enterprise, Ubuntu 8.04 LTS Server & Untangle (based on Debian Lenny)) on a single physical server.

My server hardware is: HP ML110G5 Server running on Intel Xeon 3065 @ 2.33 GHz with 4 GB RAM and 160 GB SATA hard drive.  This is a very small business scenario and this server has to entertain only 7 clients.

After reviewing the things, I finally selected VMWare ESXi as hypervisor.  I have successfully installed all three OS. 

Now, there are couple of problems I have been facing:

1. Out of three, at present only two - Windows 2003 and Ubuntu 8.04 are in use.  Both OS hangs etc approx 2-3 times a day.  Most of at the morning, when client tries to connect the server, it can't.  I checked logs at server also, but couln't find anything.  Even I can not get into console using VMI Client.  At last, to power off the VM remains the only way, but after power on it works like a charm.

2. As Untangle requires two NIC, I bought an additional NIC, but ESXi do not detect it.  My newly bought NIC has Broadcom BCM5782KFB P13 chip, which is on the compatibility list of ESXi.

Please help me for the solution.

Thanks in advance.

Dipesh

---

### Post by samosamo on 2009-08-10
Hey buddy. What does any of this have to do with Ubuntu Server Platforms?

---

