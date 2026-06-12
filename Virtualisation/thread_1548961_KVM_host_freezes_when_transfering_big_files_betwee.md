---
title: "KVM host freezes when transfering big files between guest and host"
date: 2010-08-09
forum: Virtualisation
---

### Post by PaLo on 2010-08-09
When I do a intensive use of the network (eg to copy a DVD image), the host and the guest becomes unavailable. Then I have to do a hard-reset. I´m usign virtio network device, also tested with e1000 and others but always the same.

Host info:

OS: Ubuntu 10.04 x86_64
CPU: AMD Athlon(tm) 64 X2 4600+
RAM: 3GB DDR2

Guest info:

OS: CentOS 5.5 x86_64
CPU: 1 vCPU
RAM: 1GB

any suggestions?

Thanks!

---

### Post by TheFu on 2010-08-11
I do not have an answer. Sorry.  If you look at the hostOS dmesg output, do you see anything strange?

I'm asking because VirtualBox appears to lock up a system due to large disk IO.  The issue has never happened when a VM was not running.  I have a e1000 NICs and use Intel PRO/1000 MT inside VMs. The host disks are directly attached and use mdadm for RAID5 software RAID.  The graphics completely lock up and drop out of X/Windows. Network access continues to work, but no local console does.  A hard power reboot is needed to get local consoles working.

Anyway, check the files in /var/log/* for hints on your issue.

---

