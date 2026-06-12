---
title: "VMWare server 2003 windows 8 gB Ram in host Ubuntu 11.4 Natty 32 bit"
date: 2012-04-18
forum: Virtualisation
---

### Post by NabX on 2012-04-18
I am using Windows Server 2003 in a VMWare in ahost Ubuntu 32 bit machine. with 4 GB RAM
  Now, i want to upgrade this memory to 8GB. Now my question is : will  this be recognized by the VMware version of Windows Server 2003, then i  will allocate 4 gb to W2k3 and the rest 4 will be used by the host?

---

### Post by CharlesA on 2012-04-19
Short answer: yes. Even Ubuntu 32-but uses PAE, which allows it to see more than 4GB of RAM.

---

### Post by dzponce11 on 2012-04-19
It should recognize the change of RAM, I use vmware player and it recognized that i added 2 more GB's of ram

~~~~dzponce11

---

