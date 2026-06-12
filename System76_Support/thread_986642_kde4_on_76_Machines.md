---
title: "kde4 on 76 Machines"
date: 2008-11-18
forum: System76 Support
---

### Post by jeamer on 2008-11-18
This may be a repeat thread, I apologize if it is.

Wondering if anyone has any distributions running KDE4 (i.e. kubuntu 8.10) on a system76 computer, and if they ran into any problems. I've booted a livecd a few times now, and KDE is just too beautiful now to continue passing by. Even more awesome is any opinions of people that started on GNOME and switched to KDE, and if that posed any specific issues.

Mostly concerned with wireless, a/v, and useability. Thanks!

---

### Post by Lee_Machine on 2008-11-18
I personally like Gnome over KDE. Yes, KDE is by far better looking but has issues with speed and stability. How often do you see a Gnome or Nautilus crash or freeze? Whereas I have seen KDE and the new Dolphin more than you should. 
Again, this opinion goes by KDE 3.5 and KDE 4.0
 
I used KDE4.0 when it first came out and it was admittedly better, I just prefer Gnome.

As for issues, from what I gathered bluetooth will not work at all with KDE4 and Ubuntu 8.10.

Be sides that it's just a matter of choice.

---

### Post by gaussian on 2008-11-19
Am I the only one thinks that branding Kubuntu and Xubuntu as separate distros is a source of enormous amount of confusion?

If you have Ubuntu on your machine you are only a
```

sudo apt-get install kubuntu-desktop

```
away from using Kubuntu. Ubuntu, Xubuntu and Kubuntu desktops are very happy to live under same (Xu/Ku/U)buntu installation and it does really not matter which was installed first. 

There are two caveats I know:
1) Bootscreen & login screen artworks. These tend to revert to the last installed Desktop and can be changed back with little googleing.
2) KDM vs GDM. Kubuntu uses KDM as its default window manager. When you install Kubuntu it offers you to switch to KDM. As far as I know KDE 3/4 works fine under GDM and Gnome/Xfce works fine under KDM.

Bottom line: feel free to try it under your current installation. I have done it as have many others.

---

### Post by wrender on 2008-11-19
I am running kubuntu 8.10 on the Serval Pro. Works great! 

There are a few things that you need to do to make sure all is well.

1. Install Synaptics, Gimp and Firefox installed.

2. Update to KDE 4.1.3

3. Turn off desktop effects before logging out.

4. Then install the system 76 drivers.

I guess some things just need the gtk files that get pulled in with the software installs. (the system76 drivers software worked better)

Kde 4.1.3 stabilizes the system greatly! You do have to have a kind eye and remember that it still is teething. The desktop effects are awesome and even work while highend 3d/opengl software like software Maya 2009 is running unlike compiz which dies. The system is faster with them off and in general it is recommended to turn off desktop effects for speed and stability. If you dont turn them off before logging out you may have problems logging in and will have to use the repair x server option when logging back in. Also turn off show while resizing in this will speed up window management.

 Kubuntu fits my needs and to me personally works beter than the default gnome/ubuntu install. If you really want it you can run it and run it well. If your not sure I would just wait for the next release which is going to rock and make you "never look back".


The only things I havent tried yet is
-finger print scanner
-HDMI out (DVI out works great)


I cant figure out how to use bluetooth, but then again I have never used bluetooth before.

---

### Post by thomasaaron on 2008-11-19
Bluetooth is not supported by 8.10 Kubuntu.
As soon as it is ported, it will come down via an update.

---

