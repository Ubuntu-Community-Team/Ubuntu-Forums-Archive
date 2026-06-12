---
title: "Server 8.04.1 Install"
date: 2008-09-28
forum: Server Platforms
---

### Post by dividenot on 2008-09-28
Having trouble installing Ubunter Server edition.

I'm running a blade server with no cd, and no disk drive.  But I can boot from usb.

Downloaded ubuntu-8.04.1-server-i386.iso and tried to run it from my 1g usb but only got as far as the detect cd rom device driver step.  I realize the iso was made for a cd but tried the usb anyway.

I just downlowded Wubi but saw that there was no option to install the Ubuntu Server edition and am now installing Kubuntu KDE4.

Was wondering if there was an option for someone with my hardware limitations to install the Ubuntu Server edition?

---

### Post by daemon_cleaner on 2008-09-28
You have got all you need to mount your *.iso as /cdrom:
* Kubuntu - Working Linux environment (we used a local Ubuntu installation)
* Established internet connection
* 1GB or larger USB flash drive
[...]
22. Reboot your computer and set your system BIOS boot priority to boot from the USB stick.
You should be able to boot Ubuntu 8.04.1 from the memory stick and by default it should save your changes, restoring them on subsequent boots.
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

---

### Post by daemon_cleaner on 2008-09-28
p.s.:
It works for me only when I follow the Notes:
"If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)"
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/")
You have to wget ubuntu-server.iso instead of wget releases.ubuntu.com/releases/8.04/ubuntu-8.04.1-desktop-i386.iso and you will need a second usb-drive for the installation: The first one (temporary, fake cd-rom-drive) to boot ubuntu-server.iso from and second one to install your server to.

---

### Post by dje on 2008-09-28
i used [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable usb stick for my eeepc. it is fast and very easy, i suggest you take a look at it

---

### Post by dividenot on 2008-09-28
I've looked at that website before.  Plus I already have a version of linux(DSL) installed onto my usb.

From what I understand the purpose of that article is to install Ubuntu onto the usb only.

My goal, sorry maybe I didn't make this clear in the original post, is to install Ubuntu server edition from the usb onto my pc which is now running Win xp and soon Kubuntu(hopefully that will help).



I'm a bit of a newbie to linux so excuse me if I'm overlooking anything.

---

### Post by lykwydchykyn on 2008-09-28
At work I use PXE to install Debian and Ubuntu onto machines without CD drives.  It works stellar.  Does your machine have the capability to boot via PXE?  If so, do you have a second machine there you can set up as a PXE boot server?

I've always had trouble with USB booting, personally.  It ought to be doable, but it's very hit and miss in my experience.

---

### Post by dje on 2008-09-28
> **dividenot said:**
> I've looked at that website before.  Plus I already have a version of linux(DSL) installed onto my usb.

From what I understand the purpose of that article is to install Ubuntu onto the usb only.

My goal, sorry maybe I didn't make this clear in the original post, is to install Ubuntu server edition from the usb onto my pc which is now running Win xp and soon Kubuntu(hopefully that will help).



I'm a bit of a newbie to linux so excuse me if I'm overlooking anything.

unetbootin allows you to create a bootable usb stick of the ubuntu iso meaning you can boot from the usb and install ubuntu from that usb as though you were installing from the cd, but you are using the usb stick instead ;)

---

### Post by daemon_cleaner on 2008-09-28
This tutorial shows you how to drop your server-edition onto the usb-drive. Than you should be able to boot it and use it like a CD Installer. You can install Ubuntu-Server trough lan (PXE), from a local system using unetbootin or from a usb-drive wherever you need to. Notice: DSL-Linux is a "Working Linux environment", so you don't need a running Kubuntu first and the second thing is: Ubuntu-server-edition has no desktop environment by default.

---

### Post by dividenot on 2008-10-01
Thanks alot guys for the help.

Actually my current situation is much like my previous situation.  I'm just a bit more clear about what the real problem is.

I've used unetbootin to install ubunter server 8 to my usb drive and can now succefully boot from my usb.  That's actually something I achieved with previous attemps.

