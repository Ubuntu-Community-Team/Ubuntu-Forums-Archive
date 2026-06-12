---
title: "Hardware RAID"
date: 2009-07-18
forum: Server Platforms
---

### Post by supanatral on 2009-07-18
When ever I run Ubuntu Server (in fact any distro of linux) and the computer has a hardware RAID'ed hard drive, it sees both hard drives as individual drives. Why is this?

---

### Post by Vegan on 2009-07-18
Does you RAID card have a BIOS to set the disks as striped (RAID 0) or anything?

Use it to configure the disks as you need.

---

### Post by supanatral on 2009-07-18
> **Vegan said:**
> Does you RAID card have a BIOS to set the disks as striped (RAID 0) or anything?

Use it to configure the disks as you need.

I guess I should have stated that better. This is RAID 1 so it's mirrored. It **should** only see one hard drive but it sees both as individual.

---

### Post by The Tronyx on 2009-07-18
> **supanatral said:**
> When ever I run Ubuntu Server (in fact any distro of linux) and the computer has a hardware RAID'ed hard drive, it sees both hard drives as individual drives. Why is this?

When you are using RAID, do you have it configured as RAID 1 or RAID 0 or...?  Additionally, what kind of RAID card are you using?

Have you confirmed that the RAID setup is actually functional?  In previous experience, with something like a RAID 1 setup, if the RAID implementation is working properly, you should not be seeing the second drive.

---

### Post by supanatral on 2009-07-18
The one that I care about and the main reason for this post is onboard. I have a seperate computer that has a PCI Express card for RAID 1 and after the long time it took to initially create the RAID, I booted into ubuntu server and it still saw both hard disks

---

### Post by windependence on 2009-07-18
If the "hardware" RAID is just software on a chip as we call it, then most Unices won't see the array even after you build it. If you see both disks, this is the case and you will need an add on controller if you want true hardware RAID.

-Tim

---

### Post by supanatral on 2009-07-18
The other computer I used had a RAID 1 PCIe card. How do I figure out whether they are true RAID, or just "software" RAID?

Is there a way to get Ubuntu Server "less picky" and just work with the controller?

---

### Post by windependence on 2009-07-19
See this how-to, but I would recommend just using an add on controller.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I like hardware RAID because it's simple, and some people here are going to try to convince you to use software RAID in the OS. Your choice, it's not bad and there isn't anything wrong with it, just more learning for you, AND you can't boot of the software raid partition, but it's probably good to separate your OS on another disk anyway.

-Tim

---

