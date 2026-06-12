---
title: "Kubuntu - Wayland"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by xc3RnbFO8P on 2014-02-27
When upgrading I got a messages "libwayland.......rpm" not needed, use autoremove bla bla
and I did, now Kubuntu looks like a beaten dog, useless.
When I try to start kwin from terminal it says :
> rig@rig-Aspire-R3600:~$ kwin --replace
kwin: error while loading shared libraries: libwayland-egl.so.1: cannot open shared object file: No such file or directory
If I try to install Wayland I get:
> rig@rig-Aspire-R3600:~$ sudo apt-get install libwayland0
[sudo] password for rig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libwayland0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libwayland-server0:i386 libwayland-cursor0:i386 libwayland-client0:i386
  libwayland-server0 libwayland-cursor0 libwayland-client0

What is the plan with Kubuntu?

---

### Post by marco-parillo on 2014-02-27
According to:
[http://blogs.kde.org/2013/06/26/kubuntu-wont-be-switching-mir-or-xmir](http://blogs.kde.org/2013/06/26/kubuntu-wont-be-switching-mir-or-xmir)
We'll be staying with X on the images for our 13.10 release now in development and the 14.04LTS release.

---

### Post by xc3RnbFO8P on 2014-02-28
Strange I found the solution today, yesterday I found nothing :confused:, maybe bug in Chromium :)
> ln -s /usr/lib/x86_64-linux-gnu/mesa-egl/libwayland-egl.so.1 /usr/lib/libwayland-egl.so.1

[https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371](https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371)

---

### Post by grahammechanical on 2014-02-28
Kubuntu is built on KDE, is it not? So, what do the KDE developers say about the possibility of a KDE Wayland compositor coming from them any time soon?

> [COLOR=#2E3436][FONT=Open Sans]Writing a new Wayland Compositor would require to rewrite the complete X11 workspace in one go. This includes not only the Window Manager, but also parts of Plasma, KDM, Screen Locker and many, many more. This would take a long development time and the transition would not be smooth, very likely buggy and with regressions like the 4.0 introduction. We do not want to break the desktop![/FONT][/COLOR]

[https://community.kde.org/KWin/Wayland](https://community.kde.org/KWin/Wayland)

---

### Post by wolfgentleman on 2014-02-28
> **Ringi said:**
> Strange I found the solution today, yesterday I found nothing :confused:, maybe bug in Chromium :)
[https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371](https://bugs.launchpad.net/kubuntu-ppa/+bug/1206371)

+10 I have been searching for this for 2-3 days and just found it. THANK YOU!

---

### Post by xc3RnbFO8P on 2014-02-28
> **grahammechanical said:**
> **Kubuntu is built on KDE, is it not?** So, what do the KDE developers say about the possibility of a KDE Wayland compositor coming from them any time soon?



[https://community.kde.org/KWin/Wayland](https://community.kde.org/KWin/Wayland)

Yes, I'm worried about they drop the support to Kubuntu, they were close to do it last year.
I always install Kubuntu session and it is getting better, more stable and sexier :cool:

________________________________________________________________________________________________________________

> +10 I have been searching for this for 2-3 days and just found it. THANK YOU!

You're Welcome :)

---

### Post by lamb123 on 2014-03-01
when will KDE 5 be released anyhow?

---

### Post by xc3RnbFO8P on 2014-03-01
> **lamb123 said:**
> when will KDE 5 be released anyhow?

Project Neon 5 ?

[[img]https://c2.staticflickr.com/8/7386/12857927695_83e6ea5651_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12857927695/)
[Project Neon 5  01](http://www.flickr.com/photos/96052779@N07/12857927695/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

