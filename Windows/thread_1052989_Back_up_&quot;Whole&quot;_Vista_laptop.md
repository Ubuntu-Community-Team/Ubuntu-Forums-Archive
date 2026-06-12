---
title: "Back up &quot;Whole&quot; Vista laptop?"
date: 2009-01-28
forum: Windows
---

### Post by 67GTA on 2009-01-28
I have finally gone through the daunting task of tweaking Vista on my HP laptop so that it does what I want it to. It is now like a well trained puppy:D When I get the energy, I will do this on my desktop. I just bought a 1TB USB external hard drive for backups. What are my options for backing up everything such as drivers, apps, tweaks, updates, etc, so I can return to this moment in time if I ever have to reinstall? Windows restore does not always fix every problem. I have looked at disk imaging software, but I'm not sure how easy/hard they are to use. Are there any other options?

---

### Post by Bender the Robot on 2009-01-28
Acronis True Image, is the one I used.  It's easy to use and, almost, foolproof. - [http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

---

### Post by slick666 on 2009-01-28
The best way to back up **everything** is to image the machine. If you have a desktop I recomend using G4L (Ghost for Linux). It's a live cd that creates a direct image (DD) of the entire hard drive and transfers it over the network to another machine via FTP. It's a great way to config a system and save it as an image but if you want to do some partial restores it will be a little more work than plopping a cd in.

[http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

---

### Post by 67GTA on 2009-01-28
Does the imaging method require the target partition to be the exact same size as the backup?

---

### Post by binbash on 2009-01-31
+1 for acronis

---

### Post by Bender the Robot on 2009-01-31
> **67GTA said:**
> Does the imaging method require the target partition to be the exact same size as the backup?

Not with Acronis. The important thing is that the backup partition/drive is large enough to take the image -  i.e. if the image is 5Gb then the backup partition/drive needs to be larger than 5Gb.

---

### Post by Lazy-buntu on 2009-02-01
You could run GParted live CD or I guess any live CD with GParted on it, create a partition on your external hard drive, then copy your windows partition there. Then, you could shrink the partition to the used size (i.e. 32GB out of 100GB used, shrink to 35GB).

I messed around with Norton Ghost, Clonezilla, and some other things, but this worked fine for me. Actually I did this for someone else's laptop. Used Norton Ghost to completely clone the C: drive, then when the laptop crashed and burned I booted up GParted Live-formatted their computer-and copied the cloned version of the partition over to the laptop. The laptop booted up like a freshly installed version of XP, but with all the settings/files there :p

There's probably a more efficient way, but that was the easiest way for me.

---

### Post by shadoweva00 on 2009-02-01
Ultimate edition, and I think business edition can make backup images from the backup and restore program. You should check into that.

---

### Post by delta_one_ on 2009-02-01
I would recommend clonezilla (clonezilla.org). It is an open source live CD and it only copies used space so it does not require a the target partition to be the same size of the backup. It compresses the image, so it actually requires less space on the target than the size of the partition you are backing up.

---

### Post by pmicheal on 2009-02-06
I recommend you to use [Drive Clone Pro]("http://www.farstone.com/software/driveclone-pro.htm") Very user friendly interface.

[Linux Archive]("http://www.linux-archive.org/")

---

