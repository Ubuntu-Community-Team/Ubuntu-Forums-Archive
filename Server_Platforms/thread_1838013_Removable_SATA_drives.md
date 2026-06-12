---
title: "Removable SATA drives"
date: 2011-09-02
forum: Server Platforms
---

### Post by srich on 2011-09-02
I have a SATA drive caddy that allows me to insert any SATA drive (like a CD or USB).  However, Ubuntu does not detect it and I have been unsuccessful Googling for a remedy.  The only way I have found to get Ubuntu to recognize the drive is reboot the server.  You can probably guess what kind of inconvenience that puts on my users each time I insert a new drive.

Any ideas?

---

### Post by arrrghhh on 2011-09-02
This article will have stuff that doesn't directly pertain to the Server Edition, but see the "manually mounting" section...

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by srich on 2011-09-04
Unfortunately, it is not a USB drive.  It is a SATA drive and does not show up when issuing the command fdisk -l.  The only way I have been able to get it to show in fdisk is by rebooting the server.  Same thing on workstation.
I need to know if there is a command or some application I can download that will rescan for new SATA drives and make them available to mount/dismount.

Thanx.

---

### Post by arrrghhh on 2011-09-04
> **srich said:**
> Unfortunately, it is not a USB drive.  It is a SATA drive and does not show up when issuing the command fdisk -l.  The only way I have been able to get it to show in fdisk is by rebooting the server.  Same thing on workstation.
I need to know if there is a command or some application I can download that will rescan for new SATA drives and make them available to mount/dismount.

Thanx.

If they don't show up in fdisk, I'm honestly not sure what you can do.

---

### Post by Vegan on 2011-09-04
You need to use a hot plug controller to be able to do that.

The low cost USB docks work fine with Windows but they need to be remounted all the time with Linux which is a minor nuisance.

---

### Post by Rob_H on 2011-09-04
I bought a low-cost SATA external drive docking station a few weeks ago and hot mounting/unmounting works perfectly under Kubuntu. (Can't speak for Ubuntu, but I guess it would be the same.) Here's a link if you're interested:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153071)

---

