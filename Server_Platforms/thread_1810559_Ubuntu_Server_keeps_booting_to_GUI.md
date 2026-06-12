---
title: "Ubuntu Server keeps booting to GUI"
date: 2011-07-23
forum: Server Platforms
---

### Post by Jake2607 on 2011-07-23
I'm working on a (minecraft) server on some old hardware and started by installing a fresh copy of ubuntu server 11.04. After that I installed the minimal xfce system with the guide at [http://www.howforge.com/how-to-install-pure-xfce-on-ubuntu-server](http://www.howforge.com/how-to-install-pure-xfce-on-ubuntu-server) . I've tried every trick I could find on to disable it from starting up, but it appears every time! Wierdly enough, it doesnt display any standard looking login screen, but instead displays this old looking login screen with a debian logo. Not sure how to get a screen shot of it. All I want is it to boot into a command line!

---

### Post by jramshu on 2011-07-23
In Grub you need to change from "quiet splash' to "text."

You need to edit /etc/default/grub
from:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="text"

```
sudo update-grub
```

---

### Post by Jake2607 on 2011-07-23
> **jramshu said:**
> In Grub you need to change from "quiet splash' to "text."
 
You need to edit /etc/default/grub
from:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="text"
 
```
sudo update-grub
```
Already tried it. Doesn't work.

---

### Post by jramshu on 2011-07-23
That's odd, always worked before in 11.04.

---

### Post by Jake2607 on 2011-07-23
It probably has to do with the weird way I installed xfce.

---

### Post by elico on 2011-07-23
so remove xfce...

---

### Post by stlsaint on 2011-07-23
Why did you install a desktop environment for a server? If you wanted a xfce system than install xubuntu. By installing the xfce desktop than you added all the default applications that come with it that are going to use up resources on your server which defeats the purpose of using xfce! Use something like webmin for a graphical front for your server! :guitar:

---

### Post by HermanAB on 2011-07-24
Howdy,

Jeez, only useless comments so far.  You don't need to uninstall Xfce or anything drastic.

You are in the wrong runlevel.  To disable X, change the server to runlevel 3.

Here is a somewhat dated explanation:
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

and this explains what changed since the above:
[http://nixcraft.com/linux-software/2654-ubuntu-set-default-runlevel-etc-inittab.html](http://nixcraft.com/linux-software/2654-ubuntu-set-default-runlevel-etc-inittab.html)

---

