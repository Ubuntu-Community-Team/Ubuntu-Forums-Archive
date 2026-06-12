---
title: "How to delete (and change?) Ubuntu and it's partitions to re-install Windows 8?"
date: 2014-05-03
forum: Windows
---

### Post by alexfitzelgard on 2014-05-03
Hi guys
I've installed Ubuntu but I don't like it so I want to go back to WIndows 8.
Problem is that I've heard WIndows 8 doesn't support linux partitions and we have to change/delete something.
Thanks in advance

---

### Post by nothingspecial on 2014-05-03
You can do this with the live cd/dvd/usb you used to install ubuntu. Boot it up, run an app called gparted that is included and format 1 or more partitions to ntfs then you can install windows in that space. It goes without saying, make sure you have a copy of anything you want to save and unplug it from the computer while you do this.

---

### Post by mekon2 on 2014-05-03
I'm sure the Windows 8 DVD/CD/USB will guide you through formatting the disk when you boot from it.

Out of curiosity how come you didn't like Ubuntu ?

---

### Post by alexfitzelgard on 2014-05-04
> **nothingspecial said:**
> You can do this with the live cd/dvd/usb you used to install ubuntu. Boot it up, run an app called gparted that is included and format 1 or more partitions to ntfs then you can install windows in that space. It goes without saying, make sure you have a copy of anything you want to save and unplug it from the computer while you do this.

actually I've tried that many times. do you think the cd has broken files?

---

### Post by alexfitzelgard on 2014-05-04
also when I format everything to NTFS no drives appear on the win 8 install

---

### Post by alexfitzelgard on 2014-05-04
> **mekon2 said:**
> I'm sure the Windows 8 DVD/CD/USB will guide you through formatting the disk when you boot from it.

Out of curiosity how come you didn't like Ubuntu ?
I was used to Win8 & stuff....

---

### Post by sandyd on 2014-05-04
Try
Device -> Create Partition Table
Select GPT

Note that this will create a new partition table.

---

### Post by Bucky Ball on 2014-05-04
*Thread moved to **Other OS/Distro Support**.*

---

### Post by alexfitzelgard on 2014-05-15
anyone?

---

### Post by alexfitzelgard on 2014-06-06
...wow

---

### Post by alexfitzelgard on 2014-06-06
none of these work.. drive isn't appearing on install disk help please :(

---

### Post by buzzingrobot on 2014-06-07
A better bet for advice on installing Windows would be a Windows forum or site.  If the Ubuntu partitions have been deleted, and a new partition table created, there's nothing left of it. 

 If the machine has been reset (if necessary) to Secure Boot,  UEFI, etc., and if the Win8 install DVD in use is a full install DVD and not one of those "recovery" disks, then I'd expect the install to proceed as an ordinary new Windows install on bare metal.

I don't know if the Win8 installer still offers a choice between an "update" and a "new" installation. If it does, I'd pick "new".

---

