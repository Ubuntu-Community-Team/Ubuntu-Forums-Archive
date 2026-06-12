---
title: "kvm guest / virtual interfaces do not consistently come up"
date: 2009-05-18
forum: Virtualisation
---

### Post by jacknc on 2009-05-18
I'm running 9.04 as the host and the guest. 

eth0 will come up automatically, but eth0:1, eth0:2, etc. will not. Running
```
sudo service networking restart
```causes them to all come up. I've tried combinations of two different hosts and multiple guests. Sometimes they do come up, but I am unable to get any guest to always come up on any host, or any host have all guests work. Certain combinations of host/guest work more often than others.

My guess is some sort of timing issue during the boot cycle, but I've been unable to go any further. Nothing interesting in dmesg or syslog.

Does anyone have any insight they can share? 

Jack

---

### Post by jacknc on 2009-05-19
I was able to work around this issue by adding multiple network interfaces to the VM and using eth0, eth1, eth2, etc. instead of virtual interfaces. Never did figure out why the virtual interfaces wouldn't work.

Jack

---

