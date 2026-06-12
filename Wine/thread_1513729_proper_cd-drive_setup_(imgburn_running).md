---
title: "proper cd-drive setup (imgburn running)"
date: 2010-06-19
forum: Wine
---

### Post by Metrop021 on 2010-06-19
I'm trying to run a disc burner program through wine (imgburn) since brasero won't do what i need. However i'm having trouble getting the program itself to see the drive. I'm guessing that i don't have the drive setup right in winecfg.

right now here's what my drive setup looks like, and my program isnt finding the drive.

[img]http://img692.imageshack.us/img692/5326/imgburnprob.png[/img]

any ideas would be appreciated

---

### Post by mc4man on 2010-06-19
go Tools -> settings -> I/O and use the first option under interface.  ASPI - WNASPI32.DLL

Your drive(s) should be found (no need to detect or set drive(s) in winecfg

Ex. from the default SPTI
> W 23:45:56 I/O Interface has been changed!
I 23:45:56 Shutting down SPTI...
I 23:45:56 Initialising ASPI...
I 23:45:56 Searching for SCSI / ATAPI devices...
I 23:45:56 -> Drive 1 - Info: ATAPI DVD A  DH20A4P 9P59
I 23:45:56 -> Drive 2 - Info: BENQ DVD DD DW1640 BSMB
I 23:45:56 Found 1 DVD±RW and 1 DVD±RW/RAM!


---

### Post by Metrop021 on 2010-06-20
yep that fixed it, thanks!

---

### Post by zackf on 2010-07-04
This fixed it for me too, thank you.

---

### Post by JoZ3 on 2010-09-12
WOW, tnx sir :D

---

### Post by brian_constante on 2010-09-26
I'm a bit of a newbee here in Ubuntu and this message caught my eye. I have installed in my HP Pavilion laptop DV4 1213LA ubuntu 10.4 and I have already installed img burn. I can't seem to find the following....
go Tools -> settings -> I/O and use the first option under interface. ASPI - WNASPI32.DLL
I noticed that this message was posted back in 2007...and i imagine that things have drastically change.
I am having the same problem with my img burn running under wine. The dvd burner is not being detected. Can you please send me specifics on how to correct the problem? Many thanks.

---

### Post by mc4man on 2010-09-27
I'm not sure how you're missing it, anyway,  see screens

---

### Post by cbilljones on 2010-09-27
Why not use K3B:confused: I recommend imgburn for window users and it is good; but you should never use wine when there are good alternatives availablel; and K3B isnt good - it's great.

---

### Post by mc4man on 2010-09-27
> Why not use K3B
k3b is ok, clearly the best linux iso creation/burning app (w/cdrskin. 
Still no comparison to imgburn.

---

