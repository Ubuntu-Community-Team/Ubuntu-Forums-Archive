---
title: "Is anyone trying Gnome on Wayland?"
date: 2015-06-06
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-06-06
Installed gnome-session-wayland. I cannot see much difference in performance, maybe its me. Have you guys using Wayland, and what are your feelings about it?:)

---

### Post by grahammechanical on 2015-06-06
Have you not noticed missing letters in dialogs and applications? That is what I get with the Gnome Wayland session. I installed Wily Ubuntu Gnome and gnome-session-wayland just the other day. What I see is similar to this thread although that subject is about Xubuntu and not with a Wayland session.

[http://ubuntuforums.org/showthread.php?t=2281000](http://ubuntuforums.org/showthread.php?t=2281000)

Regards.

---

### Post by Chanath on 2015-06-06
> **grahammechanical said:**
> Have you not noticed missing letters in dialogs and applications? That is what I get with the Gnome Wayland session. I installed Wily Ubuntu Gnome and gnome-session-wayland just the other day. What I see is similar to this thread although that subject is about Xubuntu and not with a Wayland session.

[http://ubuntuforums.org/showthread.php?t=2281000](http://ubuntuforums.org/showthread.php?t=2281000)

Regards.

Clicking on a file/folder won't open, but would on right click. Hide top bar extension won't come out of hiding, when a file/app is maximized. No other problems. 

What would be the special stuff that Wayland would do that X cannot?

---

### Post by zika on 2015-06-06
Answer to question that gives the name of this thread: Yes, both in GDM *1) and as &#8222;separate&#8220; session *2).
Separate session is faster. After going to 3.17 I've encountered some problems but not those that could not be bridged or disregarded... ;)
I like it.
*1: Gnome on Wayland from GDM
*2: from tty:```
/usr/bin/gnome-session --session=gnome-wayland
```Both could be used at the same time... ;)

---

### Post by grahammechanical on 2015-06-06
> What would be the special stuff that Wayland would do that X cannot?

It is not so much a matter of special stuff but what would we do differently if we had to start from the beginning again.

[http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29](http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29)

Regards.

---

### Post by virgosun on 2016-04-20
Will not install because incompatibility with GeForce 940M

---

### Post by rickard-s on 2016-04-26
I am experiencing strange flickering and distortion that follows beneath the mouse on the screen. I have a laptop with Intel HD3000 and Nvidia Gefore GT540M GPU's using the open source drivers. In X11 it works good.

---

### Post by grahammechanical on 2016-04-26
Nvidia driver Wayland & Mir support coming.

[http://www.linux-magazine.com/Online/News/New-Nvidia-Driver-Offers-Wayland-Support](http://www.linux-magazine.com/Online/News/New-Nvidia-Driver-Offers-Wayland-Support)

Regards.

---

### Post by kurt18947 on 2016-04-26
No .desktop launchers on the Desktop Ubuntu-Gnome 16.04. Long time Windows users that don't like change don't like that.  There were some gnome-shell extension that didn't work though I don't recall which ones or if they've been rewritten.

Aanndddd I can't log in on one machine. Same O.S. as above, Ubuntu-Gnome 16.04 64 bit. A Thinkpad 410 will permit login to a wayland session. A desktop with AMD 785 chipset and 4200HD video will return to the Lightdm screen after entering the password. This machine works fine with the default option. Wayland *was* working on this machine but stopped some weeks ago.

---

### Post by ventrical on 2016-04-30
> **zika said:**
> Answer to question that gives the name of this thread: Yes, both in GDM *1) and as &#8222;separate&#8220; session *2).
Separate session is faster. After going to 3.17 I've encountered some problems but not those that could not be bridged or disregarded... ;)
I like it.
*1: Gnome on Wayland from GDM
*2: from tty:```
/usr/bin/gnome-session --session=gnome-wayland
```Both could be used at the same time... ;)

It is working well on yakkety. (the above method). You can log on to gnome-classic in one console and ubuntu-gnome(wayland) in the other. If you try to run another instance of browser - lets say firefox- it will alert you that the other session is still running. ;)

Also do not see missing characters .. etc..

note to mods - I am carrying this over to yakkety dev as I am experimenting with wayland on dev cycle.

---

