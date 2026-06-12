---
title: "Cannot recognize display amd radeon hd 7700 on Ubuntu"
date: 2014-04-07
forum: Ubuntu Development Version
---

### Post by woodwork78 on 2014-04-07
I have managed to install Ubuntu 14.04 64 bit on my desktop computer.
I would like to be able to install the proper video drivers for amd radeon hd 7700.
After boot the plymouth image displays fine, then at login the screen turns to static.  I've tried boot with failsafe graphics to no avail.  Is there a way to login to a viewable gui or terminal and install the proper drivers for my gpu's?

I read this post which seems similar but don't quite understand. [http://ubuntuforums.org/showthread.php?t=2208207](http://ubuntuforums.org/showthread.php?t=2208207)

Cheers!

My login screen looks like this:
[ATTACH=CONFIG]251804[/ATTACH]

---

### Post by ventrical on 2014-04-07
> **woodwork78 said:**
> I have managed to install Ubuntu 14.04 64 bit on my desktop computer.
I would like to be able to install the proper video drivers for amd radeon hd 7700.
After boot the plymouth image displays fine, then at login the screen turns to static.  I've tried boot with failsafe graphics to no avail.  Is there a way to login to a viewable gui or terminal and install the proper drivers for my gpu's?

I read this post which seems similar but don't quite understand. [http://ubuntuforums.org/showthread.php?t=2208207](http://ubuntuforums.org/showthread.php?t=2208207)

Cheers!

My login screen looks like this:
[ATTACH=CONFIG]251804[/ATTACH]


While the USB iso is booting (just slightly before), you tap a key really quick - or hold it down (I use Ctrl+Shift) and the you will come into a screen that will give you F-key options. Hit <enter for default english then F6 and choose nomodeset - Esc and then  try the 'live' or install from there.

Regards..

---

### Post by woodwork78 on 2014-04-07
Thanks ventrical.  After reading your reply I had to google nomodeset and found this info in another thread:
[INDENT]   **nomodeset** 
      The newest kernels have moved the video mode setting into   the kernel. So all the programming of the hardware specific clock   rates and registers on the video card happen in the kernel rather than   in the X driver when the X server starts.. This makes it possible to   have high resolution nice looking splash (boot) screens and flicker   free transitions from boot splash to login screen. Unfortunately, on   some cards this doesnt work properly and you end up with a black   screen. Adding the nomodeset parameter instructs the kernel to not   load video drivers and use BIOS modes instead until X is loaded.
 [/INDENT]After reading this it sounds to me like I just need to edit grub to make nomodeset permanent

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
so that the proper video drivers can load with X.  Is this correct?  Or should I still do a clean install?

---

### Post by QDR06VV9 on 2014-04-07
> **woodwork78 said:**
> Thanks ventrical.  After reading your reply I had to google nomodeset and found this info in another thread:[INDENT]   **nomodeset** 
      The newest kernels have moved the video mode setting into   the kernel. So all the programming of the hardware specific clock   rates and registers on the video card happen in the kernel rather than   in the X driver when the X server starts.. This makes it possible to   have high resolution nice looking splash (boot) screens and flicker   free transitions from boot splash to login screen. Unfortunately, on   some cards this doesnt work properly and you end up with a black   screen. Adding the nomodeset parameter instructs the kernel to not   load video drivers and use BIOS modes instead until X is loaded.
 [/INDENT]
After reading this it sounds to me like I just need to edit grub to make nomodeset permanent

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
so that the proper video drivers can load with X.  Is this correct?  Or should I still do a clean install?
That should work, providing  that option has not changed in trusty.
I'm not aware of any changes there.
```
gksudo gedit /etc/default/grub
```

And then change only th bold underlined text(below)
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
_**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**_
GRUB_CMDLINE_LINUX=""
```

---

### Post by woodwork78 on 2014-04-07
Thanks.  Will try it out tomorrow at the office and let you know!

---

### Post by woodwork78 on 2014-04-08
Thanks for the help.  What I did was hold shift to start grub.  I edited the kernel and added **nomodeset** right after quiet splash, which I read only sets the nomodeset for the current session.

Login and desktop screen works perfect.

To make it permenant I edited grub.
Changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

now everything seems to be working fine!

---

