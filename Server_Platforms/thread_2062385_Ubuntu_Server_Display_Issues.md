---
title: "Ubuntu Server Display Issues"
date: 2012-09-24
forum: Server Platforms
---

### Post by dolphin194 on 2012-09-24
I am having issues with Ubuntu 12.04.1 Server (32-Bit) on my Dell PowerEdge 2650. The computer operates fine with the operating system, however I cannot see anything I am doing.

When I plug a monitor into the computer, it either says "Frequency out of range" or "Entering power save," therefore I cannot see anything on the screen.

So I go in and type 
```
sudo reboot
```and enter my password and the computer rebooted just fine.

But I couldn't see anything I was doing.

---

### Post by lisati on 2012-09-24
A vague recollection of a similar issue while my server boots (but not when booting has completed) has me wondering if adding the "nomodeset" option in your grub menu will help, e.g. as described here: [http://ubuntuforums.org/showthread.php?t=1598078](http://ubuntuforums.org/showthread.php?t=1598078)

---

### Post by DC80 on 2012-09-25
Hi,

I do not know about screen settings as something like this never happend to me. 

However, maybe ssh will help. I know you need to type blind but if you can install ssh then you are at least able to access the server from a remote location.

---

