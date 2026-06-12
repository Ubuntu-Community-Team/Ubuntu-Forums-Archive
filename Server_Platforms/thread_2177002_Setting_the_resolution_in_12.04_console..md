---
title: "Setting the resolution in 12.04 console."
date: 2013-09-26
forum: Server Platforms
---

### Post by codingman on 2013-09-26
I have tried changing the GFXMODE and GFXPAYLOAD in GRUB, but that doesn't work.

The issue is that during installation, I had the server connected to a large, 1600x1200 monitor, but now it is connected to a monitor that is 1280x1024. Thus, there is a teensy bit of screen that is lost, and the font is extremely large.

---

### Post by Petro Dawg on 2013-09-26
Have you tried using...

```
xrandr -s [COLOR=#000000]1280x1024[/COLOR]
```

---

### Post by codingman on 2013-09-26
xrandr is not installed.

---

### Post by Petro Dawg on 2013-09-26
Yup, I see now you are using a server.

Here is an article about how to change it in the server edition...

[http://blog.mattrudge.net/2012/10/02/changing-the-tty-resolution-on-ubuntu-server/](http://blog.mattrudge.net/2012/10/02/changing-the-tty-resolution-on-ubuntu-server/)

hopefully it will help

---

### Post by codingman on 2013-09-28
Yes, that was the one that I saw just before posting this, with no change whatsoever...

Any answers are appreciated!

---

### Post by Petro Dawg on 2013-09-28
did you try...

```
GRUB_CMDLINE_LINUX="video=VGA-1:1280x1024"
```

Also, just to be sure, did you "update-grub" after saving your changes before reboot?

---

