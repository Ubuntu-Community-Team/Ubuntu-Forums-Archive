---
title: "Can't install Guest Additions on VB"
date: 2012-12-01
forum: Virtualisation
---

### Post by Ziza on 2012-12-01
I'm fairly new to Linux and VirtualBox, so bear with me.

I installed Zorin OS and then Guest Additions and it worked fine at first, but after I had updated all my packages it stopped working - I could no longer run it in Seamless mode. If I tried to re-install GA, it said "Unable to mount the CD/DVD image [name of image] Would you like to force mounting of this medium?" Then underneath: "could not mount the media/drive [name] (VERR_PDM_MEDIA_LOCKED)"

The same thing happened with several Ubuntu-based distros I tried, most recently Lubuntu. It works fine prior to updating, but after that I just get error messages.

From the Terminal, I ran sudo sh /media/cdrom/VBoxLinuxAdditions.run, but it says 'Can't open'

Under 'Disks' it says it is mounted. Unmounting and ejecting then retrying doesn't help.

What am I doing wrong?

I'm running the standard "lubuntu-12.10-desktop-i386.iso" on OSX Mountain Lion, allocating 1gb RAM and 8gb disk space.

---

### Post by Cheesemill on 2012-12-01
Instead of installing the guest additions through VirtualBox try installing the package from the Ubuntu repositories on your guest VM.
```
sudo apt-get install virtualbox-ose-guest-utils  virtualbox-ose-guest-x11 virtualbox-ose-guest-dkms
```
This way the guest addition modules will automatically recompile every time you update the kernel (which is what is breaking them).

---

### Post by Ziza on 2012-12-01
That worked perfectly, thanks. (You need to reboot after installing, of course.)

---

### Post by Ziza on 2012-12-01
...so how do I actually view the folders in the guest? Adding them to VB Shared Folders is easy, but they don't show anywhere on the guest machine. 

I tried about 10 different ways that I found online, most involving typing a lot in Terminal, but none has worked. The closest I got was creating some extensionless files in /media/ with the names of the folders in Host that I want to share.

---

