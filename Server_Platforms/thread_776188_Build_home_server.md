---
title: "Build home server"
date: 2008-04-30
forum: Server Platforms
---

### Post by i l a n on 2008-04-30
Hi.
I am new in ubuntu and i have ubuntu 7.10. I want to build a home server, and i do have tow computers.
where can i find a guide to do that?
thanks.

---

### Post by ginjabunny on 2008-05-01
there is full documentation here, [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html), but be aware that Ubuntu server doesn't come with a gui (so no gnome, kde, xfce, etc), you'll have to use command line and basic editors to configure it, unless you install something like Webmin (Web based admin tools) or as I just noticed in the that link "eBox" (which is new to me).
You can install a gui if you really want but you don't have to run it all the time, change the run level and startx when you want to use it. Apt will let you install selective packages with having to download the whole desktop.

A few years ago I used Linux server just as a firewall and also had a Win2000 server, but then I figured out that Linux could do both and more so just run Ubuntu server now (with a gui).

What is the spec of your PC?

---

### Post by la3875 on 2008-05-01
Recommend you check out eBox or webmin or you can install Ubuntu desktop on the server box to give you a graphical setup. I'm looking forward to using eBox myself.

Good luck!

---

