---
title: "server text screen resolution"
date: 2013-11-18
forum: Server Platforms
---

### Post by docbop on 2013-11-18
Installed the latest Ubuntu server 13.10 and want to increase the screen resolution to see more on the screen.   Ia there an article or tech note on how to change resolution of the text screen.

---

### Post by nerdtron on 2013-11-18
Try rebooting the server with the monitor attached to it. In my experience, it boots with the native resolution of the monitor, say for example 1440x900.

Anyway, why bother configuring it with a monitor attached? Just setup the IP address of the server and do all your configuration remotely. You can easily use copy/paste/scroll when you use your own terminal to ssh on the server.

---

### Post by papibe on 2013-11-18
Hi docbop.

Try this:

Edit your default grub file:
```
sudo nano /etc/default/grub
```
Look for a line that looks like this:
```
#GRUB_GFXMODE=640x480
```
And edit it so it looks something like this:
```
GRUB_GFXMODE=1024x768
```
(choose a resolution your monitor supports).

Save the file. Update grub:
```
sudo update-grub
```
and finally restart your computer.

Hope it helps. Let us know how it goes.
Regards.

---

