---
title: "Can you install Ubuntu with LXDE instead of Gnome like this?"
date: 2009-05-19
forum: The Cafe
---

### Post by gymophett on 2009-05-19
> 
Download the alternative CD, and press F4 at the boot menu, then select "Install command line system", then after it's installed, install your preferred desktop environment (i use LXDE on mine, sudo apt-get install lxde), and you've got a nice Ubuntu desktop system in about 1/3 or less of the space and using heaps less resources.

Will that work? If it does, will I still have Pidgin, OpenOffice, Firefox, and everything preinstalled? Or is there a better way to do this? Should I install 9.04, then LXDE, then remove Gnome or what? Please help. I've had problems removing Gnome and such. I'm doing a fresh install now, so what is the best way?

---

### Post by Bodsda on 2009-05-19
> **gymophett said:**
> Will that work? If it does, will I still have Pidgin, OpenOffice, Firefox, and everything preinstalled? Or is there a better way to do this? Should I install 9.04, then LXDE, then remove Gnome or what? Please help. I've had problems removing Gnome and such. I'm doing a fresh install now, so what is the best way?

Im not certain, but I would have thought a command line system would not include X or video drivers etc. which means first you would have to set up your internet connection via cli and then install and configure the x window system then install your desktop environment and then pray that it works

---

### Post by Saint Angeles on 2009-05-19
> **Bodsda said:**
> Im not certain, but I would have thought a command line system would not include X or video drivers etc. which means first you would have to set up your internet connection via cli and then install and configure the x window system then install your desktop environment and then pray that it works
i would hope that any DE would DEPEND on X... but im not sure if they do.

---

### Post by Bodsda on 2009-05-19
> **Saint Angeles said:**
> i would hope that any DE would DEPEND on X... but im not sure if they do.

Not directly

