---
title: "Stupid VM and its stupid ethernet driver"
date: 2008-12-17
forum: Virtualisation
---

### Post by ant2ne on 2008-12-17
I'm installing a second XP VM. The first one runs just fine. The second one doesn't know what drivers to use for its ethernet interface. Which is kind of funny seeing as how it is a virtual device. How do I download drivers for a virtual device?

---

### Post by bodhi.zazen on 2008-12-17
I suggest you revise your posting style. Stupid this and stupid that do not exactly motivate people to help.

Also can you give any more details ? I do not understand why networking is working with install #1 and not #2.

Are you using bridged or NAT ?

---

### Post by ant2ne on 2008-12-20
> **bodhi.zazen said:**
> I do not understand why networking is working with install #1 and not #2. Are you using bridged or NAT ? I don't understand either. I installed VM 1 a few months ago. And don't recall any problems. 

> **bodhi.zazen said:**
> Stupid this and stupid that do not exactly motivate people to help.VM 1 works, VM 2 is stupid.

---

### Post by thomasr on 2008-12-20
A little more info would help. Re you running VirtualBox? VMware Server? VMWare Workstation? And what version.

---

### Post by ant2ne on 2008-12-21
oh yeah sorry... 

vmware-server version 1.0.5 build 80187

---

### Post by thomasr on 2008-12-25
Try removing the network card in VM Properties and then add one again.

---

### Post by dcstar on 2008-12-25
> **thomasr said:**
> Try removing the network card in VM Properties and then add one again.

Or installing VMWare tools which installs the Windows network driver.......

---

### Post by ant2ne on 2008-12-27
> **dcstar said:**
> Or installing VMWare tools which installs the Windows network driver.......did both of those. =(  I even removed and re-installed vmware tools.

---

