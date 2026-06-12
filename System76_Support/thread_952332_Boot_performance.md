---
title: "Boot performance"
date: 2008-10-19
forum: System76 Support
---

### Post by Derath on 2008-10-19
I have a recently purchased Pangolin, and while booting it up, I noticed it takes a considerable amount of time to boot (relative to my other systems of course). After turning off bootsplash and watching it boot, I've found one of the slow downs here:

```

[   23.876963] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX01, max UDMA/100, ATAPI AN
[   53.832872] ata2.00: qc timeout (cmd 0xa1)
[   53.835752] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   53.838705] ata2.00: revalidation failed (errno=-5)
[   53.841566] ata2: failed to recover some devices, retrying in 5 secs
[   54.674794] ata2: port is slow to respond, please be patient (Status 0x80)
[   55.028325] ata2: COMRESET failed (errno=-16)
[   55.066856] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   55.116035] ata2.00: configured for UDMA/100
[   55.118873] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[   55.121673] ata2: irq_stat 0x40000008

```

I'm not sure if this is an error or not, but I have noticed that it takes a long time during these steps.

Also, How does the upgrade process to 8.10 look so far?

Thanks!
Jordan

---

### Post by thomasaaron on 2008-10-20
Just my opinion: If you don't like squashing bugs, don't upgrade to 8.10 until the official release. By then, we should be done with testing and have any bug fixes implemented in the driver.

Another opinion: If you want to minimize chances of completely hosing your system while upgrading, you might want to consider waiting about a week until the initial rush is over. Normally, Ubuntu's servers are very busy for the first week, and there are numerous complaints of hosed upgrades.

Not sure about the slow boot time. Will run some tests on it this week. It may have to do with the fact that the dvd driver is a SATA drive (which is relatively new-ish). There may be a bug there.

---

### Post by gpstar on 2008-10-20
it was doing the same on my bonobo, but in the bios, I changed the default OS settings from Windows Vista which it came set to, to the "Other Operating System" and it changed some things around and it no longer does the 

[   54.674794] ata2: port is slow to respond, please be patient (Status 0x80)

error message anymore, and it boots straight up quickly.

---

### Post by Derath on 2008-10-20
I'll give that a shot when I get home from work, thanks for the hint!

EDIT: Changed the BIOS setting, boot time has gone from about 2.5 minutes down to about 45 seconds, no lie. 

Thanks gpstar!
thomasaaron: Thanks for the info, also maybe the BIOS should be set on all laptop models for Other OS? I'm sure we can't be the only ones who noticed this, but then again most people probably don't like watching the text go by like I do. :)

---

### Post by Peneus on 2008-10-22
This is really nice.

Could you guys give a step by step description on how you did it for the newbies like me.
I have Daru2 by the way.

Thanks

---

### Post by thomasaaron on 2008-10-22
These instructions will not work on a DarU2, as it does not have the same setting option in the BIOS.

---

### Post by hvacr on 2008-10-22
This tells me that a driver may be missing. I have the new Pangolin and it boots very fast. This setting in the bios is for the AHCI driver for the hard drives. The Vista setting is much faster, xp does not have sata driver, were vista does. I would hope Ubuntu has sata drivers built in.

---

