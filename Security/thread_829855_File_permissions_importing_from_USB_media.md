---
title: "File permissions importing from USB media"
date: 2008-06-15
forum: Security
---

### Post by azcn2503 on 2008-06-15
I am using Ubuntu 8.04LTS.

When importing from USB media such as a digital camera or a USB flash memory stick - the permissions for these files defaults to read-write access for the owner only, but for all other users it is set to none.

This is a real issue for me as my family will be using this PC as their 'media server' - importing photos from their digital cameras and viewing photos on their new HDTV in the living room. Unfortunately, MediaTomb does not serve the files unless the permissions for others is set to read-only.

How can I default Ubuntu so that when importing from USB media, it has the following permissions:

owner: read-write
group: read-only
others: read-only

At the moment, it defaults to:

owner: read-write
group: none
others: none

Please help!

---

### Post by amak79 on 2008-06-15
azcn2503,

There are a number of ways to accomplish this. The method you need depends upon how the USB drive is connected to the system. If you plug in the drive after you have logged in, then you can customise your mount options through GNOME. If the drive is "always" plugged in, then you can edit the fstab file to have it mount at boot.

**1. Mount after log in**

Plug in the USB drive and let Ubuntu mount it. Once the drive icon appears on the desktop, right click on it and select **Properties**. Click on the **Volume** tab. Then click on **Settings** to reveal the advanced mount options. Add the following to the **Mount Options** field: fmask=0133,dmask=0022,**uid**=1000,**gid**=1000

**Note:** Make sure to set the **uid** and **gid** values to the id's of the user that will be mounting the USB drive. You can find the id's my running: id **username**

Now you need to unmount the USB drive and remount it for the new mount options to take effect.

**2. Mount at boot**

Open /etc/fstab and add the following:

UUID=**uuid** /mnt/usbdrive vfat noatime,user,fmask=0133,dmask=0022,**uid**=1000,**gid**=1000 0 0

**Note 1:** Make sure to set the **uid** and **gid** values to the id's of the user that will own the mounted USB drive. You can find the id's my running: id **username**.

**Note 2:** You will need to replace **uuid** with the correct UUID of the USB drive. You can find the drives UUID by running: sudo vol_id **/dev/sdb1** | grep UUID . I used **/dev/sdb1** in the previous command as that is the USB device on my system.

**Note 3:** I have assumed that you are using a FAT (vfat) formatted USB drive.

Create the USB drive mount point:

$ sudo mkdir /mnt/usbdrive

Mount the drive:

$ sudo mount /mnt/usbdrive

---

### Post by kawouter on 2008-10-04
I had the same problem. I transfered photos from a cf card to my server and then other users couldn't read them (without manually changing the permissions). 

If you want to automount the media with read access to anyone do the following:

- Start gconf-editor
- go to system/storage/default_options/vfat
- do edit/umask/edit and change 077->022

Now the files have RW-R-R as rights and dirs have RWX-RX-RX

Wouter.

--------------------
[http://www.woubar.nl](http://www.woubar.nl)

---

