---
title: "Difference between running Gnome Shell and Gnome Ubuntu"
date: 2014-04-08
forum: Ubuntu Development Version
---

### Post by wallacegalloway on 2014-04-08
Can anyone explain the difference between running Gnome Shell on Ubuntu 14.04 or running Gnome Ubuntu 14.04, especially considering the former has 5 years of support and the latter 3 years support?

---

### Post by HereInOz on 2014-04-08
I think what you mean is what is the difference between installing Ubuntu 14.04 with the Unity desktop, then installing the Gnome desktop or just Gnome shell on to that machine, as against installing UbuntuGnome as the Gnome flavour of Ubuntu (similar to Kubuntu is the KDE flavour of Ubuntu).  If this is the case, here goes.

If you install Ubuntu and then install either Gnome Shell or the full Gnome desktop environment, you will have Unity and Gnome as desktops which you can switch between at the login prompt.  I prefer the full Gnome Desktop because you get Gnome Classic as well as Gnome 3.whatever it is, whereas with UbuntuGnome, you will only have the Gnome desktop initially.  Nothing to stop you putting Unity on it though.  

In reality, it doesn't matter if you install Ubuntu with Unity, then put Gnome on it, or intall UbuntuGnome and then put Unity on it.  You end up with the same animal either way.  Where did you get the bit about 3 years support?  I was under the impression that all LTS flavours were 5 years.

---

### Post by buzzingrobot on 2014-04-08
It's 3 years:  [http://ubuntugnome.org/lts-status/](http://ubuntugnome.org/lts-status/).

Installing Gnome Shell and the other Gnome packages on a Unity systems, of course, gets you both environments. Unity's default applications are not the same as Ubuntu Gnome's (e.g., Thunderbird versus Evolution) and LightDM will remain the display manager unless the user switches to GDM, used by default in Ubuntu Gnome.

Ubuntu Gnome also has no scopes, lenses, Amazon, web apps, etc., that are part of Unity.

---

### Post by wallacegalloway on 2014-04-08
Thanks Gentlemen...I prefer Gnome 3.10 over Unity 7. Does Unity take up a lot of disk space keeping it? Can i just remove it?

---

### Post by buzzingrobot on 2014-04-08
Not sure how much disk space Unity requires.  

Unity, like Gnome or KDE, is a very large collection of packages with many interlocking dependencies.  Trying to remove Unity, or Gnome, or KDE, is difficult and error-prone, and, frankly, best avoided. (They are very difficult to remove cleanly, meaning packages you probably do not want removed will be.) 

The packages used to install these environments are actually so-called meta-packages that are used as a convenient shorthand.  For intance, installing "kde-full" will trigger the installation of the hundreds of packages that make up a complete KDE installation.  Almost a gig's worth.

If Unity and Gnome are both on a machine, the components of Unity are not executed when you use Gnome, or vice versa.

---

### Post by wallacegalloway on 2014-04-08
Thanks again!

---

