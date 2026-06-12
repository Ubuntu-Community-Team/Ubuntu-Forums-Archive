---
title: "Team Fortress 2 Issues"
date: 2009-06-06
forum: Wine
---

### Post by oh n0es on 2009-06-06
Hello there,

After being installing PlayOnLinux and Wine, I downloaded Steam then downloaded Team Fortress 2.
I tried to launch Team Fortress 2 and the initial Valve sound played and then the menu sound, but there was absolutely no video/display. Checking the processes list, hl2.exe was still running, so obviously something is going wrong here.
My system should be fine, as I used to run TF2 in Windows before switching to Ubuntu, but here are the specs & software:

PlayOnLinux 3.5
Wine v1.0.1-0ubuntu6
Ubuntu (Gnome)

Intel Core2 Quad CPU Q6600 2.4GHz
4GB RAM
NVIDIA GeForce 8500 GT
Resolution: Dual monitors, both 1680 x 1050

Thanks in advance for any help.

---

### Post by NightMKoder on 2009-06-06
Don't know playsonlinux (they...do weird things with wine), but it works nearly perfect on nvidia cars on wine-latest (1.1.23). Try upgrading it: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) . Just install via wine, no pol (just install steam, you don't really need tweaks).

---

### Post by oh n0es on 2009-06-06
I already have the latest version of Wine installed, and the latest nVidia drivers. Still not working.

---

### Post by oh n0es on 2009-06-08
*Bump*
Still can't get anything to work.

---

### Post by u235sentinel on 2009-06-08
> **oh n0es said:**
> *Bump*
Still can't get anything to work.

I've had to use the regular Wine install instructions on the winehq.com/appsdb site to get mine working.  I didn't have a lot of success with playonlinux.

Crossover games however (verson 7.2.0) works pretty good.  I have it running just fine cept for the mic bit.  Otherwise it's something to consider.

---

### Post by oh n0es on 2009-06-08
Thanks for the recommendation. However, I tried CrossOver and nothing displays. I launch Steam and nothing happens, but I can see Steam running in my taskbar.

Nevermind, figured out what was going wrong. It's not ideal, but I have to run TF2 in a Window.
Thanks for the help though.

EDIT: So, it now runs in Wine but it freezes as soon as it reaches the TF2 loading screen after the Valve splash.

---

### Post by u235sentinel on 2009-06-08
> **oh n0es said:**
> Thanks for the recommendation. However, I tried CrossOver and nothing displays. I launch Steam and nothing happens, but I can see Steam running in my taskbar.

Nevermind, figured out what was going wrong. It's not ideal, but I have to run TF2 in a Window.
Thanks for the help though.

did you try version 7.2.0?

I'm also wondering what video card you have.  Nvidia's are usually the way to go.  I've heard people have success with ati but personally I had more problems than I was willing to put up with and switched everything to nvidia.

---

### Post by oh n0es on 2009-06-09
I'm using an nVidia 8500GT. Two displays, both at resolution 1680x1050.

---

### Post by u235sentinel on 2009-06-09
> **oh n0es said:**
> I'm using an nVidia 8500GT. Two displays, both at resolution 1680x1050.

You should be good to go.  Try crossover games 7.2.0 and see if that works for you.  I've had it going for a week and love it

---

### Post by NightMKoder on 2009-06-09
If you're using twinview, I heard that can cause some problems.

---

### Post by joker999 on 2009-06-11
add to launch for TF2 

-dxlevel 81

its work for me. 

Enjoy!

[size=1]however will run as low fps :( like 15 to 20fps[/size]

---

### Post by oh n0es on 2009-06-11
Tried, doesn't work.

---

