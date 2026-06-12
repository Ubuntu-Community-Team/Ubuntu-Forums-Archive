---
title: "Trying to install ubuntu server 9.10 64 bit on VM Ware ESXi"
date: 2010-02-24
forum: Server Platforms
---

### Post by roycruse on 2010-02-24
Hi

Im trying to install ubuntu server 9.10 64 bit on VM Ware ESXi

unfortunately im not getting very far - as i get the following message :-

This kernel requires an x86-64 CPU, but has detected an i686 CPU. Unable to boot - Please use a kernal suitable for your CPU.

Where can i find a vmware ESXi compatible UBUNTU SERVER installer

---

### Post by kemra on 2010-02-24
Sounds as though your host has a 32bit processor so will only support quests who are also 32 bit OS's.

You need Ubuntu Server 32bit. Go [here]("http://www.ubuntu.com/getubuntu/download-server").

Click "Alternative Download Options" and then tick the "32-bit Version" radio dial and then "Begin Download".

---

### Post by _Morpheus_ on 2010-02-24
Hi,

I'm running Ubuntu 9.10 64 Bit just fine on ESXi 4 Update 1. Make sure that you install Update 1 of the ESXi hypervisor.

HTH

_Morpheus_

---

