---
title: "Maverick 10.10 + Radeon + Wine + 3D game = flickering"
date: 2010-11-15
forum: Wine
---

### Post by Diskdoc on 2010-11-15
Might be an oldie for the nerds here but it took me a while to figure this out, thought I'd share the solution.

If objects or the screen are/is flickering in games running in Wine, edit /etc/default/grub and do

> sudo gedit /etc/default/grub

and add "nomodeset" the the kernel options, like this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 


Then do

> sudo update-grub

and reboot.

---

