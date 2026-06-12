---
title: "Installing Gnome 3 on Ubuntu 12.04"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Svante65 on 2012-04-04
Which way is the right way is to install Gnome 3 on Ubuntu 12.04?
I see many different ways on the Internet. Some with and some without extra ppa's. And some with installing different packages.
And what about extensions? How do you access as many as possible?

---

### Post by kurt18947 on 2012-04-04
I don't know if it's right or not but I just installed 'gnome-shell' using Synaptic.  "gnome-tweak-tools" is pretty much required IMO.  The page "extensions.gnome.org" run in FireFox works very well for installing extensions.  The thing right now is that Precise is using gnome 3.4.0 and many of the useful extensions are written for gnome 3.2.2.1. There are a number of shell extensions shown in Synaptic & presumably in Ubuntu Software center but use caution. I know at least one extension in Synaptic, "gnome-shell-extensions-extended-places-menu" will not create the desktop when installed, I just had a blank screen.  The extensions I've installed  from 'extensions.gnome.org' do work.

---

### Post by Perfect Storm on 2012-04-04
Moved to Ubuntu +1

My advice:
To install Gnome Shell;
```
sudo apt-get install gnome-shell gnome-theme-standard gnome-tweak-tool gnome-contacts gnome-sushi dconf-tools
```

If you want the most extensions to work with Gnome Shell 3.4 I'll suggest PPA: [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu)
As most of the extensions on gnome extensions site is not updated for Gnome Shell 3.4.




To uninstall Unity completely and run Gnome Shell only:
```
sudo apt-get purge appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu
 unity-lens-music unity-lens-applications unity-greeter unity-common unity-asset-pool unity-2d-launcher unity-2d libunity-misc4 libunity-2d-private0 gir1.2-unity-4.0 liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar appmenu-gtk appmenu-gtk3 appmenu-qt indicator-appmenu compiz compiz-plugins-main-default libcompizconfig0 
sudo apt-get purge lightdm
sudo apt-get install lightdm
```

**Advisable**: removing all local config files/folders/other local settings from "home" users. (I couldn't get Gnome Shell starting without doing this step at current state.

If you want to remove qt libs that are related to unity and other ubuntu applications:
```
sudo apt-get remove libqt4*
```

**Note:** if you have applications like vlc, ubuntuone and other qt depended. they will uninstalled as well.

---

### Post by dino99 on 2012-04-04
> **Svante65 said:**
> Which way is the right way is to install Gnome 3 on Ubuntu 12.04?
I see many different ways on the Internet. Some with and some without extra ppa's. And some with installing different packages.
And what about extensions? How do you access as many as possible?

Gnome 3.4 is actually installed by default on Precise. (so may have watch outdated posts on the net)

---

### Post by jbicha on 2012-04-04
To clarify, GNOME Shell is definitely not installed by default. Unity uses GTK3 and the Ubuntu default install includes many GNOME 3.4 apps and libraries.

---

### Post by keithpeter on 2012-04-04
> **Artificial Intelligence said:**
> 
Moved to Ubuntu +1

To uninstall Unity completely and run Gnome Shell only:
```
sudo apt-get purge /* loads of stuff */ 
```


Hello Artificial Intelligence and all

I've done this the other way round as a testing project.

I installed a command line Ubuntu 12.04 using the netinstall iso, then just installed the gnome-core package which brought down gdm, mutter, shell, synaptic, and epiphany. From there, I built up to a desktop with the usual suspects. Seems stable (Shell crashes now and again but restarts itself). I did see a few unity library files in the apt-get output.

Is approach this advisable? Didn't want Evolution so avoided the full gnome desktop package.

---

