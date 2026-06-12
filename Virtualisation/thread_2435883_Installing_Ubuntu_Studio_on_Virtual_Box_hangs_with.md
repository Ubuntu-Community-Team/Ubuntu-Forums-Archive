---
title: "Installing Ubuntu Studio on Virtual Box hangs with more than 1 cpu"
date: 2020-01-27
forum: Virtualisation
---

### Post by chrisrodgers on 2020-01-27
I am running Virtual Box 6.1 on Win 10 Pro with AMD FX 8320 8 core and 16GB RAM.  If I try to install or run Ubuntu Studio 19.10 with more than 1 cpu, it hangs and fails to install or boot.

I can successfully install and run the following (in the same VirtualBox 6.1):
Kubuntu 19.10 4cpu 4GB
Xubuntu 19.10 2cpu 2GB
Lubuntu 19.10 2cpu 2GB
Ubuntu Desktop 19.10 4cpu 8GB

I tried Ubuntu Studio as 4cpu 8GB, but hung.  I saw a thread from last year where someone mentioned having an issue with Ubuntu Studio > 1cpu, so I dropped to 1cpu 8GB and it installed successfully.  I successfully added VB Guest Additions. I reconfigred to 4cp 8GB but it would not boot up (hung).  I reconfigured to 2cpu 8GB and still hung.  I reconfigured to 1cpu 8GB and it booted successfully.

Since Ubuntu and other official flavors do not seem to have this issue, it makes me thing it is a difference between Ubuntu Studio and Ubuntu (maybe the kernel or something?).  Any pointers for me?  

I wanted to get back to using Ubuntu Studio (used to use 16.04 and 18.04), but if I can't use more than 1cpu, would I be better off installing tools into Ubuntu or another flavor with multiple cpus?

---

### Post by deadflowr on 2020-01-27
Ubuntu Studio ships with the low-latency kernel versus the generic kernel that all other Ubuntu flavors ship.
Not that that is the issue, but it is something that is different between them.

---

