---
title: "NTFS Compression......?"
date: 2007-05-30
forum: Windows
---

### Post by adampyre on 2007-05-30
Hello,

I just installed Windows XP on another partition on my Ubuntu driven notebook so I could have Windows apps when needed for work. I am trying to make the footprint as small as possible, as it is only a 20 gig hard drive (old laptop) and I want as little space as possible devoted to XP, especially once I start installing bloatware I need for work (Office, etc.)

So, the first thing I did after installing XP was compress the hard drive hoping it would reduce the size somewhat. Before the compression, the windows partition had 1.73 GB of used space. After waiting 45 minutes for the compression process to complete, it now has 1.83 GB of used space. 
.
.
.
.
????????????????????????????????????????????

What did I do wrong? (Or am I stating the obvious?)

---

### Post by smoker on 2007-05-31
hi, i think compression works better on fat than ntfs file systems, but bear in mind for any windows system to operate with a modicum of decency, you need to have around 15-20% free space on the drive. you can turn off system restore, and reduce your page file size to save space, but you may be better installing something like windows 2000 for less bloat, and using open office (for windows), instead of ms office,

then again, depending on what apps you need for windows, maybe installing wine on ubuntu will be a better option.

best of luck

---

### Post by adampyre on 2007-05-31
I need Windows for some multimedia applications (I can't get Ubuntu to work with my TV OUT, tried using ATITVOUT and it almost works but the graphics are screwy) I also need it for office 2003, as I can't get it working in WINE and crossover costs $40.00 I don't have at the moment.

---

### Post by smoker on 2007-05-31
hi, don't know much about the apps you mention, i'm afraid, though another possibility is 'virtualbox' and installing xp as a virtual machine on top of linux. i believe virtualbox is in the repositories now, and if interested more info can be found here: [http://www.virtualbox.org/](http://www.virtualbox.org/)

best of luck

---

### Post by adampyre on 2007-05-31
Sounds like a good idea, but I only have 256 megs of memory on this machine. I would get more but I'd have to buy 2 sodimms and they are expensive for this Dell.

---

### Post by trippinnik on 2007-06-07
What do you need to do in Office 2003 that you can't do in OpenOffice?  As for the TV card, you could check with the MythTV community maybe someone has it working. Otherwise you might really be better off using just windows.  You really won't be able to do much with virtualization unless you have more memory.

---

### Post by trippinnik on 2007-06-07
for the SODIMM you can pick some up from crucial or [www.newegg.com](www.newegg.com).  You don't need the Dell supplied ones and they'll be a lot cheaper.

---

