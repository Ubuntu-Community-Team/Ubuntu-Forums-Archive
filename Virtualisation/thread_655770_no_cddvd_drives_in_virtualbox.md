---
title: "no cd/dvd drives in virtualbox"
date: 2008-01-01
forum: Virtualisation
---

### Post by rbprogrammer on 2008-01-01
well there is my problem, virtualbox will not recognize my two cd/dvd drives :confused: ..

they are [FONT="Courier New"]/dev/hdc[/FONT] and [FONT="Courier New"]/dev/hdd[/FONT] respectively.  before when i needed to use a disc, i had to create an image of the disc, save it to a local directory ( in a shared guest directory if i needed it after i installed windows ), then in virtualbox, use that image as the drive.  but as you can see in the screenshot, i only have [FONT="Courier New"]/dev/sdc1[/FONT].  don't know what partition on which drive that is.

i also saw somewhere ( regretfully i cant find where now ) to use this command:
```
export VBOX_CDROM='/dev/hdc:/dev/hdd'
```
but that did not work either, even after i rebooted.  i even tried multiple times..

as far as fstab is concerned, this is what i have:
```

...
/dev/hdd        /media/cdrom0  udf,iso9660  user,noauto,exec        0  0  
/dev/hdc        /media/cdrom1  udf,iso9660  user,noauto,exec        0  0 

```

how do i get at least one of the drives ( if not both ) recognized by virtualbox??

---

### Post by rbprogrammer on 2008-01-01
forgot the attachment :oops: ..

---

### Post by malibusurfer2 on 2008-01-03
I have a similar problem. I can't get VirtualBox CD/DVD-ROM to show a drive in the drop down box for a Windows XP virtual machine. I can click on Mount CD/DVD Drive and Host CD/DVD Drive, but the box is empty - no /dev/whatever. The Mount point under my CD drive Porperties, Volume is /media/cdrom0. Is there a line I need to add to my XP.xml file under .VirtualBox/Machines/XP?

---

### Post by rbprogrammer on 2008-01-14
bump :confused:

---

### Post by spur on 2008-01-14
Have you tried ensuring they are mounted in Ubuntu first? I have found that i need to do that to see them.(I'm not sure if that is normal or not)

---

### Post by rbprogrammer on 2008-01-14
what are the odds of that... with a few weeks of not getting this solved, i bump my thread, then just mere minutes i find this: [http://www.virtualbox.org/ticket/775](http://www.virtualbox.org/ticket/775)

apparently, it is a problem in VirtualBox v1.5.2 and how it accesses the device ids.  there are two fixes for it, one is a little *sloppy & jerry-rigged*.  the other is a bit more elegant.  i only tried the better solution at the bottom which was just to install [FONT="Courier New"]libhal-dev[/FONT].....

hope that helps you too malibusurfer2.

---

### Post by huanix on 2008-03-12
installing libhal-dev also did the magic for me!

---

