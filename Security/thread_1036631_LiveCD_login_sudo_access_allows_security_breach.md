---
title: "LiveCD login sudo access allows security breach ?"
date: 2009-01-11
forum: Security
---

### Post by yyoor on 2009-01-11
I have Ubuntu Intrepid installed in my desktop. While tweaking the /etc/fstab file for performance, I screwed up something and hence could not login to the Graphical Interface on reboot. I tried the Ubuntu LiveCD to access the system ( using the View Ubuntu without installing option) . I opened the terminal, entered the following command:

# sudo nano /media/disk-1/etc/fstab

Changed the file and saved. **System did not ask for a password anytime**. I checked the file permissions for this file and found only root has access to change it.

-rw-r--r--   1 root root       656 2009-01-10 23:35 fstab

To my surprise, I am able to access, modify or delete any file in the system through this LiveCD login (as user 'Ubuntu') without any access restriction !!!

Is this normal behaviour ? If yes, I find it as a security breach as one can access any system if armed with a LiveCD ???

Excuse me if this question is naive, I am a newbie to Ubuntu :confused:

---

### Post by cybergalvez on 2009-01-11
no computer is safe if you can actually get to the physical machine

> **yyoor said:**
> I have Ubuntu Intrepid installed in my desktop. While tweaking the /etc/fstab file for performance, I screwed up something and hence could not login to the Graphical Interface on reboot. I tried the Ubuntu LiveCD to access the system ( using the View Ubuntu without installing option) . I opened the terminal, entered the following command:

# sudo nano /media/disk-1/etc/fstab

Changed the file and saved. **System did not ask for a password anytime**. I checked the file permissions for this file and found only root has access to change it.

-rw-r--r--   1 root root       656 2009-01-10 23:35 fstab

To my surprise, I am able to access, modify or delete any file in the system through this LiveCD login (as user 'Ubuntu') without any access restriction !!!

Is this normal behaviour ? If yes, I find it as a security breach as one can access any system if armed with a LiveCD ???

Excuse me if this question is naive, I am a newbie to Ubuntu :confused:

---

### Post by hyper_ch on 2009-01-11
> **yyoor said:**
> Is this normal behaviour ?

> **yyoor said:**
> If yes, I find it as a security breach as one can access any system if armed with a LiveCD ???
You find it as a security breach... most people don't (including me)...

If you want to protect yourself against physical access, use encryption.

> **yyoor said:**
> Excuse me if this question is naive, I am a newbie to Ubuntu :confused:
Same applies for windows... by default anyone who has physical access can read all your data... it's nothing different here...

---

### Post by mpsii on 2009-01-11
Yes, this is normal behavior.

You have booted into the LiveCD and mounted the hard disk. Then using sudo (which provides root access) you have modified a file on the mounted system.

This is normal. You need root access to mount filesystems and perform other tasks, even in the live CD. As it was said before, you will need to take additional measures on your system if you are concerned that just anyone with a live CD can access/modify/copy/delete files on your harddrive.

---

### Post by tommynz1975 on 2009-01-16
In the spirit of 
*****Locks keep honest people out*****

you could change your bios not to allow the system to boot from media other than your hard-drive and password your bios so that it requires the password every time you boot.

Yes I know their are plenty of ways to reset the bios password but.. If it makes you sleep better at night **do it.**

---

