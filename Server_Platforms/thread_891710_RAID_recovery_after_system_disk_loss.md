---
title: "RAID recovery after system disk loss?"
date: 2008-08-16
forum: Server Platforms
---

### Post by oddentity on 2008-08-16
Hi

I've recently resurrected an old PC with a single hard drive for use as a home LAN server, and put Ubuntu 8.04.1 LTS on it. I plan to get a further two hard drives and set them up in RAID mirrored mode to operate as a big NAS to share photos, music and all the usual stuff between my home PCs using Samba. I've seen plenty of guides on how to set this up from scratch, and how to recover if a RAID hard disk fails.

In my configuration though, the disk with the OS will not be part of the RAID array. But what I'm wondering is, what if the disk with the OS on it fails, or I upgrade the OS? Or in other words, can anyone please give me any tips on how to get a fresh OS install to resume a pair of mirrored hard drives that are in good condition and already have mirrored data on them? I've been looking at the mdadm assemble mode but I'm not 100% sure I won't mangle my data :confused: Is there any specific information I should backup to make this easier?

Thanks

---

### Post by fjgaude on 2008-08-16
If you are talking about software raid (**mdadm**) then if your OS drive fails or if you upgraded the OS all you do after you have installed the new OS is:

```
sudo mdadm --assemble --scan
```

Here's some text to read and study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Let us know how you are doing.

---

### Post by oddentity on 2008-08-17
Great, thankyou for helping :)

Yes I've been looking at mdadm, it looks ideal for my needs.

I'll be getting a pair of SATA drives and a PCI SATA controller this week (motherboard is an old ASUS nForce 1 IDE only board). I'll post back with my progress once I've got them working. At the moment I'm just trying to find a basic Linux compatible PCI SATA controller.

---

### Post by fjgaude on 2008-08-17
For speed make sure the controller you acquire is run off a PCI-Express bus, else the array throughput will be limited to about 115MB/sec because of the bus bottleneck.

Old motherboards are all PCI; the later ones mostly use the PCI-E bus.

---

