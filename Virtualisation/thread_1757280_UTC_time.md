---
title: "UTC time"
date: 2011-05-13
forum: Virtualisation
---

### Post by hanslammerts on 2011-05-13
Hi there,
 
Recently I succeeded in creating a KVM vm on my newly installed 10.04LTS machine. This vm is also running 10.04LTS. Everything seems to work nicely, but there´s one issue I can´t seem to solve.
Having read several posts about UTC time, my vm still shows me UTC time where I would like to have local time.
I have changed my timezone using tzselect, and also put my timezone in /etc/timezone. 
I also changed /etc/default/rcS to read UTC=no.
After this, I rebooted the vm, and also restarted all other kvm related processes on the host, but when I login again, the vm still shows me UTC time....
 
Anyone knows how I can get my vm to show local time instead of UTC ?
 
Thanks,
 
Hans
 
P.S. the host does display local time.......

---

### Post by hanslammerts on 2011-05-14
Never mind, I figured it out.
There is another file in /etc called localtime. This file was changed when I did a 
dpkg-reconfigure tzdata

---

