---
title: "Ubuntu's what Linux was MEANT to be!"
date: 2006-01-15
forum: The Cafe
---

### Post by pbr on 2006-01-15
Hi!  I'm Paul... I've been working with UNIX and LInux for over 20 years.

I'm REALLY impressed with Ubuntu.  It's best feature - it just plain WORKS.

There are still a few rough edges - things that people often need to do that require signifigant Linux admin experience - but a LOT of the pain has been eliminated.  GREAT JOB!

2 tasks which will still trip up your average user are:
- adding swap files 
- adding hard drives

Both of these have procedures that are complex enough to be daunting to the average user.  Consider that under (ugh!) Windows, new drives are recognized and made available without users needing to edit files like /etc/fstab.  Also consider that the virtual memory management on Windows is pretty much "automatic".  While that might not be a valid goal for Linux, it sure would be nice to be able to say "use N gigabytes of this drive for swap" rather than having to (1)dd (2)mkswap (3)edit /etc/fstab (4)swapon or reboot 

Beyond those complexities, Ubuntu's pretty much a "pain free linux" - Congratulations!

-Paul

---

### Post by BoyOfDestiny on 2006-01-15
[QUOTE=pbr]Hi!  I'm Paul... I've been working with UNIX and LInux for over 20 years.

I'm REALLY impressed with Ubuntu.  It's best feature - it just plain WORKS.

There are still a few rough edges - things that people often need to do that require signifigant Linux admin experience - but a LOT of the pain has been eliminated.  GREAT JOB!

2 tasks which will still trip up your average user are:
- adding swap files 
- adding hard drives

Both of these have procedures that are complex enough to be daunting to the average user.  Consider that under (ugh!) Windows, new drives are recognized and made available without users needing to edit files like /etc/fstab.  Also consider that the virtual memory management on Windows is pretty much "automatic".  While that might not be a valid goal for Linux, it sure would be nice to be able to say "use N gigabytes of this drive for swap" rather than having to (1)dd (2)mkswap (3)edit /etc/fstab (4)swapon or reboot 

Beyond those complexities, Ubuntu's pretty much a "pain free linux" - Congratulations!

-Paul[/QUOTE]

