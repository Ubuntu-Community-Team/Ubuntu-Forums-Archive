---
title: "please help ??"
date: 2010-06-21
forum: The Cafe
---

### Post by saakeman on 2010-06-21
I know that this is not about ububntu 
but, If any one can help 
I have a 4gb Kingston flashdrive 
but it only shows  250 mb ??

---

### Post by Paqman on 2010-06-21
Where are you getting the 250MB from? 

When you open the device and hit ctrl-h, do any hidden folders pop up? If they do, try shift-deleting them, they're just trash files.

---

### Post by saakeman on 2010-06-21
> **Paqman said:**
> Where are you getting the 250MB from? 

When you open the device and hit ctrl-h, do any hidden folders pop up? If they do, try shift-deleting them, they're just trash files.

ok it was a 4gb flash, it only say it has 250 mb 

when I try to format the flash it will only format to 250 mb space

I am formating from windows 
no hidden files / folders

and we putted google OS on it to test it and when we booted back into windows we formated and it only showed 250 mb

---

### Post by philinux on 2010-06-21
Moved to Café

---

### Post by sydbat on 2010-06-21
> **saakeman said:**
> ok it was a 4gb flash, it only say it has 250 mb 

when I try to format the flash it will only format to 250 mb space

I am formating from windows 
no hidden files / folders

and we putted google OS on it to test it and when we booted back into windows we formated and it only showed 250 mbI've had this happen. Someone I know who travels alot to places that end in "hina", thought they were being nice (and they were) and brought me a 8GB flash drive - at that time, 8GB was massive. Anyway, it turned out to be about 256MB in reality.

It turns out that many "knockoffs" for technology like this, use some program that makes the end user think there is more flash memory than is actually there. I do not remember what this is called (as it has been years).

---

### Post by doas777 on 2010-06-21
check to make sure there isn't another volume mounted as well. I've had a few thumbs that mount to two drives, one for the stupid apps integrated with the thumb, and one for my data.

---

### Post by Sporkman on 2010-06-21
> **sydbat said:**
> ...to places that end in "hina"

:lol:

---

### Post by NightwishFan on 2010-06-21
Use the Ubuntu disk utility and give it a new MBR partition table and fat32fs. If that does not work, I have no idea what will.

---

### Post by betrunkenaffe on 2010-06-21
Indeed, I caused this on my 2 GB stick once by making a bootable USB. The partition on it was 1GB and Windows could never delete the formatting and get it back to 2GB. Removing MBR on it should fix the problem.

You can also test by putting it in, going to terminal and running

sudo fdisk -l

and look at the output, if the usb device shows 1 partition and the main device could handle more. That's exactly what I had (except had also made a 2nd partition on mine for the other GB).

---

### Post by themusicalduck on 2010-06-21
I had this problem. I had to find the usb drive in GParted and go to Device, Create Partition Table. This will delete everything off the drive, but should allow you to format it to a larger size.

---

