---
title: "Failure to boot from hard drive"
date: 2007-02-27
forum: Windows
---

### Post by cameron_diaz on 2007-02-27
I'll try to summarize the events leading up to my problem as best I can.

I have two hard drives. I tried installing Windows Vista Business on the first one to use in a dual-boot configuration with Windows XP which was on the second hard drive. Well, the Vista installation worked fine, but when I went to boot into XP, I found Vista's boot loader hadn't recognized Windows XP. Clearly frustrated, I tried several different things until I finally decided to format the first hard drive. It was horrible I lost my entire data from the Hard drive. Vista made my data vanish. I hate it. I tried using repair tool and many recovery software, but it did not work. Please help me out.

---

### Post by renzokuken on 2007-02-27
you could try a livecd to recover any data from the drives.........

---

### Post by Coelocanth on 2007-02-27
If Vista actually wiped the drive with XP, there's not much you can do. However, if XP and your data are still on that second drive, you could try removing the first drive (or just unplug it from your mobo), which will leave only the XP drive. Then, boot up with your XP install CD (make sure the CD or DVD drive is the first boot option in your BIOS) and do a recovery (fix MBR). That should restore your MBR and allow you to boot into XP again. Then you can hook up your second drive again.

Hmmm, you may be able to do that without even unhooking the first drive, actually.

---

### Post by erlyrisa on 2007-02-27
Actually, just removing the New dirve that is supposedly Vista, should have you booting to XP once again (ie you shouldn'g have to fix the MBR with XP's recovery CD)


-Note, I haven't used a Vista install yet.... but I remember an option in a XP installation which when it asks about where you want to install, it also asks if you want o format the other drives that you may have on your computer..... if you did this and formatted your other drive too - then your stuffed.

-If the info is really needed and you did do a format ... with any luck you only did a quick format, inwhich case it may be possible to re-contruct the data on your drive. In this case mounting the drive under linux and veiwing it's contents, you maybe able to re-contruct some of the data that you need (note: not for the light hearted, there are specialist services which would be able to do this aswell). To check if you have info on the drive boot to a recovery console with one of your setup CD's and change to the drive that holds your data(c:). Type DIR , if it's empty then it's been formatted.

NOTE: next time bacup! - I have fallen for the 'press enter know' trap while doing installs aswell.

---

### Post by jordanstalon on 2007-02-28
[FONT="Century Gothic"]I know Vista doesn’t install itself easily. Something must have happened, that’s for sure. What software you have used to recover your data? One of the data recovery software I know is Salvage Data recovery Software for windows. My friend used the software and got his data back. Few days back I tried to recover the data of my office system, which I lost accidentally while formatting and it worked well. Try with their software. I think their site name is salvage data. 
All the best.[/FONT]

---

