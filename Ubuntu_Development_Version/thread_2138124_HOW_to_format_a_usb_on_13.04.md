---
title: "HOW to format a usb on 13.04 ?"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by shantiq on 2013-04-23
i do not see that i can right click on a usb and get a format option anymore...   come to think of it it had disappeared on 12.04 too

where is it?

how does one format a usb these days?

---

### Post by The Spectre on 2013-04-23
> **shantiq said:**
> i do not see that i can right click on a usb and get a format option anymore...   come to think of it it had disappeared on 12.04 too

where is it?

how does one format a usb these days?

With the Disks utility or GParted if you have it installed.

---

### Post by slickymaster on 2013-04-23
You can always do it at a terminal.
```
sudo umount /dev/sdb
```where 'sdb' is the USB drive to be formatted.

Format to ext4:
```
sudo mkfs.ext4 -n 'Label' -I /dev/sdb
```where 'Label' is will be the name displayed for the USB

Format to FAT32:
```
sudo mkdosfs -F 32 'Label' -I /dev/sdb
```where 'Label' is will be the name displayed for the USB

---

### Post by shantiq on 2013-04-23
thanx



this is the one for me  >  [COLOR=#000000]Disks utility[/COLOR]


Accessories/Disks

---

### Post by Mathor on 2013-04-23
Not a very popular option, but I usually do all of my usb formatting within the application "Startup Disk Creator" aka usb-creator-gtk which is installed by default. Usually I end up putting an .iso on the drive using the same application, so it is a rather quick and speedy graphical way to achieve this.

---

### Post by shantiq on 2013-04-23
XLENT! Mathor never knew that was there

i usually use Unetbootin to make a live usb but this kills 2 birds with one stone

---

### Post by pcrussell502 on 2013-11-18
running 13.4 here...

went to software center and installed "disk"  it shows installed with a green check mark.  i can't find it anywhere on my 13.4 system despite the fact that the software center thinks it's installed.  

went to software center and installed "usb-creator-gtk".  it shows installed with a green check mark.  i can't find it anywhere on my 13.4 system despite the fact that the software center thinks it's installed.

when in search for it with application finder>all applications>and the first few letters of either of the installed programs above, NONE of them, or anything even remotely close shows up.

so apparently i have everything i need to format a thumb drive, except they are not visible in 13.4, and 13.4 does not know how to find them.  weird.

-peter

---

### Post by shantiq on 2013-11-18
run it in terminal maybe ```
  usb-creator-gtk
```

i too do not see it as a visible app  but it comes up from the terminal

---

### Post by philinux on 2013-11-18
Closed. This is 14.04 testing forum now. Please post new thread in main support forum.

---

