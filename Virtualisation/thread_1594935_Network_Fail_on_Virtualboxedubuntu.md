---
title: "Network Fail on Virtualbox/edubuntu"
date: 2010-10-12
forum: Virtualisation
---

### Post by cfhowlett on 2010-10-12
I've updated to latest VBox 3.2.10-66523 and installed u/k/x/netbook ubuntu in dedicated virtual machines.  Then installed guest additions and enabled fullscreen in all - EXCEPT edubuntu.  For some reason, edubuntu won't find the auto eth0 network via the virtualbox NAT.  Anyone else experience/fix this issue?

---

### Post by cfhowlett on 2010-10-15
Reinstalled twice and both times, I had a network connection via my host machine's wifi during the live session.  However, once I booted into the virtual machine's HDD installation, NO NETWORK was present.  

I reinstalled 10.04 and updated to 10.10 from there.  No idea why the network didn't net get detected and configured during installation.

---

### Post by tushargkwd on 2010-10-17
Try changing the network adapter type in the Oracle Virtualbox and see if it helps you.

---

