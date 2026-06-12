---
title: "Removal of a package and its deps."
date: 2005-05-06
forum: Repositories &amp; Backports
---

### Post by Gentist on 2005-05-06
I recently installed Ubuntu on one of my computers for testing purposes, and it went quite smooth all the way through the installation (with the exception of a few boot parameters).

Now, with the system up, I decided to apt-get kubuntu-desktop, since I prefer KDE over GNOME as a desktop environment (although I normally use a lightweight windowmanager instead). So... With KDE installed and fully functional, I decided to get rid of GNOME and everything that came with it. However, that wasn't as easy as installing it. First of all, I don't know which the main package for the GNOME install is, though I guess it is ubuntu-desktop. Secondly, "sudo apt-get remove <package>" does not take care of the dependencies.

Basically, I want to remove the original GNOME install and all of its dependencies which aren't used used by another package or installed by itself (much like Gentoo's "emerge depclean"). I have no idea how I should go about this, and I can't seem to find any documentation explaining this kind of uninstallation process, which I think is quite weird considering that you do not want unused dependencies and packages on your system normally.

---

### Post by bnutting on 2005-05-06
I may be wrong but I don't think there is a sure fire safe way to get rid of gnome on Ubuntu. If you to run KDE and not have Gnome my only suggestion is to install Kubuntu.

---

### Post by Gentist on 2005-05-06
I was under the impression that "sudo apt-get install kubuntu-desktop" was the same as installing kubuntu, with the exception that you will have gnome as well. The thing is, the same applies for kubuntu-desktop. I can't remove it and all of the dependencies safely. I'm not too familiar with the Debian/Ubuntu package manager, but I though it was keeping track of the dependencies installed so that you can uninstall an application/package together with the dependencies that are not in use by another package.

I'm not specifically asking to remove the GNOME installation, I just want to be able to install something, and then later uninstall it without having to manually remove every package that came with it. In short, I guess that you could say that I'm asking for a way to clean out dependencies who's main package is no longer on the system.

---

### Post by fng on 2005-05-06
[QUOTE=Gentist]I was under the impression that "sudo apt-get install kubuntu-desktop" was the same as installing kubuntu, with the exception that you will have gnome as well.[/QUOTE]

Yep

---

### Post by Gentist on 2005-05-06
So how do I uninstall the entire ubuntu-desktop (GNOME) and all of its dependencies effectively (so that I'll only be running kubuntu-desktop (KDE))? If that's not possible, say that I want to install k3b at one point and then decide to remove it. How do I remove k3b along with all the dependencies it installed?

---

### Post by bored2k on 2005-05-06
[QUOTE=Gentist]I recently installed Ubuntu on one of my computers for testing purposes, and it went quite smooth all the way through the installation (with the exception of a few boot parameters).

Now, with the system up, I decided to apt-get kubuntu-desktop, since I prefer KDE over GNOME as a desktop environment (although I normally use a lightweight windowmanager instead). So... With KDE installed and fully functional, I decided to get rid of GNOME and everything that came with it. However, that wasn't as easy as installing it. First of all, I don't know which the main package for the GNOME install is, though I guess it is ubuntu-desktop. Secondly, "sudo apt-get remove <package>" does not take care of the dependencies.

Basically, I want to remove the original GNOME install and all of its dependencies which aren't used used by another package or installed by itself (much like Gentoo's "emerge depclean"). I have no idea how I should go about this, and I can't seem to find any documentation explaining this kind of uninstallation process, which I think is quite weird considering that you do not want unused dependencies and packages on your system normally.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster](http://ubuntuforums.org/showthread.php?t=24403&highlight=debfoster)
Debfoster is the way to go.

---

### Post by Gentist on 2005-05-06
Sounds nice, I'll give it a try as soon as I figure out how to activate the "unstable/insecure" packages.

EDIT: Thank you. Everything just became a lot more sensible. Now I might actually keep Ubuntu. :D

---

### Post by jodef on 2005-05-06
Debfoster looks interesting, just what I was looking for to keep my system clean.

---

### Post by Gentist on 2005-05-07
I decided to remove both ubuntu-desktop and kubuntu-desktop in favour for IceWM. Everything seem to run fine, with the exception of the graphical tools that came with Ubuntu. Synaptic, the package manager, does not run anymore. Supposedly the dependencies for it was removed. Since I plan to install Ubuntu together with (for example) IceWM on a couple of old computers for use by people who are not so tech-savvy, I'd like Synaptic to work.

I have two questions first. Which packages are required by Synaptic, and what package does Synaptic come with? I'm guessing that the latter is ubuntu-base, though in such case, why doesn't it have the appropriate dependencies?

This is what it spits out when I try to run Synaptic:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:8130): Gtk-WARNING **: cannot open display:
```

EDIT: Nevermind, I got it to work.

---

