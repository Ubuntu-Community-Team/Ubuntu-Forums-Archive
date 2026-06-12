---
title: "Ubuntu Server 8.10 and Ubuntu Desktop on Dell Vostro 410"
date: 2008-11-15
forum: Server Platforms
---

### Post by waynehapp on 2008-11-15
I did a clean install of Server 8.10 onto my machine. Dell Vostro 410 and can not get the Ubuntu GUI to work.

When I did the following to get the GUI Desktop after installing from the latest 8.10 cd image off the website.

apt-get install ubuntu-desktop

after a reboot the machine  hangs when I should a login screen.

I tried booting into recover mode and ran xfix, tried to start X - Windows manually via xstart. I get no errors, just a blank screen. 

The beta version of the server installed w/o any problems.

Any workarounds/fixes out there?

---

### Post by lncoll on 2008-11-15
I had a similar problem in my Vostro 410 too. This is solved adding irqpoll in the kernel line in Grub.

Luis

---

### Post by waynehapp on 2008-11-15
That did not work for me.

I booted into recover mode,
went into a shell 

then

nano /boot/grub/menu.lst

At the end of the kernel line I added irqpoll.

Saved, exit

then ran

update-grub

Told it to use the new menu.lst

rebooted and nothing.

---

### Post by lncoll on 2008-11-16
Ok, sorry it doesn't work. What vga do you have?.
Also you can look at /var/log/Xorg.0.log file for errors.
Is possible that X is using a screen resolution your monitor can't handle, this is more usual with LCD and Widescreen monitors, look at the log file for the resolution frequency in my log says:
(II) NVIDIA(0): Setting mode "1152x864_75" - This means 1152x864 at 75 hz.  
And verify your monitor can handle it, if not you must reconfigure X with a lower resolution.

Luis

---

