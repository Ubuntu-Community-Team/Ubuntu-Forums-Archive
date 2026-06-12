---
title: "Problem installing ubuntu-desktop"
date: 2007-01-14
forum: Server Platforms
---

### Post by sfoo on 2007-01-14
Hi,

I installed Edgy Eft as a LAMP server and all was fine. Then I decided I'd install a GUI so I did the ```
sudo apt-get install ubuntu-desktop
```

This caused big problems.. On a reboot, I don't get an X login screen. I manage to login to tty1 for a minute and see that "top" shows that all the top processes are apport. After a few minutes I get an out of memory error and the machine hangs. 

"So, let's try the recovery console" I say to myself. Except, that when I get to the bit where it's supposed to launch a shell for me, I get an "Init: sulogin respawning too fast, stopped" error which then gets into an inifinite loop between tying to spawn a shell and that error.. 

I thought I'd try to do an uninstall of ubuntu-desktop, but the machine hangs before it does anything useful..

So.. any ideas? I'm wondering why installing ubuntu-desktop totally screws up the install and, secondly, how do I recover from it?? 

Thanks..

---

### Post by tturrisi on 2007-01-14
ubuntu-desktop is NOT THE graphical environment.  ubuntu-desktop is mainly a lot of unnecessary bloat for gnome.  Just install:
apt-get install gnome-core xorg

---

### Post by sfoo on 2007-01-14
yeah... after digging around a bit, I came to the realization that ubuntu-desktop was more than what I wanted. So, I'm hoping it was one of the unwanted packages that caused my system problems since installing ubuntu-desktop installs xorg and gnome-core (doesn't it?)

I ended up doing a reinstall of the LAMP server because I just couldn't get any sort of shell to clean up the mess (which is somewhat worrying.. ) Anyway, I'll give just gnome-core and xorg a go.

---

### Post by Littleweseth on 2007-01-15
I can't find the exact page on the ubuntu wiki that i used to install my server with a GUI, but this one should come close;

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

Personally, i prefer gdm and openbox to the xdm and icewm given in that set of instructions, but feel free to install whatever you want. Openbox just happens to be the fastest window manager with sensible/usable default settings, imo.

-lws

---

### Post by sfoo on 2007-01-17
I just tried to install gnome-core and xorg. 
However, gnome-core wasn't installed because "no suitable version could be found".
xorg was installed but on startup it complains about the nvidia driver. I seem to be having problems with the nvidia driver even though I have installed nvidia-glx. 

No joy with gdm either..

I think I might have to investigae nvidia-glx a bit further. (I have an onboard GeForce 6100).

---

