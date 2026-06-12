---
title: "Ubuntu Server + Hardware Raid"
date: 2006-10-17
forum: Server Platforms
---

### Post by cvprados on 2006-10-17
Hello,

 I'm trying to install an ubuntu server over an HP Server with an Intel RAID controller SATA. In the Bios I activate the RAID settings, I create the RAID as mirror raid, but when I start to install UBUNTU justs sees the 2 harddrives as sda and sba, it does not see any raid device so when I install in sda nothing is copied to sdb, any ideas.

 After the Bios there is a RAID setup from the manufacturer (HP) where I build the raid.

Thanks

---

### Post by hkgonra on 2006-10-17
My understanding of this is that if Ubuntu sees 2 hd's then you do not have harware Raid, you have software Raid, Hardware raid has it's own processor and memory and ubuntu would just see the raid card and the number of " drives " that the raid card created.

---

### Post by cvprados on 2006-10-17
That's what I thought, but the Card controller looks like HW Raid:

0000:00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family)
Serial ATA Storage Controllers cc=RAID (rev 01)

---

### Post by hkgonra on 2006-10-17
That is a controller on the motherboard, the regular system processor does the raid calc so it is software raid.

---

### Post by cvprados on 2006-10-17
thanks

---

### Post by thunderlight1 on 2006-10-24
I had almost the same problem with my HighPoint RocketRAID 454 4-channel ATA RAID 5 Host adapter until I installed the draid package. Now it works.

Hope this helps.

BR,
//Cesar

---

### Post by hkgonra on 2006-10-24
> **thunderlight1 said:**
> I had almost the same problem with my HighPoint RocketRAID 454 4-channel ATA RAID 5 Host adapter until I installed the draid package. Now it works.

Hope this helps.

BR,
//Cesar


What is the draid package ?

---

### Post by Aberrix on 2006-10-24
dont even bother with dmraid, its so screwed up.

Use the alternate-install CD, I had my RAID up and running within minutes.

---

### Post by tdhardwick on 2007-05-27
mdadm is a good package for software raid

---

