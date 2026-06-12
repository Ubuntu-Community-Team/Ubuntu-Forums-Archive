---
title: "What a pain."
date: 2010-01-23
forum: Testimonials &amp; Experiences
---

### Post by noobeh on 2010-01-23
I think I have had every headache one could possibly have with this installation.  I used the "Install in Windows" option and here is my experience:

Wubi installed the files fine, then reboot, select ubuntu from boot menu, it got to some window I couldn't recognize because the color was maybe set to 4 colors.  I figured out from the web how to shut of X, did so and got the ubuntu@ubuntu prompt.  I was looking for inittab, couldn't find it to set the runlevel- looked for xorg.conf- couldn't find it.  About a minute into poking around I got booted out automatically.  I got to the boot menu selected ubuntu, got dumped out to sh:grub, rebooted went into XP and uninstalled and reinstalled.  Before rebooting I thought maybe ubuntu didn't like my flat screen so I connected it to another I have rebooted and got the exact same crud as before.  ctrl-alt-F2'ed out of the messed up screen went back into Windows, figured it wasn't the monitor it must be the video, looked up reasons why ubuntu may have a problem with Nvidia 8800 and came up with a possible problem with DVI.  So, I rebooted, enabled my onboard VGA, plugged the monitor into my motherboard's video, went to the boot menu and viola!  Ubuntu went through the installation screens which were now readable, got to the end, did the reboot and got dumped to sh:grub.  I must have done some thing wrong I said to myself and started again.  Rebooted, enabled the Nvidia card, went back into Windows, uninstalled and reinstalled ubuntu, rebooted, stopped back at the BIOS to reenable the onboard VGA, picked ubuntu from the menu, got to the setup screen in ubuntu, and the computer locked up at 5% while setting up the file system on the disk image.  Reset the computer, stopped at the BIOS, reenabled the NV card, booted back to windows and spent 2 hours waiting for CHKDSK to run on two partitions.  The root.disk was corrupt, so I deleted the found files from CHKDSK, reinstalled ubuntu, rebooted, stopped at the BIOS to reenable the onboard video, picked ubuntu, and this time holy cow it made it into ubuntu, through the setup and all I needed to do was reboot before using it!  Rebooted the computer, picked ubuntu, and then got dumped to sh:grub.  Now what is this I thought?  Rebooted, BIOS, set vid, go to Windows, research what the heck is sh:grub, found the answer on the forums after an hour or so of poking around, got some instructions for these commands:

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot

I tried them out all I needed was the correct sda#, after 3 tries, I found sda5 to be the correct one.  I now get into ubuntu and all seems to be working.  I get the NVidia driver from the Nvidia site, find out how to shut down gdm and the driver installs without a hitch.  So, I reboot, BIOS, enable the NV card, boot into ubuntu and holy cow it is all workin'.  I pat myself on the back, go the software manager, downloaded anarok, pick an internet radio station to listen to while I set up ubuntu to my liking, and what's this?  yep, the sound doesn't work.  I look for the mixer on the menu, can't find it, so I download GNOME Mixer, all is setup correctly as far as I can figure there.  So, I reboot, go back to windows uninstall ubuntu, edit the boot.ini file and I'm free of that nightmare once and for all.  I'm installing Topologilinux as I type this (I know that works.) :popcorn:

I think the "Install in Windows" option needs some tweaking.

I mainly uninstalled ubuntu because it didn't have much software installed by default and I realized I was going to have to spend a bunch of time doing that on top of getting the sound working.

---

### Post by HoboElectus on 2010-01-23
The only problem I've ever had is the boot menu getting left behind after I deleted the WUBI install. Annoying but fixable.

---

### Post by Swagman on 2010-01-23
When using wubi to install within windows it is pretty vital to have defragged first. 

If you possibly can, do **NOT** install in C:\
Your system *Should* have another partition for your stuff so you don't have to stick it in the "Engine Room" (C:\)

---

### Post by noobeh on 2010-01-23
> **Swagman said:**
> When using wubi to install within windows it is pretty vital to have defragged first. 

If you possibly can, do **NOT** install in C:\
Your system *Should* have another partition for your stuff so you don't have to stick it in the "Engine Room" (C:\)

I installed to my D drive.  I think that's what grub is barfing on and why the need for specifying where the linux images reside.   

At any rate, I'm typing this on Slackware, so my day isn't completely without victory.   I love trying new stuff. :KS

---

### Post by juancarlospaco on 2010-01-23
Dont use Wubi.

---

### Post by d3v1150m471c on 2010-01-23
install from a live cd. and in the future, upgrade from the live cds. this will save you loads of trouble.

---

### Post by mkvnmtr on 2010-01-24
I do not know why a new user does not use Virtual Box to install and try a new distro like Ubuntu. It is easier than installing to the disk and when you mess it up you can do it again.

---

### Post by HoboElectus on 2010-01-24
> **mkvnmtr said:**
> I do not know why a new user does not use Virtual Box to install and try a new distro like Ubuntu. It is easier than installing to the disk and when you mess it up you can do it again.

Maybe they don't know about virtualization?

---

### Post by Tamlynmac on 2010-01-24
> noobeh

Thank you for sharing your experience and Good Luck.

---

### Post by steveneddy on 2010-01-31
I never recommend Wubi.

IMHO - wubi sucks.

It is better IMHO to use VirtualBox to run Ubuntu while using Windows.

My .02

---

