---
title: "On NFS Drive With Local Boot"
date: 2010-09-14
forum: Server Platforms
---

### Post by jakerote on 2010-09-14
I have succesfly got the network running but i was wondering if i could get my laptop to boot wirelessly. Your help would be appriciated
 
tia

---

### Post by arrrghhh on 2010-09-14
Are you trying to PxE boot your laptop wirelessly or do you just want an NFS mount setup wirelessly?

The latter is possible, just modify /etc/fstab and put the NFS mount in there.

---

### Post by jakerote on 2010-09-16
yeah pxe boot my laptop wirelessly

---

### Post by arrrghhh on 2010-09-16
> **jakerote said:**
> yeah pxe boot my laptop wirelessly

I don't think this is possible.... How would it work?  PxE booting only works wireline, unless I'm missing something I've never seen a laptop with configuration settings in the BIOS to PxE boot from the wifi card!

---

### Post by Vegan on 2010-09-16
I have serviced a lot of portables and I have found none that can support the wireless boot, likely due to the limitations.

I use a Live CD to service machines that are unbootable as its safe to use and see if the disk is toast without harm.

The CD is immune to malware too making it ideal for such scenarios.

So for NFS boot, the only way is to use a fixed cable or simply install the OS on the local disk and then use it that way.

---

### Post by FuturePilot on 2010-09-16
It's not possible to PXE boot wirelessly.

---

