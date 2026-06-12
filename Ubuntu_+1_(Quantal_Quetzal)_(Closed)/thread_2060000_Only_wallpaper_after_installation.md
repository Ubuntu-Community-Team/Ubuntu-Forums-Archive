---
title: "Only wallpaper after installation"
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Graham1 on 2012-09-19
Hi 

I have installed both the beta and daily build (18/09/2012) of Ubuntu 12.10 onto my HP TC1100 tablet but on both occasionals, after the installation finishes, it boots to a blank desktop (only the wallpaper is visible). Any ideas what might be causing this? If you need any more info, please let me know.

:)

---

### Post by dino99 on 2012-09-19
you might need to test some boot option, like nomodeset; then logs might help. Do you have a xorg.conf built ? If so remove it as kernel directly deal with X.

---

### Post by Graham1 on 2012-09-19
> **dino99 said:**
> you might need to test some boot option, like nomodeset; then logs might help. Do you have a xorg.conf built ? If so remove it as kernel directly deal with X.

Hi dino99

Adding "nomodeset" to the livecd (usb) seems to have fixed my problems. However, the system is very unresponsive. Would this be the case if I had installed (tested) directly from the harddisk?

:)

---

### Post by Graham1 on 2012-09-20
I have since re-installed Ubuntu 12.10 (daily: 19/09/2012) back onto my tablet but I am unable to get to the point where I add "nomodeset" to test. Is there a special key I need to press during startup?

:)

---

### Post by funicorn on 2012-09-21
Yes, firstly you need to continuously press 'shift' once upon bios slpash, then you will see the grub boot menu.  Then press 'e', you will enter grub editing mode.  Shift the cursor to the end of the line started with 'linux' , type  in 'nomodeset', then press 'ctrl + X'. This will boot your system with kernel parameter 'nomodeset'.

---

