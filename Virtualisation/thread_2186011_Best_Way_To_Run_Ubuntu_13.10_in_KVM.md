---
title: "Best Way To Run Ubuntu 13.10 in KVM"
date: 2013-11-05
forum: Virtualisation
---

### Post by joyousjake on 2013-11-05
I tried it out, but it looks a bit messed up when I try it out. I gave The VM 3700 MB of RAM, and my host has about 4GB of RAM. The disk is 50 GB. The processor configuration is Opteron_G3.

Thanks in advance.

---

### Post by houstonbofh on 2013-11-06
Are you talking about Unity?  It requires a lot of memory and accelerated 3D graphics for good performance.  In a 2D graphics environment, it offloads the processing to the CPU, which is probably what you are seeing.

---

### Post by joyousjake on 2013-11-07
Yeah, is there any way to get Unity 2D?

---

### Post by TheFu on 2013-11-08
So ... you gave the guest 3.7G on a 4G system?  I would recommend against that. Always leave the hostOS with 1G of RAM and 1CPU if you have more than 2 cores.

Read [this]("http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization") and [this]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox").  The main ideas for the virtualbox article apply to KVM ... or any virtualization, just not the exact details.

No need for 50G of storage, just to try out Ubuntu. 10-15G is fine.  Here is my main desktop machine:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        14G   11G  1.9G  86% /

```  I've been using this since 2008. For a long time it was 10G.
BTW, I run it inside KVM in the way that the first link explains.

The main ideas are:
* Preallocate all storage. There are exceptions in the article for SSD, otherwise, preallocate.
* Use virtio drivers for Linux storage and network drivers
* Do not hog the hardware. allocate 1 vCPU and 1G of RAM to a guestOS unless you KNOW more is needed.
* Use virtual ICH chipsets when possible, not older models.
* Virtual hardware matters, forget any real hardware. The VM does NOT care.

---

### Post by joyousjake on 2013-11-09
Thanks. That will be something to try.

---

