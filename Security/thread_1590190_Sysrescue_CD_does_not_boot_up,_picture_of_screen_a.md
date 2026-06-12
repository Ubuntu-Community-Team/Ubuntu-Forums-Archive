---
title: "Sysrescue CD does not boot up, picture of screen attached"
date: 2010-10-07
forum: Security
---

### Post by newboyo on 2010-10-07
Hi all,
 
I use a thinkpad T410 (core i5, with 4 GB of RAM) and Karmic 64 bit.
 
Mondo doesn't work (Module Loop not found error), so I thought I'd try Partimage from Sysrescue to backup my win partitions. 
 
On inserting the sysrescue disk, it works fine until setting up {I think} net root, after which it goes crazy (pls see attached pic of screen) and I need to power it off and boot normally. I thought it might be linked to DMA, so I tried booting sysrescue after turinng off DMA in the bios, but no luck. 
 
 
Need help on getting sysrescue working, please help!
 
Rgds,
 
New
 
 
p.s The same sysrescue disc works WELL in a 4 year old centrino with 2 Gb of RAM. Go figure!!!

---

### Post by Rubi1200 on 2010-10-07
If you are looking for a backup solution why not try Clonezilla?
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by newboyo on 2010-10-07
I guess I'll have to do that, but more importantly the things that bother me are -
- is there a harware issue
- why can't I get sysrecue to work

---

### Post by Rubi1200 on 2010-10-07
Does this also happen with, for example, an Ubuntu LiveCD?

---

### Post by newboyo on 2010-10-07
LiveCd works just fine!

---

### Post by cariboo on 2010-10-07
+1 for clonezilla, I use it extensively for backing up Windows partitions, especially failing hard drives. I've never had a failure yet.

---

### Post by newboyo on 2010-10-07
> **cariboo907 said:**
> +1 for clonezilla, I use it extensively for backing up Windows partitions, especially failing hard drives. I've never had a failure yet.

Is there anyway of verifying a clonezilla backup (like in Mondo)?

---

### Post by ghane on 2010-10-09
> **newboyo said:**
> Hi all,
 
On inserting the sysrescue disk, it works fine until setting up {I think} net root, after which it goes crazy (pls see attached pic of screen) and I need to power it off and boot normally. I thought it might be linked to DMA, so I tried booting sysrescue after turinng off DMA in the bios, but no luck. 
 

Can you try:

[LIST=1]
[*]sysrescuecd 1.6.1, just to see if there is a change
[*]Try acpi=off on the kernel load line
[/LIST]

What version of sysrescuecd?

--
Sanjeev

---

### Post by newboyo on 2010-10-09
> **ghane said:**
> Can you try:

[LIST=1]
[*]sysrescuecd 1.6.1, just to see if there is a change
[*]Try acpi=off on the kernel load line
[/LIST]

What version of sysrescuecd?

--
Sanjeev


thanks vm. acpi=off works with 1.6.1!!!

Relieved to know that there aren't any hardware issues.

---