The real problem now is that, after booting from the usb, I'm having trouble at the step where it asks to find and mount my cdrom drive (where I have none).  I tried loading quite a few of the device files including a few with a name like /dev/usbdev1.1_cu00.  I know that all the files necessary to install ubuntu are on my usb and I'd really just like to skip the cdrom detection step.  It's a critical step I realize and I am not sure how to get around it.

---

### Post by daemon_cleaner on 2008-10-01
> **dividenot said:**
> I'm having trouble at the step where it asks to find and mount my cdrom drive (where I have none) (...) and I'd really just like to skip the cdrom detection step.
> **Mounting the USB stick as /cdrom**

 *This step is only needed for the Alternate install CD and Ubuntu 6.10 or older.* 
Switch to the second virtual console during the first couple of dialogs (when asked about your preferred language for the installation etc.) by pressing the ""ALT-2"". Do the following: 

[LIST]
[*]mkdir /cdrom /dev/cdroms
[*]cd /dev/cdroms
[*]ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
[*]mount -t vfat /dev/cdroms/cdrom0 /cdrom
[/LIST]
Then switch back to the first virtual console by pressing ""ALT-1"". Continue installing Ubuntu as if you were running from CD.
*This was a bit tricky until I got the hang of it. You need to have the hardware detection detect your hda before you can mount it! But just wait until it complains about a missing CD-ROM, then *don't* try to helpfully tell it where to look. Just accept the dialog where it says that this stage failed, *then* switch over to the virtual console and mount -t vfat /dev/hda3 /cdrom. (I skipped the gyrations with /dev/cdroms, they don't seem to be necessary.) Back in the installer, you should now be able to proceed from the next point in the dialog.*
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

What is about the the pendrivelinux-solution?
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

Take a look here as well:
[http://ph.ubuntuforums.com/showpost.php?p=5496792&postcount=3](http://ph.ubuntuforums.com/showpost.php?p=5496792&postcount=3)
[http://ubuntuforums.org/showpost.php?p=4896210&postcount=42](http://ubuntuforums.org/showpost.php?p=4896210&postcount=42)

---

### Post by dividenot on 2008-10-01
I've gotten through the cd detection stage.  Now I'm stuck on the "load installation components from cd" stage.

I found that my usb is detected as /sdb1, /sda1,3,5, and 7 are my hard drive partitions.

---

### Post by dividenot on 2008-10-02
Install from USB update;

I have read alot of tutorials and forum posts.  Tried alot of stuff.  But still only partial success.

I attatched the log files from the installation if anyone knows what to look for.  I added the ".doc" file extention but can upload them with a different one if needed.

To recap on the problem; I get along pretty well booting from my usb and have passed the cdrom detection stage.  The load installation components from cd stage is the one that fails.

I've tried to install other versions of Ubuntu but no success with any of them.  

I'm running a Chinese version of Windows XP and am located in China (which, I believe, has been part of my problem trying the netboot).  I don't suppose any of the operations I perform on my windows effects the linux files, do they?

---

### Post by daemon_cleaner on 2008-10-05
> **dividenot said:**
> I have read alot of tutorials and forum posts.  Tried alot of stuff.(...) I've tried to install other versions of Ubuntu but no success with any of them.  

I am using USB-Sticks to install Ubuntu(s) on machines without cd-rom-drives since months. All informations you need are on the web.  
If you can not install Ubuntu using Unetbootin and can not boot from PXE, than try mentioned pendrive-linux-solution, or other methods/tutorials:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is even a script, to create a flash drive that can be used for installing Ubuntu Server:
[https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

---

### Post by doglover56 on 2010-12-11
Hello.  I was trying this and I can't get it to work.
I started the install just fine, and as predicted it wouldn't find the CD.  So I mounted the USB as /cdrom, and was able to confirm by cd'ing to /cdrom and could browse the USB drive.  So, it should be working, but when I continue the install it still tells me that it can't find the CD.  I tried it both ways, just mounting the USB on /cdrom and using the symbolic link through /dev.  Both allow me to browse the USB drive through /cdrom.  

Anybody else had success?
Thanks,
IMF

---

