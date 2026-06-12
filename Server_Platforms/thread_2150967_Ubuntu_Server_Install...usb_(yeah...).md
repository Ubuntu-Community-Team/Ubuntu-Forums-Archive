---
title: "Ubuntu Server Install...usb (yeah...)"
date: 2013-06-02
forum: Server Platforms
---

### Post by Ravenshade on 2013-06-02
12.04 and a long back log of threads to sift through. >.>; Well, I've sifted as best I could and tried various 'solutions'. Such as disconnecting the cd drive, trying to use a dvd (failed)...amongst various others. 

Simple things first then. 

I have a computer (quite an old one, still has a floppy), it also has USB ports. So I fired up my Unetbootin (because I'm on Fedora not Ubuntu). I install Ubuntu 12.04 LTS server to my usb-stick. 

I take the usb stick and insert it into the rear end of my computer (with some gusto as this is 90th time). 

I load up the install screen, select Ubuntu Server from the Unetbootin screen. ...dum de dum de dum

!! Load Installer Components from CD....

Now, I've disabled to the CD-RW/DVD-ROM drive in the BIOS, I've also pulled out the power cable. So...there's no CD/DVD drive (I get the same problem anyway or it doesn't recognise the LiveCD as a legitimate Ubuntu disk...(go-figure)). I've tried to delete the /cdrom directory, but it's busy, meaning I can't mount /dev/sdb1 there (another solution which has turned out to be fruitless). 

Anyone have a suggestion? I'm willing to try anything...that doesn't involve spending money. >.>

also tried: [http://arnieyuan.wordpress.com/2011/01/23/install-ubuntu-with-usb-failed-to-load-installer-components-from-cd-solved/](http://arnieyuan.wordpress.com/2011/01/23/install-ubuntu-with-usb-failed-to-load-installer-components-from-cd-solved/)
But...didn't work, didn't detect the iso.

---

### Post by sandyd on 2013-06-02
Is the USB Drive formated as FAT32?

---

### Post by Ravenshade on 2013-06-02
According to gparted, File System is fat32...according to gnome it's ms-dos, I'm assuming one and the same >.> It also has plenty of space left (used 2.2 out of 7.3 gb). Flags boot, lba.

---

### Post by cariboo on 2013-06-03
I suggest you check the MD5 checksum on your iso, as it looks like you may have a corrupted download. I've used a usb thumb drive to install the 12.04 server on my Intel atom powered auxiliary media server, and didn't run into the same problem as you. I have previously seen the same error message, and found that it usually comes from a corrupted iso.

---

### Post by Ravenshade on 2013-06-03
Tried redownloading, it verified successfully. Same problem. So I'm going to try this a different way. 

Install Ubuntu 12.04 Desktop. What do I need to apt-get uninstall to bring it back down to terminal level? I don't need anything heavy like gnome running.

My Solution: [http://www.darrinhodges.com/converting-ubuntu-12-04-lts-desktop-to-server/](http://www.darrinhodges.com/converting-ubuntu-12-04-lts-desktop-to-server/)

---

### Post by Cheesemill on 2013-06-04
I've only ever had this issue when creating the USB using UNetBootin. Try using dd to create your USB instead, for example...
```
sudo dd bs=4MB if=ubuntu-12.04.2-server-amd64.iso of=/dev/sdx && sync
```
where /dev/sdx is the identifier for your USB drive.

If you are still having problems then you could use the mini iso to install ffrom instead...
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

---

