---
title: "Boot from an HDD where is installed Ubuntu Server 14.04"
date: 2019-09-04
forum: Server Platforms
---

### Post by tirengarfio2 on 2019-09-04
Hi there, 

I have in my hands an 1.5 TB HDD that supposedly stores a clone of an remote VPS with Ubuntu Server installed. 

I have connected the HDD to the motherboard, and it looks the HDD is detected correctly. 

[IMG]https://i.stack.imgur.com/Sd8FE.png[/IMG]

When I try to boot my PC just connecting this 1.5 TB HDD, it says something like "No bootable device found".

To know if the HDD is bootable or not, I searched on Google and found this:

[https://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr](https://superuser.com/questions/329467/how-to-see-if-usb-stick-has-mbr)

So I have run:

file -s /dev/sda

and I get:

/dev/sda: x86 boot sector

---

### Post by slickymaster on 2019-09-04
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2019-09-04
Which partition are you trying to boot from? If sdb1 has the OS you want and boot in somewhere on sdb, then you can either swap the SATA cables inside the machine or change the boot order in the BIOS.  This assumes that sdb has the OS that used to boot on this machine.

Assuming you can access the file system below the RAID, perhaps below LVM, then you'll want to treat it like a backup and restore the relevant files to a new install as needed.  I don't know your skill level and I cannot provide steps for this, since I wouldn't have gotten the "backup" or mirror in that method.

a) please post text, not images. Copy/paste the commands AND relevant output, then wrap it in *code tags* so it looks the same here as it does in a terminal.  Adv editor  (#) 

b) We can't just slap any virtual machine image into any other computer and expect that to boot.  It doesn't work that way. Besides needing the BIOS to be setup the same way, the disk controllers need to be recognized and the boot files need to be in the correct, expected, location.

c) Appears this "image" was made by connecting it to an existing RAID setup, allowing it to sync/mirror, then they broke the RAID and shipped you the disk.  Which sort of RAID was used?  Was LVM used or did they use some non-standard file system?

---

### Post by SeijiSensei on 2019-09-05
Are there particular applications in this image that you need?  If not, I'd just install a fresh copy of [Ubuntu Server 18.04LTS]("http://cdimage.ubuntu.com/ubuntu-server/bionic/daily/current/") and move along.  Also you can probably find the most recent versions of any applications in that image in the repositories.

---

