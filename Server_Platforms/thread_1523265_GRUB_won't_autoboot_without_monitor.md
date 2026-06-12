---
title: "GRUB won't autoboot without monitor"
date: 2010-07-03
forum: Server Platforms
---

### Post by johnuk09 on 2010-07-03
I've installed Ubuntu Server on an old computer and I want it to autoboot as it is intended to be a headless box.

I have installed the desktop packages to allow me to use FreeNX.

Basically the problem is similar to what is described here:
[http://blog.computerant.com/2010/03/22/grub-2-bug/](http://blog.computerant.com/2010/03/22/grub-2-bug/)

Unfortunately I've already made these changes and it still seems to need a monitor before it will show the boot menu and a keyboard to press enter on the first option.  If I restart from within the gnome desktop, it will reboot perfectly. If I use shutdown -r now, shutdown -s now or shutdown -h now and then power it on again, it will display the GRUB boot menu without automatically booting.

This is the latest version of karmic.  Does anyone have any suggestions?

---

### Post by wojox on 2010-07-03
What if you set it to automatic login?

---

### Post by johnuk09 on 2010-07-03
I have tried this but it doesn't get far enough to automatically log in. Therefore, since it doesn't even respond to pings, I can only assume that it isn't autobooting, seemingly due to lack of monitor and then not displaying anything when I plug the monitor in (until I reboot) due to lack of monitor on the first attempt?

---

### Post by Derspankster on 2010-07-03
Same problem here after upgrade to Lucid from 8.04. I run gnome desktop on my server because I use a webcam app that requires Wine to run a Win only interface. 

I'll keep searching for a solution. As it stands now, I must connect a monitor if I reboot for some reason. Autologin is set but no X headless.

---

### Post by not_a_phd on 2010-07-29
I have had similar issues with Karmic on a headless installation. If the machine was shutdown cleanly, it will automatically boot the next time. However, if it was not shutdown cleanly, it will bring up the Grub menu, waiting for a keyboard response on the next boot. 

I have hunted around the /etc/default/grub settings file, but to no avail.

---

### Post by gobbledigook on 2010-07-30
are we sure this is a grub problem and not a BIOS setting causing the halt?

personally i've never had any problems with any version of ubuntu and the boot halting at the grub menu. It normally has a countdown and then boots the first thing in the list... can you post your grub menu? should be in /etc/defaults/grub/menu.list ?  could be that this is the problem. Also do you leave a keyboard plugged in? i have to do this to get a headless boot.

---

