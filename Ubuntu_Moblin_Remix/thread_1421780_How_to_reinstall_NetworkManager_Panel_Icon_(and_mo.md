---
title: "How to reinstall NetworkManager Panel Icon (and more)"
date: 2010-03-04
forum: Ubuntu Moblin Remix
---

### Post by bebopjazz on 2010-03-04
All of my panel icons have gone away for some reason. In fact, networking was not enabled either. I restarted the network but I don't have the icons that are left of the time icon on the upper panel. This included the network-manager icon. I don't see these in the dialog box to add panel apps. Seems that this might be one app that included all of those icons?

I don't know if this happened after the latest update or not. How can I check to see if I have a new kernel? Ubuntu doesn't have a /boot/grub/grub.conf file, or at least I didn't find it.

thanks!

btw, is this the correct forum for UNR? I didn't see a specific one for ubuntu NETBOOK remix.

(UNR needs a new name. It's too close to UMR)

---

### Post by Anthony523 on 2010-03-04
I just had the same problem and that's why I'm looking around on here if anyone has a fix please help..

---

### Post by bebopjazz on 2010-03-05
It would be nice for someone to help us on this. I think I updated, got a new kernel, and the network manager in the panel went away. On top of that, not networking. I couldn't "ifup eth0" or "service networking start" (and I don't know if that's the right service for networking on Ubuntu anyway)

 I'm a gentoo and fedora user so when I looked for /boot/grub/grub.conf and couldn't find it, I went on a search to find out how Ubuntu uses grub. Now I can reboot with an older kernel

Still it would be nice for someone to either tell us how to reinstall network-manager icon or tell us if something has changed in the updates for UNR.

thanks much,

brad

---

### Post by bebopjazz on 2010-03-05
I found an answer:
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)
scroll down to Missing Panel Applet. It says:

I had to reinstall network-manager-gnome

Also note that if you were logging in with Gnome-failsafe mode then you might not have all the panel icons. Check that before you log in.

---