Hmm during the install, a swap partition is made automatically I believe (I've been doing it manually once I learned how, since I like / and /home on different partitions...)

As for hard drive mounting... before I played with fstab, you can go to System -> Administration -> Disks.  It allows mounting via the gui (although I don't think it permanently modifies the fstab info). 

As for partitioning, gparted is a good tool.

---

### Post by BSDFreak on 2006-01-15
[quote=BoyOfDestiny]Hmm during the install, a swap partition is made automatically I believe (I've been doing it manually once I learned how, since I like / and /home on different partitions...)[/QUOTE]

He's talking about adding more swap space, you can do that by increasing the size of your swap partition via gparted which is relatively painless and you won't have to change anything else. You can also do that by adding files using dd, mkswap and swapon. The third way is to create yet another swap partition.

> As for hard drive mounting... before I played with fstab, you can go to System -> Administration -> Disks.  It allows mounting via the gui (although I don't think it permanently modifies the fstab info). 

As for partitioning, gparted is a good tool.

I don't know if fstab-sync is installed by default in Ubuntu but with it there is no need to change the fstab after you have added new storage.

---

### Post by Franko30 on 2006-01-15
[QUOTE=BoyOfDestiny]As for hard drive mounting... before I played with fstab, you can go to System -> Administration -> Disks.  It allows mounting via the gui (although I don't think it permanently modifies the fstab info).[/QUOTE]

Yes, here we should have **an option "do this automatically at startup"** or s.th. like it.

[QUOTE=BoyOfDestiny]As for partitioning, gparted is a good tool.[/QUOTE]

Yes, for people knowing what 'partitioning' is. :-)

What pbr meant was that people new to Ubuntu need to be able do do the stuff he mentioned without browsing HowTos and forum posts first.

I would have been glad to have such an option described above when I started using Ubuntu about a year ago (which for me was: starting using Linux).

Fortunately I have a lot of spare time and I love **reading** (HowTos, forums, wikis etc.).

My wife, on the other hand, is **not** such a 'text based' person. She likes the visual stuff (buttons to click etc.) and listening to explanations. Which is why I have to explain her Ubuntu and Linux stuff by actually telling her.

Maybe we should start an **"Ubuntu Basics HowTo" podcast**. This would be great - having a **link on the desktop after the first startup** and then learning important basics and Ubuntu Linux stuff on the go with your MP3 player. :D 

Cheers

Franko30

---

### Post by tom-ubuntu on 2006-01-15
I absolutely agree with adding harddrives.

But do average users know what swap is? For what it is used? And do they care to in-/decrease it? Once it is setup, and the installer can do that automatically for you, is it not ok for them?

---

### Post by DaMasta on 2006-01-15
The average user does not buy hard drives either. Imo, of course.

---

### Post by Inarius03 on 2006-01-15
I agree with what you said about it being pain-free and what Linux should be. I've been a heavy, above-average Windows user for years now (back to 3.1 days). I tried SuSE and it was alright, but still kind've hard to get some things going the way I wanted them, and I could never get the wireless card in my laptop working. Wanted to try Gentoo, but I spent 3 days trying to get it installed with no luck whatsoever. Then I came along Ubuntu, and WOW... very much impressed. The ease of use, ease of customization, ease of editing files, etc. is above and beyond what I had hoped for from Linux, hearing of how techy you had to be to successfully run it daily if you were very much used to Windows.

I kind've want to try Debian now and see what it's like, but as of now, I am 100% completely satisfied with my Ubuntu 5.10 system and I can't wait to see what it can really do in the future!

---

### Post by DaMasta on 2006-01-15
[QUOTE=Inarius03]Rowlett, TX[/QUOTE]
Really? Which part. I used to live right off of Rowlett road, but now I'm in Dallas.

---

### Post by Inarius03 on 2006-01-15
[QUOTE=DaMasta]Really? Which part. I used to live right off of Rowlett road, but now I'm in Dallas.[/QUOTE]

Near RHS. ;)

---

### Post by DaMasta on 2006-01-15
[QUOTE=Inarius03]Near RHS. ;)[/QUOTE]
Small world.

---

### Post by mstlyevil on 2006-01-15
[QUOTE=DaMasta]Really? Which part. I used to live right off of Rowlett road, but now I'm in Dallas.[/QUOTE]

I live in the best part of Texas. I live 141 miles north of the Texas-Oklahoma state line. ;)   J/K

---

### Post by Bandit on 2006-01-15
Ubuntu is one the best Linux distro's out.
IF anyone thinks Ubuntu is hard then they havent spent 5 minutes using it yet.
For example 3 minutes ago I got a notification that there were 4 files to upgrade. I clicked the update notification icon. Looked at what needed update. 30 seconds later I was done. Everything installed quickly and painlessly and no need to reboot...
Try that on windows...
If I am feeling lazy and need a program like NVU, I can just check the repositors. It downloads and installs so much quicker then windows does.. Less user intervention click ing the freaking NEXT NEXT NEXT OK NEXT on windows... OMG... I hate windows...
Cheers,
Bandit

---

### Post by poofyhairguy on 2006-01-16
I'm glad you like Ubuntu original poster.

I'm also glad that your wishes for Ubuntu are actually possible. No pie in the sky ("I want to run all my old Windows games perfectly") for you. Glad to see that, makes for a happy user.

---

### Post by egon spengler on 2006-01-16
[QUOTE=Franko30]
[QUOTE=BoyOfDestiny]As for partitioning, gparted is a good tool.[/QUOTE]


Yes, for people knowing what 'partitioning' is. :-)

What pbr meant was that people new to Ubuntu need to be able do do the stuff he mentioned without browsing HowTos and forum posts first.[/QUOTE]

I really do not know, do people that don't know about partitioning often feel the urge to increase their swap space?

---

