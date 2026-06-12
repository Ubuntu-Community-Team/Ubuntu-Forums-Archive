---
title: "Alternate Install Full Disk Encryption with SSD possible?"
date: 2012-04-09
forum: Security
---

### Post by wecali on 2012-04-09
Hi, 

from what I understand an SSD uses wear leveling to equally distribute the writing between all cells on the SSD. 
What I don't understand is how a full disk encryption affects this wear leveling, the complete disk is fully used and if some cell fail there might be not enough cells to replace them. I understand that the manufacturer has some additional, build in unused cells on the SSD for especially for that case. 

There are two questions that i have: 
Can I fully encrypt an SSD, thereby using every available cell (with backup cells in reserve) and it will last at least six years or so? 
Does the wear leveling also work by swapping already occupied cells (therefore currently in use) with one another?

many thanks in advance,
wecali

---

### Post by flurospar on 2012-04-09
You can encrypt a SSD fully, but don't expect it to run too long. Six years is very long. I'd say two years at the most (for a moderate user).

Why don't you get those external USB hard disks? They are quite portable, and IIRC they don't use SSDs.

---

### Post by wecali on 2012-04-09
Well, I thought I'd use an SSD for speeding up all the applications and their loading time (although i understand that full encryption decreases speed a bit). 

But from the information you gave me, i'd better think twice about buying an SSD for that purpose. 2 years is not an option as i wanted to install 12.04 LTS and use it for the full 5 years as a productive working system (and the ssd itself even longer). 

Many thanks for that crucial information! :)

---

### Post by tubbygweilo on 2012-04-09
wecali, a few thoughts on ssd + Ubuntu via [wiki.ubuntu.com]("https://wiki.ubuntu.com/MagicFab/SSDchecklist"), some of the information may be a bit old but a few queries on [launchpad]("https://bugs.launchpad.net/ubuntu?field.searchtext=ssd&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---

### Post by bodhi.zazen on 2012-04-09
> **tubbygweilo said:**
> wecali, a few thoughts on ssd + Ubuntu via [wiki.ubuntu.com]("https://wiki.ubuntu.com/MagicFab/SSDchecklist"), some of the information may be a bit old but a few queries on [launchpad]("https://bugs.launchpad.net/ubuntu?field.searchtext=ssd&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

Then update the information, it is a community wiki

---

### Post by darkod on 2012-04-09
Also, it's not a perfect solution, but to remind you that SSDs with 3yr warranty are very common. And if it fails after the 3yrs, they will probably be very cheap to replace by then.

Of course, you will always need to have updated backup if you expect it to fail, but you should have that in any case.

---

### Post by DZ* on 2012-04-15
SSD's controller is oblivious of encryption or even disk partitions, so it will happily move data around. However, the TRIM command will be disabled with the whole-disk encryption method. Since the kernel 3.1, TRIM with encryption is possible, but it is disabled by default: the LUKS website says the reason is that it enables knowledge where the encrypted data are.

---

