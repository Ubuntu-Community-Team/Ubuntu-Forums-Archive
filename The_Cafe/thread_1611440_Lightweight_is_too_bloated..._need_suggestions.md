---
title: "Lightweight is too bloated... need suggestions"
date: 2010-11-01
forum: The Cafe
---

### Post by TheNessus on 2010-11-01
hey all.

I want a lightweight system, but I don't know my way around it.
So I went to install Lubuntu in addition to gnome, on Meerkat (10.10). But it draws so many dependencies, such as Chromium (already have chrome, opera, and FF, why do I need another one?), its own video and sound players, etc, etc... way too many stuff. So I downloaded lubuntu-minimal, but it's not configured plainly, things don't work, and it feels 'not my own'. So I removed that after installing.
Besides, There are too many lxde and X11 packages running around, I don't know which to pick. 

Simply put, for those of you who are familiar with #!, I want to have something like how it comes out of the box - a very plain tint2 panel and right-click menu, that's it, but also, again, without any added extras, since Ubuntu Gnome already has a lot of stuff of it's own. I want as little things as possible running in the background...

---

### Post by jhsu802701 on 2010-11-01
Don't use Ubuntu.  Instead, use antiX Linux, a lightweight version of MEPIS Linux.  antiX Linux is my favorite distro, because no other distro offers its unique combination of lightweight operation (competitive with Puppy Linux), superior repository (Debian compatible), and user-friendliness (no endless configuring just to be able to shut down from the GUI).

---

### Post by smellyman on 2010-11-01
If you just want Openbox then...
 
Why not #! or Archbang?  I like doing my own arch install with openbox, but Archbang is a good implementation and saves you some hours of configuring.  :)

---

### Post by CraigPaleo on 2010-11-01
Might want to try [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"). It's based on Ubuntu.

---

### Post by TheNessus on 2010-11-01
Good suggestions; however, I'm too weary of driver issues. Especially Broadcome wireless (propriety), and led backlight issues. Even with ubuntu I had to configure these two before they worked, or worked properly. Never got #! to reduce backlight right, and never got Fedora to use the wireless, for example.

---

### Post by smellyman on 2010-11-01
> **TheNessus said:**
> Good suggestions; however, I'm too weary of driver issues. Especially Broadcome wireless (propriety), and led backlight issues. Even with ubuntu I had to configure these two before they worked, or worked properly. Never got #! to reduce backlight right, and never got Fedora to use the wireless, for example.
 
I havent tried this: [LINK]("http://www.pclinuxos.com/forum/index.php/topic,79046.0.html") 
 
but PCLinuxOS generally has great driver support and this is a minimal install of openbox.

---

### Post by TheNessus on 2010-11-01
> **smellyman said:**
> I havent tried this: [LINK]("http://www.pclinuxos.com/forum/index.php/topic,79046.0.html") 
 
but PCLinuxOS generally has great driver support and this is a minimal install of openbox.

As suspected, Broadcom issues... [http://www.pclinuxos.com/forum/index.php/topic,79046.msg652962.html#msg652962](http://www.pclinuxos.com/forum/index.php/topic,79046.msg652962.html#msg652962)
I think it's best if I say in the .deb area anyway and not venture into RPM land :)

Puppy linux and antiX both look interesting but my computer doesn't that extreme minimalism, it is an i3, 3gb ram, etc. I mainly don't want clutter, rather than a need for speed. Maybe #! worth another shot then...? Since the new #! is Debian based though, I'm weary about it.

---

### Post by smellyman on 2010-11-01
> **TheNessus said:**
> As suspected, Broadcom issues... [http://www.pclinuxos.com/forum/index.php/topic,79046.msg652962.html#msg652962](http://www.pclinuxos.com/forum/index.php/topic,79046.msg652962.html#msg652962)
I think it's best if I say in the .deb area anyway and not venture into RPM land :)
 
Curses broadcom!!!
 
of course there have been kernel updates and changes since then.

---

### Post by hhh on 2010-11-01
I ran a standalone Openbox session on Jaunty for 6 months that was super snappy. I used these two sources...
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
...plus the Openbox wiki and Arch's Openbox page. I highly recommend it if you want the convenience of Ubuntu with a snappier setup.

Installing an Xfce session would be another route that would be less alien feeling than Openbox. I don't know if I would install the entire xubuntu-desktop as when I tried Xubuntu a couple of years ago, it really wasn't very fast, though that might have changed by now. Anyway, it's easy enough to install either xubuntu-desktop or just xfce4, and easy enough to undo the changes...
[https://help.ubuntu.com/community/Installation/LowMemorySystems#XFCE](https://help.ubuntu.com/community/Installation/LowMemorySystems#XFCE)

That whole page is worth checking out. To remove xfce4, for example, you'd run this in a terminal...```
sudo aptitude purge xfce4
```

---

### Post by hhh on 2010-11-01
> **TheNessus said:**
> Since the new #! is Debian based though, I'm wary about it.
Don't download the Statler alpha then, download the stable release which is based on Jaunty...
[http://www.crunchbanglinux.org/wiki/downloads](http://www.crunchbanglinux.org/wiki/downloads)
That would give you a stable Openbox setup out of the box with all the Ubuntu drivers and none of the bloat of having Gnome apps plus whatever another DE or WM would pull in with it.

---

