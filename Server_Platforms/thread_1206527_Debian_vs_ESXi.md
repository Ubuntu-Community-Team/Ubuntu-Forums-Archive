---
title: "Debian vs ESXi"
date: 2009-07-07
forum: Server Platforms
---

### Post by SuperMiguel on 2009-07-07
Im running FreeBSD now on my server, it is acting as a file/webserver... I currently studying for few ms certs and i need to install w2k3 to run AD and exchange server. 

Option 1: Should i install debian, then install vmware server/virtualbox and on top of that install win2k3 and freebsd.
Option 2: Install ESXi, then install debian, freebsd, win2k3, and win xp (to manage esxi).

System Especs:
Athlon 6000+ 3.1 Ghz
8gb of ram
4tb of HD
BIOSTAR TFORCE TA790GX 128M AM3/AM2+/AM2 AMD 790GX HDMI ATX AMD Motherboard

This a home server, and will be use for home file sharing, school work, and study purposes :)

---

### Post by guilly on 2009-07-07
option1.

Less headaches if you ask me. Especially if this is just for personal use.

---

### Post by scorp123 on 2009-07-07
> **SuperMiguel said:**
>  Option 2: Install ESXi Are you even sure ESXi works on your hardware?? ESX and ESXi are very very selective when it comes to hardware support ... in other words: they suck at hardware compatibility.

If you want an Enterprise-level virtualisation solution ... why not look at XenServer 5.5? It can be downloaded for free as well.

But VirtualBox definitely is easier to use.

---

### Post by SuperMiguel on 2009-07-07
> **scorp123 said:**
> Are you even sure ESXi works on your hardware?? ESX and ESXi are very very selective when it comes to hardware support ... in other words: they suck at hardware compatibility.

If you want an Enterprise-level virtualisation solution ... why not look at XenServer 5.5? It can be downloaded for free as well.

But VirtualBox definitely is easier to use.

im not sure if it is, is not listed on the HCL :(

---

