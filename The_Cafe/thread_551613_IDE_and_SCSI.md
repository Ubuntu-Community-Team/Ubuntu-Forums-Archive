---
title: "IDE and SCSI"
date: 2007-09-15
forum: The Cafe
---

### Post by drndrw on 2007-09-15
Hey guys. I know that most computers use IDE drives and most servers use SCSI drives, but is there really any noticeable difference? The real reason why I'm asking is because I'm thinking about turning my Xubuntu machine into a web or game server, and it currently has a 80 gb IDE in it. But if there's a difference, I might go over to ebay and pick up a cheap server for $200. What do you think? Thanks.

---

### Post by logos34 on 2007-09-15
why not a sata raid array (cheaper per gb than sci)?

---

### Post by drndrw on 2007-09-15
I'm not sure what that means. Is that cheaper and better than IDE?

---

### Post by bogolisk on 2007-09-15
> **drndrw said:**
> Hey guys. I know that most computers use IDE drives and most servers use SCSI drives, but is there really any noticeable difference? The real reason why I'm asking is because I'm thinking about turning my Xubuntu machine into a web or game server, and it currently has a 80 gb IDE in it. But if there's a difference, I might go over to ebay and pick up a cheap server for $200. What do you think? Thanks.

Use SATA. IDE price, SCSI performance.

---

### Post by drndrw on 2007-09-15
Well what is SATA? Is it cheap? Do I need a special plugin thing or will IDE work? I think I might have a SATA drive in my computer though...

---

### Post by blueturtl on 2007-09-15
IDE stands for Integrated Drive Electronics and basically means just that: the controller for the hard-disk is included on the disk. IDE disks at least initially were cheaper to produce, and although the performance was worse than what professionals used it was sufficient for home use. 

IDE drives today mostly mean SATA. SATA and PATA are types of connections used for the hard-disk. All old drives are PATA (or Parallel ATA) drives whereas the new drives are SATA (or Serial ATA). SATA has the advantage in transfer rates as well as wiring (the SATA cables are much smaller and more convenient to use).

SCSI stands for Small Computer System Interface. Hard-disks that are labeled SCSI require a separate hard-disk controller interface card placed into the system so they can be plugged in and used (unless one is integrated into the motherboard). You can use as many SCSI hard-disks in a system as your interface card allows for you to connect. The use of a separate (and often expensive) controller interface meant that SCSI drives had lower CPU utilization as well as other benefits over their IDE counterparts. Also because SCSI was labeled a more professional technology the hard-disks themselves were often produced with better specs; lower seek latency, higher spindle speed etc.

The benefits of SCSI might go to waste if you do not perform very disk intensive tasks (sound & video editing, heavy i/o server etc). Therefore most systems use IDE.

p.s. I read about this subject years ago so please forgive me for any factual errors.

---

### Post by poe503 on 2007-09-15
SCSI prices have really dropped in the past year.  I bought a new U160, 68pin, 36gb disk drive for $25 on eBay.  The thing with SCSI is you have to do your homework to set up the system correctly.  It is possible to make all sorts of mistakes and purchase the wrong equipment as SCSI has been around for a long time and there are variations in design.

---

### Post by Crashmaxx on 2007-09-15
Just stick with IDE, get SATA if you want new drives and have it built in to your motherboard. I wouldn't think you would be doing anything that would need SCSI, and newer IDE drives are very good performers anyway. I would expect that you would max out a lot of other things (namely bandwidth) before you need to worry about IDE being an issue.

---

### Post by forrestcupp on 2007-09-15
I was under the impression that the newer high RPM IDE drives were about as fast as SCSI.  I really thought that SCSI drives were kind of outdated.

---

### Post by drndrw on 2007-09-15
Well I thought SCSI and SATA's had different connections than IDE's did.

---

### Post by blueturtl on 2007-09-16
SCSI does have a different type of connection than IDE.
IDE drives come with two different types of connectors, SATA or PATA.

IDE and SCSI are two different things altogether but SATA is a type of IDE drive.

---

### Post by Sp4cedOut on 2007-09-16
Most of the newer motherboards are coming with SATA slots.  If yours doesn't have them, just go with IDE.

---

### Post by drndrw on 2007-09-16
Is it possible to add a SATA slot to an older mother board? Say, a Pentium III?

---

### Post by logos34 on 2007-09-16
if the board has pci slots then you can add a sata host cotroller card

---

### Post by nonewmsgs on 2007-09-16
if you want to get real technical IDE is actually a pretty meaningless term
the correct one is ATA
now there is serial ata and parellel ata ie sata or pata.  people often call pata ide, but that's not as correct.

---

### Post by drndrw on 2007-09-17
So then what is PATA? I also thought it was IDE.

---

### Post by sr20ve on 2007-09-17
removed

---

