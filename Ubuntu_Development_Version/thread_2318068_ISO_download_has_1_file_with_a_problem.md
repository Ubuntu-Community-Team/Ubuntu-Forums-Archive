---
title: "ISO download has 1 file with a problem"
date: 2016-03-22
forum: Ubuntu Development Version
---

### Post by Aidoboy on 2016-03-22
I've download several copies of the daily from the 7th, checked them against each other and the site, written with win32 disk imager, but they always seem to turn up with 1 problematic file. Is this normal? Could I be doing something wrong?

Thank you so much for your help.

---

### Post by VMC on 2016-03-22
Do the md5sums match?

---

### Post by kansasnoob on 2016-03-22
Where are you still finding images from the 7th?

---

### Post by Aidoboy on 2016-03-22
> **VMC said:**
> Do the md5sums match?
Yes, they do.
```

    Source: 614951546d8411554a94a9c25155d65f
Download 1: 614951546D8411554A94A9C25155D65F
Download 2: 614951546D8411554A94A9C25155D65F


```

> **kansasnoob said:**
> Where are you still finding images from the 7th?

Here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by VMC on 2016-03-23
Maybe the problem is the [COLOR=#000000]win32 disk imager. Have you tried another iso2usb[/COLOR]  program, such as UNetbootin. Also what is the [COLOR=#000000]problematic file in question?[/COLOR]

---

### Post by sudodus on 2016-03-23
Win32 Disk Imager is cloning (similar to dd, gnome-disks, mkusb) and I doubt very much that it is causing the problem. It could be that the listed md5sum of that package is bad. What is the name of the offending package?

-o-

If you replace 'current' in the path with 'pending', you will get the 'latest and greatest' daily iso file. Try if that file is better. The 'current' version is the most recent version, that has passed some automatic tests. This is applied to standard Ubuntu, but several of the flavours (Lubuntu, ..., Xubuntu) do not apply such tests, and the 'current' daily iso file is the most recent version of the daily iso file.

You will see this if you 'go upstairs', select the parent directory, in the directory tree

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by sudodus on 2016-03-23
I checked this 'current' version from March 7 successfully: 'Check finished; no errors found'

I flashed the iso file into the pendrive with ***mkusb***. If your iso file is really correct, I don't understand what happened.

- What are you doing when 'they always seem to turn up with 1 problematic file'? And which file is bad (file name)? Please describe!

- Maybe, after all, there was a problem with ***Win32 Disk Imager***. Maybe you should try again, maybe with another USB drive, if some memory cell is bad. Maybe you unplugged the pendrive before everything was written from the buffers.

If still problems, try another tool to flash the iso file into the pendrive. ***Unetbootin*** has been suggested already. ***Rufus*** has also a good reputation. The official Ubuntu recommendation today is the [USB installer provided at pendrivelinux.com](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) (for installation from Windows).

---

### Post by Aidoboy on 2016-03-23
> **VMC said:**
> Maybe the problem is the [COLOR=#000000]win32 disk imager. Have you tried another iso2usb[/COLOR] program, such as UNetbootin. Also what is the [COLOR=#000000]problematic file in question?[/COLOR]
I'll give some more a try, I guess. I don't know how to check on the file, the only option is to reboot. [It looks like this, but stock Ubuntu instead of Mate.]("https://ubuntu-mate.community/uploads/default/original/2X/5/5a410a660e56d6ef934d5d0e666502f085fde5f1.jpg")

> **sudodus said:**
> I checked this 'current' version from March 7 successfully: 'Check finished; no errors found'

I flashed the iso file into the pendrive with ***mkusb***. If your iso file is really correct, I don't understand what happened.

- What are you doing when 'they always seem to turn up with 1 problematic file'? And which file is bad (file name)? Please describe!

I don't know how to check, the only option is to reboot. [It looks like this, but stock Ubuntu instead of Mate.]("https://ubuntu-mate.community/uploads/default/original/2X/5/5a410a660e56d6ef934d5d0e666502f085fde5f1.jpg")

> 
- Maybe, after all, there was a problem with ***Win32 Disk Imager***. Maybe you should try again, maybe with another USB drive, if some memory cell is bad. Maybe you unplugged the pendrive before everything was written from the buffers.

If still problems, try another tool to flash the iso file into the pendrive. ***Unetbootin*** has been suggested already. ***Rufus*** has also a good reputation. The official Ubuntu recommendation today is the [USB installer provided at pendrivelinux.com]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") (for installation from Windows). I tried pendrivelinux, but I realize now that that was with a corrupt download file. (That's why the second time I downloaded twice and checked against each other). I'll try pendrivelinux with a non-corrupt download.

---

