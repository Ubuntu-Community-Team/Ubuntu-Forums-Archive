---
title: "Can't seem to install Ubuntu Server 10.04"
date: 2011-09-09
forum: Server Platforms
---

### Post by drerock on 2011-09-09
I've had a heck of a time trying to get Ubuntu Server Installed. 

I've tried using the 10.04.03 AMD64 iso and the 11.04 AMD64 iso 

I tried installing using a cd, and have found that there are many people having trouble installing with NEC 3500 cd-rom drives. Getting an error that says "insert the disc labelled: ..."

so, I got the officially recommended Universal USB Installer, and successfully installed the OS, only to see the system hang at a blinking cursor just after 'Verifying DMI pool data....'

Any ideas?

Thanks

---

### Post by Entilza on 2011-09-09
Did you remove the USB stick afterwards?

Also check the boot order in BIOS after.

---

### Post by drerock on 2011-09-09
> **Entilza said:**
> Did you remove the USB stick afterwards?

Also check the boot order in BIOS after.

Yes, I've tried all the obvious things. It doesn't appear to even be trying to load GRUB or anything as far as I can tell.

---

### Post by Entilza on 2011-09-09
Well did it recognize your hard disk when you installed?  And you installed grub on the MBR at the end without any errors?

No other USB devices plugged in?

---

### Post by drerock on 2011-09-10
When trying with the CD, I get an "Insert CD" error that is apparently widespread with my CD drive. 

When installing from USB it installs the system without any errors. 

When I set my BIOS options, there are two USB boot choices:
USB-CDROM and
USB-ZIP

It only works if I boot from USB-ZIP. 

It seems like a problem with the way the USB drive is detected by the installer. 

I have now also tried this with Ubuntu Server 11.04 CDROM as well, and continue to get the "insert the disc labelled:" error.

---

### Post by Wim Sturkenboom on 2011-09-10
The message is a message from the BIOS. Some solutions found on the web include bios reset, flash bios and a quite extensive guide ([http://www.techrepublic.com/forum/discussions/48-118782](http://www.techrepublic.com/forum/discussions/48-118782) , post by zlitocook)

---

### Post by drerock on 2011-09-11
> **Wim Sturkenboom said:**
> The message is a message from the BIOS. Some solutions found on the web include bios reset, flash bios and a quite extensive guide ([http://www.techrepublic.com/forum/discussions/48-118782](http://www.techrepublic.com/forum/discussions/48-118782) , post by zlitocook)

After tinkering around with BIOS settings I determined that it was not a DMI error. I think the problem is with GRUB installation. I am able to install Puppy Linux 5.2 and it boots right into the GRUB system it installed to the MBR

I still can't figure out why this is such a problem. I am going to try and install Ubuntu again, and then install grub with the puppy cd, but I think they use different versions of grub so it might be tricky

---

### Post by Dangertux on 2011-09-12
Try this, right when your installation is about to finish. Where it tells you to pop out the media drop to a shell alt+f2 and do the following

```

~# chroot /target
# install-grub /dev/hda

```

*note this will install grub on your MBR.

After the install finishes press alt+f1 or exit out to return to the installation and reboot as normal.

I had a similar problem with Lucid the other day and this fixed it. YMMV

---

### Post by drerock on 2011-09-17
Thanks for that tip, it probably would have worked, but I went in through puppy linux and manually updated the grub menu.lst to include the Ubuntu server installation... 

now onto the next problem, getting the server to sleep and wake remotely....

thanks to all

---

