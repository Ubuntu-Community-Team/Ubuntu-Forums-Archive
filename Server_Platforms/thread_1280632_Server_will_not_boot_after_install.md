---
title: "Server will not boot after install"
date: 2009-10-02
forum: Server Platforms
---

### Post by gwmbox on 2009-10-02
Hi all

I am new to this so be kind :)

I am in the process of setting up a home fileserver and have the following in play.

Dist. downloaded : Ubuntu 9.04 Server (the latest version) 64-bit version

WinFast K8M890M2MA-RS2H onboard vid, lan, usb, 2 x SATA and audio
AMD Athlon 64 X2 Dual Core 3600+ CPU
1GB DDR2 533 Ram
1 PCI 4 port SATA Card
1 40GB SATA Samsung HDD (For the System)
4 x 1TB WD HDD, setup as RAID1 so 2 x 1GB Sets (For the file storage with RAID Mirror)

I have BIOS set to boot CD, then HDD.

Installed Server 9.04 ok and got to the remove media and reboot screen, I remove the CD, ENTER - system reboots and then I get the DISK BOOT FAILURE message...

I have tried everything I can think of but no matter what I do it is the same.  I even tried an IDE 40GB drive and removed the SATA 40GB drive, reinstalled the U9.04 server edition on it and get the same result.

Please help....

Thanks

---

### Post by undecim on 2009-10-02
Make sure the bios isn't trying to boot one of your 1TiB drives.

---

### Post by gwmbox on 2009-10-03
Yes tried that, even removed the 1TB drives (disconnected) to be sure.  I have now tried FreeNAS and that is fine and boots as it should, so it has to be a ubuntu server edition issue?

Thanks

---

### Post by cariboo on 2009-10-03
Where did you install grub?

---

### Post by gwmbox on 2009-10-03
:redface: grub? :redface:

I simply downloaded the Server edition and installed that - did not know I had to do anything else :redface: back to the documentation for me I thinks :redface:

---

### Post by DC^ on 2009-10-03
Make sure you have make the good choice of booting. Select in the bios, the harddisk where he needs to boot Ubuntu.
What I mean:
You can select what to boot first in de bios e.g:
1st Boot: CD/DVD
2st Boot: Hardisk 1
3st Boot: Removable device
4st Boot: Harddisk 2

You have select the harddisk as 1st boot where you installed Ubuntu.

Btw: The Server edition of Ubuntu doesn't have an graphical interface.

---

### Post by gwmbox on 2009-10-03
> **DC^ said:**
> Make sure you have make the good choice of booting. Select in the bios, the harddisk where he needs to boot Ubuntu.
What I mean:
You can select what to boot first in de bios e.g:
1st Boot: CD/DVD
2st Boot: Hardisk 1
3st Boot: Removable device
4st Boot: Harddisk 2


That is pretty much how I have it set, as said it boots fine for FreeNAS.  To setup Ubuntu Server it detects and installs on the correct HDD, but when I remove the media and reboot I get the boot failure.... very odd and puzzling.

> **DC^ said:**
> Btw: The Server edition of Ubuntu doesn't have an graphical interface.

Yes I am aware of that and I am happy to play with the commands and learn, however as yet I am unable to even boot up the server as above... 

If FreeNas was having the same issue I would say it is a hardware issue but the fact that the correct drive boots when I install FreeNAS makes me think it has to be Ubuntu - I just cannot figure out why.

My setup is the boot drive is using the onboard SATA1 port.  The 4 1TB drives are connected to the PCI 4 port SATA card SiI 3114 SATARAID 5.4.03.

Thanks

---

### Post by cariboo on 2009-10-03
Grub needs to be on the mbr of the first hard drive. Could you paste the output of:

```
cat /boot/grub/menu.lst
```

and

```
sudo fdisk -l
```

in your next post. Please surround the output with [noparse]```

```[/noparse] tags.

---

