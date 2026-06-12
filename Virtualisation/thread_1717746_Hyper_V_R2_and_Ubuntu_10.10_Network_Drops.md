---
title: "Hyper V R2 and Ubuntu 10.10 Network Drops"
date: 2011-03-30
forum: Virtualisation
---

### Post by audi4780 on 2011-03-30
Hi Everyone,

I have Ubuntu 10.10 running in Hyper V R2 with the synthetic network drivers loaded. I followed the steps on this article to update update-initramfs -u
[http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/](http://www.panterlo.com/2010/10/10/ubuntu-10-10-and-hyper-v-r2/)

I have OpenVPN setup to allow clients to access the other Hyper V guests remotely. It seems after a day or so, the networking crashes in Ubuntu 10.10. If I try to restart the network after it crashes via the "/etc/init.d/networking restart" it will not bring the adapter back up. I have tried reinstalling a clean Ubuntu 10.10 so far 3 times, and each time I would ultimately get this same issue.

Is there something else I need to do? Not sure if there is some sort of incompatibility with routing data through the OpenVPN tun adapter and the synthetic adapter.

I really do not want to use legacy adapters as throughput is significantly slower when routing between two adapters. 

Has anyone experienced this issue? Is there another version of Ubuntu/Linux that I should use instead?

Thanks!

---

### Post by CraigYork on 2011-05-15
I've got the same problem, I've also tried running 11.04 with the same issue. I'm struggling to find any info on this subject, anyone got an idea to try?

---

### Post by destr0y on 2011-10-09
Also confirming that this issue happens in 11.04.  Seems to be specific to the synthetic NIC in Hyper-V - the legacy one might be OK.  Previously, I'd gotten "around" this problem by installing WatchDog, and auto-rebooting if it couldn't ping our default gateway..  not a fix by any means.

edit #1 - nope, happens to the legacy NIC too.
edit #2 - Someone on the Fedora forums ([http://forums.fedoraforum.org/archive/index.php/t-254272.html](http://forums.fedoraforum.org/archive/index.php/t-254272.html)) suggested getting rid of the irqbalance package.  Obviously there are repercussions of this if your VM has more than one vCPU.
```
sudo aptitude purge irqbalance
```

---

