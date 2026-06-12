---
title: "Ideas for a lighter desktop environment?"
date: 2017-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by william.hua on 2017-11-03
I am currently running Lubuntu 16.04 LTS on an ASUS Eee PC R101D with an Intel Atom N455 CPU. The OS is still laggy despite LXDE being very light. Any ideas on a desktop environment even lighter than LXDE that is compatible with Ubuntu or possibly even another distro?

---

### Post by vasa1 on 2017-11-03
Moved to Ubuntu, Linux and OS Chat. If you need support on Lubuntu itself, please post in Desktop Environments as that sub-forum is for official flavors.

---

### Post by kansasnoob on 2017-11-04
Has it already been upgraded to 2GB of RAM? The stock 1GB just really isn't enough to do much of anything with any web browser.

I recently did a bunch of playing with some Dell Latitude 2100 series netbooks which have similar specs and once I had 2GB of RAM in them I could run either Lubuntu, Xubuntu, or Ubuntu w/Flashback(Metacity) if I installed the uBlock Origin add-on in Firefox. Still not good for streaming videos but good enough for light browsing.

The Legacy edition of Bodhi Linux did seem a bit faster:

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by mörgæs on 2017-11-04
If you click the old hardware link in my signature and search the text for *lubuntu-core* you will find an option for making Lubuntu even lighter.

---

### Post by sudodus on 2017-11-04
I agree with the previous replies.

You can try the ultra-light **Puppy Linux** or **Tiny Core**, if you need something lighter than what is possible with Lubuntu and other distros or re-spins based on Ubuntu.

---

### Post by william.hua on 2017-11-04
Yes, I did upgrade to 2GB of RAM.

Do they have support for the Ubuntu Software Center or something similar?

---

### Post by sudodus on 2017-11-05
Lubuntu and the other Ubuntu community flavours have support for the Ubuntu Software Center and something similar. I would suggest that you learn using the **Synaptic Package manager** and the text mode tool **apt**.

```
sudo apt update
sudo apt full-upgrade
sudo apt install synaptic
```

Puppy Linux and Tiny Core have their own tools to update, upgrade and install program packages.

---

### Post by TheFu on 2017-11-05
> **william.hua said:**
> I am currently running Lubuntu 16.04 LTS on an ASUS Eee PC R101D with an Intel Atom N455 CPU. The OS is still laggy despite LXDE being very light. Any ideas on a desktop environment even lighter than LXDE that is compatible with Ubuntu or possibly even another distro?

You don't need a "DE" for a usable system.  You can run a WM-only (Window Manager only) environment.  I have the last 3+ yrs with either openbox or fvwm.  fvwm has been around since the mid-1990s and is VERY light, but the configuration of it is more manual.  Openbox does setup some menus - just click anywhere on the desktop to see one. Openbox is the WM that LXDE normally uses, so you are already using it.

The main things that will make any OS laggy (after removing all the cheese) is the choice of programs.  Firefox, Chrome, or any huge programs like those will quickly suck all the RAM and CPU from a low-end computer.  Find less taxing versions - perhaps lynx or dillo will work well enough for your browsing needs?   
You can also try to optimize the swap used - perhaps zswap would be helpful?
Also be certain that the GPU has the correct drivers.  On Intel, that is handled automatically, so there isn't much you can do.  The CPU on that machine is really, really, really, slow, as you know.  A used $75 computer would be 10x faster.  I wouldn't try to run any GUI on that system. I'd repurpose it for lite server-only use.  It would run something like Pi-Hole nicely.

Lacking all of that, TinyCore is VERY fast on any system with 256MB of RAM or more. It does have a different package management technique, so don't expect APT (or any of the UIs into APT), but for a purpose built, 1-2 program system, tinycore might be perfect for your needs.

---

### Post by vasa1 on 2017-11-05
OP needs to describe what the intended usage is. Without that information ...

---

### Post by speedwell68 on 2017-11-05
Bodhi Linux.

---

### Post by Tadaen_Sylvermane on 2017-11-05
+1 to the window manager idea. I ran i3 for quite some time on my laptop. Using Plasma now, only so wife can use it if necessary. I love the ease of a tiling window manager though. Learning curve yes, but once you get it you can move around and do things exponentially faster than with a mouse.

---

### Post by su:bhatta on 2017-11-05
+1 to using WM's like Openbox . 
I have used FVWM in past, and, in Ubuntu repos there is FVWM Crystal, which is built on FVWM, customised. (Remember to check out right/left click both options on desktop to be pleasantly amazed)

Both of these have suited my old hardware.
Openbox menus are helpful, so is having a Tint2 panel, and you can check out standalone programs like fdpowermon ( for laptop battery monitoring). Also, gkrellm for system monitoring.
 These programs have very small footprint and helpful.

for playing videos/songs, command line tools are useful.
Do look around, choices are a plenty.

---

### Post by william.hua on 2017-11-05
TinyCore worked out just fine. It runs pretty quickly on my old netbook. Thanks. ;)

---

### Post by kansasnoob on 2017-11-05
> **william.hua said:**
> TinyCore worked out just fine. It runs pretty quickly on my old netbook. Thanks. ;)

I'm curious what you ended up using as a browser? Web browsers have proven to be the most resource consuming app by far.

---

### Post by william.hua on 2017-11-05
I haven't fully decided yet. Right now I'm trying Chromium. It does seem to be a bit resource intensive for my hardware, but since I have such a stripped down OS and Chromium is pretty much the only thing running on my computer that uses a lot of CPU resources, it might work out.

---

### Post by help_me2 on 2017-11-10
> **sudodus said:**
> I agree with the previous replies.

You can try the ultra-light **Puppy Linux** or **Tiny Core**, if you need something lighter than what is possible with Lubuntu and other distros or re-spins based on Ubuntu.
I agree with these suggestions. I've always liked Puppy especially. It is lightning fast on old hardware, plus there are many variants of puppy so you can fine tune the OS for your config without too much hassle.

Or you could just do a minimal text install of ubuntu and run openbox on top of it.

---

### Post by sudodus on 2017-11-11
> **help_me2 said:**
> I agree with these suggestions. I've always liked Puppy especially. It is lightning fast on old hardware, plus there are many variants of puppy so you can fine tune the OS for your config without too much hassle.

Or you could just do a minimal text install of ubuntu and run openbox on top of it.

I agree with your tip about running Openbox (or maybe Fluxbox or some other window manager) to get a minimal yet working graphical user environment.

See these links for more details,

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[...minimal installed system with only a text screen add a light-weight window manager (for example Fluxbox) and the few necessary GUI tools.](https://askubuntu.com/questions/964898/does-stopping-x-server-in-ubuntu-16-04-kde-have-any-negative-effect-while-logged/964904#964904)

---

### Post by kansasnoob on 2017-11-13
I'm currently playing with some old desktops that have ATOM 230 CPU's and I discovered that installing the 'intel-microcode' driver improved performance considerably. I always install 'psensor' when I'm playing with things like this so I can monitor system temps as well as CPU & RAM usage. I mention the importance of monitoring temps because I've found on the P series Intel core 2 duo mobile CPU's 'intel-microcode' causes extreme increase in system temps - enough so to do real damage! But with these ATOM 230's the improvement in CPU response to activity (or end of activity) is vastly improved with no noticeable change in temps.

---

### Post by pete5 on 2017-11-16
I was quite impressed with BunsenLabs. Installed it on an old P4 w/512M and could run Firefox just fine.

---

