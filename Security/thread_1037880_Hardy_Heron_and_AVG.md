---
title: "Hardy Heron and AVG"
date: 2009-01-12
forum: Security
---

### Post by ucalagon on 2009-01-12
Hi RealWorld - I'm completely new to ubuntu 8.04. It's running on side D: of a Windoze Vasti machine but installed as "Inside Windows".  I've got AVG for linux installed within ubuntu as a "Belt and Braces" effort along with gufw 0.20.7.
When I try and update AVG, I get "You do not have permission to run avgupdate.exe" but it did update itself on first install
I've trawled around the Authorizations options without success.

1. I realise that linux is unlikely to attract viruses but the Authorization system is something I obviously need to understand.
2. I'd initially hoped to install ubuntu "completely independent of Windows" on Side D: but kept getting a format error message; side D; was ntfs but I couldn't reformat from within the install.

Is it better to restart, reformat in FAT32 and install again, please? 
How can I change the Authorization to allow AVG updates?

All help gratefully received - David, Norfolk UK

---

### Post by Tubes6al4v on 2009-01-12
It seems from your post that you installed Ubuntu using Wubi (i.e. it runs from your windows partition). Is this correct?

Anti-virus is really not needed for Linux. Take a look at some Ubuntu Security Threads on here and other sites. [Here]("http://ubuntuforums.org/showthread.php?t=510812") is the one posted as a sticky in the Security forum.

---

### Post by ucalagon on 2009-01-12
Yep, installed with wubi.  Couldn't get any other install command to run from CD.  Maybe because of ntfs format??  Thanks for quick response

---

### Post by hyper_ch on 2009-01-12
well, simplest way to do a real install would be

(0) defag your windows partition

(1) shrink the windows partition (on vista use its own partitioning tool)

(2) leave the "freed" space empty... don't even create a partition for it

(3) select then the install option form the menu when you boot from the cd

(4) upon the partitioning screen select then to use the largest FREE space --> if you are unsure, aks here! Because accidental wrong partitioning could delete all your files!

---

### Post by ucalagon on 2009-01-14
Thanks to hype & tubes.  Real hope is that I'll have a HDD with "freestanding" ubuntu to take on travels and access via USB HDD reader. I have another sound problem; no sound with video on websites bbc news vids etc but I'll poke it on correct forum!
David

---

