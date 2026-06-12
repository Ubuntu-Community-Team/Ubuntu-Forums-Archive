---
title: "increasing screen size  in virtual box"
date: 2008-02-18
forum: Virtualisation
---

### Post by Tucatts on 2008-02-18
I have Gutsy running just fine in a virtualbox setting. It all works fine with one exception. The screen size shown for VirtualBox as it resides on my 22" widescreen (1680x1050 resolution) is a box about 11" or so square. I have used the "install Guest Additions" with no change. So does anyone know how to make VirtualBox utilize  more real estate on my LCD screen? 
Many thanks,
Tucatts

---

### Post by randy78 on 2008-02-18
> **Tucatts said:**
> I have Gutsy running just fine in a virtualbox setting. It all works fine with one exception. The screen size shown for VirtualBox as it resides on my 22" widescreen (1680x1050 resolution) is a box about 11" or so square. I have used the "install Guest Additions" with no change. So does anyone know how to make VirtualBox utilize  more real estate on my LCD screen? 
Many thanks,
Tucatts

CTRL+F enables fullscreen...
Try that, then try adjusting your settings in the Guest OS

---

### Post by kpkeerthi on 2008-02-19
1. On your ubuntu guest, install **build-essential** package using Synaptic
2. Install [vbox guest additions]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/")
3. Reboot guest. Choose **Recovery mode** from GRUB
4. Reset resolution by running the command:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
... and choose 1680x1050, leaving the rest default.
5. Reboot.

---

### Post by Tucatts on 2008-02-24
Hey kpkeerthi, wanted to say Thank you! Your instructions worked like a charm and I have the full 1680x1050 resolution now and it looks great!
Thanks again,
Tucatts

---

### Post by sbussy89 on 2008-03-23
OK, I got my screen resolution set (when I restarted the machine it magically fixed itself) but now every time I click in the window my mouse disappears.  It's there, because if I run it over the menu options they get highlighted, but I can't see it otherwise.  What can I do to get my mouse back?

---

### Post by ilari on 2008-03-23
Replace mouse driver "mouse" with "vboxmouse" in /etc/X11/xorg.conf configuration.

You can do this easily without needing your invisible mouse by opening a virtual terminal (press ctrl-alt-F1), logging in and using vi to edit the file. Then restart X with "sudo /etc/init.d/gdm restart"

---

### Post by pranav_ps on 2010-09-08
Thanks a million for enlightening...

---

