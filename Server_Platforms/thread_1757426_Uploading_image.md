---
title: "Uploading image"
date: 2011-05-13
forum: Server Platforms
---

### Post by jaes84 on 2011-05-13
How would you go about making an image of a server, and then uploading that image to a backup computer, without using a second computer?

---

### Post by volkswagner on 2011-05-13
Clonezilla allows you to create a back up image to second hard drive, Network share, or USB device. 
You can even make an .iso for a bootable DVD if the image is small enough.

---

### Post by jaes84 on 2011-05-13
> **volkswagner said:**
> Clonezilla allows you to create a back up image to second hard drive, Network share, or USB device. 
You can even make an .iso for a bootable DVD if the image is small enough.
Can i do this without turning off the computer?

---

### Post by jaes84 on 2011-05-13
anyone?

---

### Post by volkswagner on 2011-05-13
Using [Clonezilla]("http://clonezilla.org/") would require you to boot/reboot the PC.  You can use the LiveCD version or Network boot it via a Clonezilla server.

If you want to make a backup without rebooting perhaps [tar can help]("http://ubuntuforums.org/showthread.php?t=35087").  Using tar may not give you an image to restore to blank disk... it may work by booting a live CD and applying the untar to disk.

Another option would be just use [dd]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/") to create an image file on a remote machine or mounted media such as USB device.  This may be your best option if you really don't want to reboot.  Just be very careful, dd stands for DataDump, but many dubbed it DataDestroyer... a simple mistake can erase your entire hard drive!

---

