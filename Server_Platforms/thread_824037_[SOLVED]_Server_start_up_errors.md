---
title: "[SOLVED] Server start up errors"
date: 2008-06-09
forum: Server Platforms
---

### Post by batty on 2008-06-09
I am trying to get a home server up and running, I've installed Ubuntu server 8.04.

All i am getting on boot up is stream of error messages:

ata2.00 : exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00 : cmd a0/00:00:00:00:00/00:00:00:00:00/00 tag 0
ata2.00 : status : {DRDY ERR}
ata2,00 : revalidation failed (errno=-5)

this just scrolls up screen non-stop.
eventually I can log in but whilst I am typing the messages are still scrolling up screen.

My server box is a AMDx2 4000 CPU in a MSI K9NBPM2-FID motherboard (NVIDIA Quadro NVS 210s and NVIDIA nforce 430) with 2GB of ram.

I have tried two different IDE hard discs with no difference.

Help please

Dave

---

### Post by cdtech on 2008-06-09
You may need to change your sd's to hd's. In your fstab and your menu.lst

---

### Post by batty on 2008-06-10
I tried that no joy still the same.
The errors continually scroll down the screen, so when I open a text document in nano I still have to deal with the error messages scrolling down through the document I am trying to edit!

Any more ideas

Please!

---

### Post by quelx on 2008-06-10
[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/ata2-takes-looong-time-591276/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/ata2-takes-looong-time-591276/)

[http://ubuntuforums.org/showthread.php?t=472056](http://ubuntuforums.org/showthread.php?t=472056)

---

### Post by batty on 2008-06-10
I tried the nomsi suggestion no success
I have tried a couple of different hard drives same error.
I'll have to assume the MOBO chipset and linux just don't work nice with each other.

Any other suggestions?

Dave

---

### Post by batty on 2008-06-11
Well it appears that after all the messing about I've tried I got nowhere.
One last try after giving it some thought and reading links about dodgy hard drives I removed my CD drive (IDE channel 2, ATA2 ?).
Everything works fine now!!
So despite being able to install off the CD drive there is obviously something wrong with it, into the bin with it!

Many thanks 

Dave

---

### Post by molotov00 on 2008-06-11
Great find!

Can we get this marked as [SOLVED]? Someone else will find this useful. (Thread Tools menu, in red, at the top of your first post)

---