```
bod@bod:~$ apt-cache show kde-core
Package: kde-core
Priority: optional
Section: kde
Installed-Size: 40
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: all
Source: meta-kde
Version: 5:48ubuntu1
Depends: kdelibs5 (>= 4:4.1.1), kdebase-runtime (>= 4:4.1.1), kdebase-workspace (>= 4:4.1.1)
Suggests: kde-l10n (>= 4:4.1.1)
Filename: pool/main/m/meta-kde/kde-core_48ubuntu1_all.deb
Size: 8044
MD5sum: 07116346e0a484c46d5ab657a4c9841b
SHA1: 18c0d831046978b7194d27e49f67c6ea53b3e273
SHA256: 0c23aa7d0bbfee51868251ea44176cc48f3b4d4a398d9e03aac792e519356a6a
Description: the K Desktop Environment core modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
 desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the
 technological superiority of the Unix operating system.
 .
 This metapackage includes the core official modules released with KDE. This
 includes just the basic desktop (browser, file manager, text editor, control
 center, panel, etc.) and important libraries and data.
Homepage: http://www.kde.org
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

### Post by XubuRoxMySox on 2009-05-19
You can use Synaptic to install LXDE from the Ubuntu repositories and purge the Ubuntu desktop:

```
sudo apt-get purge ubuntu-desktop
```

But if it's a nice "Ubuntu Lite" you're looking for, I recommend the uber-lightweight Ubuntu-based [Crunchbang Linux]("http://crunchbanglinux.org"). I added LXDE to mine and it's pretty much trouble free as along as you let PCMan manage the desktop.

The Crunchbang/LXDE combination is super lightweight, super-simple and newbie friendly.

Crunchbang has no desktop environment at all. There's nothing to "click on," so it's kinda freaky for a newbie at first sight, but don't worry! Just *right*-click the desktop and a whole menu magically appears out of the darkness. You can select Synaptic, install LXDE (Crunchbang uses Ubuntu's repositories), and log out. Choose LXDE from the Options menu when you log back in and make it the default.

Applications are found in /usr/share/applications and appear as icons! Just drag and drop the ones you want right to your desktop.

Add your favorite wicked-kewl wallpapers to usr/share/lxde/wallpapers and select your favorite from Edit>Preferences in PCMan.

It's awesome, newbie friendly uber-lightweight Ubuntu! 

-Robin

---

### Post by mkvnmtr on 2009-05-19
I have used the Ubuntu minimal install disk several times. It is about 10 Mb and you get a command line install. You can then install ldxe for a desktop. You do of course need to install everything else you need or want. It seems to come with a internet connection set up because you have to download everything. You might google Ubuntu minimal install. Right at the top there are several pages that will explain how to do it and install the desktop of your choice.

---

### Post by albinootje on 2009-05-19
> **dixiedancer said:**
> You can use Synaptic to install LXDE from the Ubuntu repositories and purge the Ubuntu desktop:

```
sudo apt-get purge ubuntu-desktop
```


The ubuntu-desktop package is just a meta-package.
It is normally needed for a proper Ubuntu release upgrade.
Removing it is not gonna remove the whole Ubuntu desktop software.

The OP might want to look here : [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) at the "Playing Around" section.

---

### Post by gn2 on 2009-05-19
Yes, that will work.
Youll need more than just Lxde though, you'll need to add the applications yourself.

After the installation of the command line system, the following should be enough to get you going with a working Lxde GUI:

```
sudo apt-get install xorg gdm lxde synaptic
```

Once that lot is installed type: startx

Then install the applications you want either with CLI apt-get or with Synaptic.

---

### Post by Warpnow on 2009-05-19
> **gn2 said:**
> Yes, that will work.
Youll need more than just Lxde though, you'll need to add the applications yourself.

After the installation of the command line system, the following should be enough to get you going with a working Lxde GUI:

```
sudo apt-get install xorg gdm lxde synaptic
```

Once that lot is installed type: startx

Then install the applications you want either with CLI apt-get or with Synaptic.

Apt-getting lxde will install gdm and xorg automatically. I did this only a couple days ago, so startx isn't necessary.

'sudo apt-get install lxde' will install gdm, xorg, and everything else you need.

---

### Post by gn2 on 2009-05-20
> **Warpnow said:**
> Apt-getting lxde will install gdm and xorg automatically. 

Well I've just learnt something, which is great. :)

> **Warpnow said:**
> I did this only a couple days ago, so startx isn't necessary.

How do you get from a CLI session command prompt to a GUI desktop without starting x?

---

### Post by Sublime Porte on 2009-05-20
Yes it will work, but you will need a working internet connection as mentioned. But that is not too hard to figure out.

Installing LXDE will install all it's requirements, which includes X and so forth. Installing Pidgin, Firefox etc. is very easy (easier than installing LXDE) so don't worry too much about that. The good thing is you can install just the components you want, instead of all the default stuff that comes with ubuntu.

> How do you get from a CLI session command prompt to a GUI desktop without starting x?

Like this: sudo reboot (so long as gdm was installed)

---

### Post by albinootje on 2009-05-20
> **gn2 said:**
>  How do you get from a CLI session command prompt to a GUI desktop without starting x?

Without using "startx" ? /etc/init.d/gdm restart is an option.
I guess you mean from the "recovery mode" root prompt.
Then "init 2" is an option to boot into "normal" mode.

---

### Post by Warpnow on 2009-05-20
> **albinootje said:**
> Without using "startx" ? /etc/init.d/gdm restart is an option.
I guess you mean from the "recovery mode" root prompt.
Then "init 2" is an option to boot into "normal" mode.


Or your press that shiny button on the front of your PC that turns it off, then push it again for power. :-p

---

### Post by Skripka on 2009-05-20
Ubuntu LXDE edition:

[http://grubbn.org/forum/showthread.php?tid=418](http://grubbn.org/forum/showthread.php?tid=418)

---

### Post by cmay on 2009-05-20
[[IMG]http://gemdet.nu/thumb-3D13_4A11C8A4.jpg[/IMG]]("http://gemdet.nu/share-3D13_4A11C8A4.html")

here is a screenshot of my lxde on ubuntu . i cheat a bit and use openbox also.
how i do is either install lxde and openbox and then start to chop of gnome.

a better idea is to get the minimal install iso and build it your self. 
that is uncheck all when running tasksel and then when you log in install xorg and lxde whihc should drag in lxdecore at least as a depencie. otherwise just install lxde-core. 

the you pick what you want of programs and reboot. 

lxde is far more fast that any other windows manager i been using and its more easy to work with than openbox or jwm i think. i use openbox and lxde toghter and sometimes keep gnome also because when i go to forums and see questions and i cant remember how gnome is looking like i can at least log in to a gnome session.

---

### Post by Warpnow on 2009-05-20
> **Skripka said:**
> Ubuntu LXDE edition:

[http://grubbn.org/forum/showthread.php?tid=418](http://grubbn.org/forum/showthread.php?tid=418)

Ligthweight window manager, but the applications included are heavy as hell. I find that odd.

---

### Post by Skripka on 2009-05-20
> **Warpnow said:**
> Ligthweight window manager, but the applications included are heavy as hell. I find that odd.

It is...OTOH, they are the standards.  Most folks running Ubuntu don't use Links as their browser. ;)

---

### Post by Warpnow on 2009-05-20
> **Skripka said:**
> It is...OTOH, they are the standards.  Most folks running Ubuntu don't use Links as their browser. ;)

Most people running ubuntu don't run LXDE either. :-p

I didn't suggest links, but Firefox is very heavy. A system that benefits from LXDE the most is likely to be crippled by it. Epiphany-webkit, Midori, Opera, these are browsers that are at least a little lightweight.

And obviously...openoffice? Can we even say abiword?

---

### Post by XubuRoxMySox on 2009-05-20
I made my own very lightweight, very speedy LXDE version of Ubuntu Jaunty simply by installing [Crunchbang]("http://crunchbanglinux.org") and adding LXDE to it! There's really no need for a whole 'nother "Ubuntu Lite" distro at all.

I know they're working on "Lubuntu," but I fear that in their efforts to make it newbie-friendly, it will quickly become as bloated and heavy as Xubuntu has turned out to be.

Crunchbang is a very minimal Ubuntu installation with no desktop environment at all. Adding LXDE adds almost no "weight" to Crunchbang and is in keeping with it's purpose of running well on older hardware.

-Robin

---

### Post by gn2 on 2009-05-20
> **Sublime Porte said:**
> Like this: sudo reboot (so long as gdm was installed)

No need to reboot.

> **albinootje said:**
> Without using "startx" ? /etc/init.d/gdm restart is an option.
I guess you mean from the "recovery mode" root prompt.
Then "init 2" is an option to boot into "normal" mode.

No I mean immediately after installing a CLI system then adding Lxde, just type startx and you're straight into a GUI.

> **Warpnow said:**
> Or your press that shiny button on the front of your PC that turns it off, then push it again for power. :-p

No need to switch off.
My PC has a reset button which also does the job ;)

---

