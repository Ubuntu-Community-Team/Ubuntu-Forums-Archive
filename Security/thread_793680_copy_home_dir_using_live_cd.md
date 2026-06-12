---
title: "copy home dir using live cd ?"
date: 2008-05-14
forum: Security
---

### Post by 0range0rca on 2008-05-14
Hi, 

I want to copy my home directory into another hdd. I booted up using the ubuntu live cd, but it says i dont have permission to read the home on the hdd that i want to copy. How do i do this ?

thanks

PS- I can login and do it, but i want to do it using a live cd
I am using ubuntu 7.10

---

### Post by mattress on 2008-05-14
This is what I would do:

1. boot live cd and sudo / su to a root shell. (sudo -i)
2. mount both partitions from a terminal window (mount /dev/hdx /mnt/oldhome etc.)
3. run cp -Rpa /mnt/oldhome/myuser /mnt/newhome/myuser
4. verify files are on new partition
5. update fstab entries for /home

That should do it...

HTH

m

---

### Post by sunstriker on 2008-05-14
just put sudo before your copy command. should do the trick.
Like:

```
sudo cp -Rv /media/disk1/home/yourusername/* /media/yourdestinationdrive/yourdestinationfolder/
```

---

### Post by fisheater on 2009-10-19
Hi all,

I have installed a package that has made my computer unbootable ([http://ubuntuforums.org/showthread.php?t=1295486](http://ubuntuforums.org/showthread.php?t=1295486)).

My files are stuck in my ubuntu 9.04 partition and I need to get them out. This threat is good, but I dont know what hard drive is called (sda1,2,3 or hda1,2,3.).

I will be using a LiveCD 9.04 to get this done. I tried to see the files in Nautilus and copy them, but dont have permission to do it. 

Thanks for the (timely) help!

FE

---

### Post by The Cog on 2009-10-19
The command **sudo -i** gets you a command prompt with full privilege - just hit return at the password prompt. Then **fdisk -l** (lower-case L) will list all the hard drives and their partitions. 

If you are mounting the partitions by hand, you will need to create the directories you are mounting them to (called the mount point) first. For example:
> mkdir /media/myhome
mount /dev/sda1 /media/myhome

---

### Post by fisheater on 2009-10-19
Thanks, got it. I managed to get my files off, but only 2 denied me permission. They were on the desktop and I was unable to get them.

Thanks for your help. Please close.

---

