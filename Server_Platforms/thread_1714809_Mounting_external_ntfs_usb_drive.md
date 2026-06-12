---
title: "Mounting external ntfs usb drive"
date: 2011-03-25
forum: Server Platforms
---

### Post by Z.K. on 2011-03-25
I have been trying to use fstab, writing a script in /etc/init.d to mount my external ntfs usb drive.  I have had absolutely no luck and I have tried just about every solution I could find on the web except for writing a udev rule which I have never done so I am not exactly sure how.  

My solution for the interim is to put the mount command in the rc.local file.  That works, but I don't understand why I can use fstab to mount it.  

Putting it in the fstab gives me errors like "unknown file system" or just "An error occurred during mounting of drive" and then the booting stops. I tried using both ntfs and ntfs-3g.

Anyone have any ideas?

:confused:

---

### Post by Z.K. on 2011-03-25
> **Z.K. said:**
> I have been trying to use fstab, writing a script in /etc/init.d to mount my external ntfs usb drive.  I have had absolutely no luck and I have tried just about every solution I could find on the web except for writing a udev rule which I have never done so I am not exactly sure how.  

My solution for the interim is to put the mount command in the rc.local file.  That works, but I don't understand why I can use fstab to mount it.  

Putting it in the fstab gives me errors like "unknown file system" or just "An error occurred during mounting of drive" and then the booting stops. I tried using both ntfs and ntfs-3g.

Anyone have any ideas?

:confused:

Okay, I finally figured it out.  I used 

```

UUID=B288375288371477  /media/usb2  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

```

in fstab and now it mounts when booting.

---

### Post by Z.K. on 2011-03-25
Okay, so I have another problem.  How can I automount a hard drive it if is actually attached, but don't stop the boot process if it is not.  I may have to put this back in the rc.local.

:confused:

---

### Post by ashikaga on 2011-03-25
This isn't an fstab-based solution, but I find [autofs]("https://help.ubuntu.com/community/Autofs") pretty handy for situations like this. You just need to install the autofs package and create a couple of config files in /etc, and then /media/usb2 (for example, assuming you've configured it that way) will be mounted whenever you try to access it (if the USB drive is available.)

---

### Post by Z.K. on 2011-03-26
> **ashikaga said:**
> This isn't an fstab-based solution, but I find [autofs]("https://help.ubuntu.com/community/Autofs") pretty handy for situations like this. You just need to install the autofs package and create a couple of config files in /etc, and then /media/usb2 (for example, assuming you've configured it that way) will be mounted whenever you try to access it (if the USB drive is available.)

Thanks, I will look into it.

---

### Post by Z.K. on 2011-03-26
> **ashikaga said:**
> This isn't an fstab-based solution, but I find [autofs]("https://help.ubuntu.com/community/Autofs") pretty handy for situations like this. You just need to install the autofs package and create a couple of config files in /etc, and then /media/usb2 (for example, assuming you've configured it that way) will be mounted whenever you try to access it (if the USB drive is available.)

Thanks, this looks like what I want and I think I will give it a try.  I found this tutorial to be a great help.

[http://www.greenfly.org/tips/autofs.html]("http://www.greenfly.org/tips/autofs.html")

):P

---

