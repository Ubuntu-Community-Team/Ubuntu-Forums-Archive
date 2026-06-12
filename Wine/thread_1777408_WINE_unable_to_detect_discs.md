---
title: "WINE unable to detect discs"
date: 2011-06-07
forum: Wine
---

### Post by ronheidtmann on 2011-06-07
Please can someone help me!

I am struggling to install any form of software as WINE will not detect any CDs.  If I install software that only requires one disc, I will insert it, detects, installs, then when I want to run the software it tells me to insert the disc as the disc is not present, but the disc is in and did not eject it.

I tried to install software with 2 or more CDs, but it will install perfectly fine until it asks me for the second disk, I will load it in, click next and will not detect it.

I have tried to mount and unmount and nothing works, I have tried the latest and the previous versions of WINE and restarted my laptop many times.

Any idea what to do?

---

### Post by e79 on 2011-06-07
Here is what I would try to do :

1. Make and ISO image out of the cd/dvd you have.
2. Once created, mount that ISO image in a folder in, lets say, your Home directory (/home/user/isomount  for example).
3.  Once that ISO is mounted, open Wine Config, Drives tab and add a new Drive mapping, specifying the path to the ISO mounted in step 2.
4. Once the second disk is asked, simply give the path that leads to it (most probably the same path you mounted the first ISO I beleive, which means you would have to mount the 1rst ISO, then unmount it, then mount the second ISO and so on)

Tell us if that works

---

### Post by ronheidtmann on 2011-06-07
I will not be doing that.  All the software that I'm trying to install I have installed successfully and worked properly without a hitch on 10.10 with WINE, there's an issue with 11.04 to mount and unmount discs (I am not referring to inserting and ejecting discs).

---

### Post by ronheidtmann on 2011-06-08
Does anyone know what to do?

---

### Post by ronheidtmann on 2011-06-08
Does anyone know what to do?

---

### Post by e79 on 2011-06-09
You might want to look at [http://ubuntuforums.org/showthread.php?t=422582](http://ubuntuforums.org/showthread.php?t=422582), particularly this post by user **tk471**, but he had to mount the ISO as I suggested :

> hello, I just had to do this for a four CD game (Blade Runner), pretty  much as described above.  After inserting your first CD, and running  from terminal
```
wine /media/cdrom0/setup.exe
```After (in my case) choosing a full install, everytime the  installer wanted the next CD, I had opened a second terminal window, to  do this:
```

sudo umount -f /media/cdrom0 
eject /media/cdrom0
sudo mount -t iso9660 /dev/cdrom1 /media/cdrom0

```and then go back to the installer, continuing for each CD.  Your  device may vary, in my case the actual CD-ROM device is at  '/dev/cdrom1'.I would also try (adding a loop in your command)
```
mount -o loop -t iso9660 /dev/cdrom1 /media/cdrom0
```I'm sorry if I have no other solutions to offer than trying to mount the CDs, but It might work if you would give it a try, let's hope :D

---

