---
title: "What is the smallest linux that can be used as Vbox host?"
date: 2010-02-07
forum: Virtualisation
---

### Post by C.S.Cameron on 2010-02-07
I have installed XP on a thumbdrive but it is very very very slow.
It is much slower than running XP in Vbox on an Ubuntu host from pendrive.
It seems to work ok even from a "persistent", image install.

I am looking for the smallest install, that will run Vbox but still have the necessary drivers required for plugging the pendrive into random PCs.

I don't need OOO etc.

---

### Post by mkvnmtr on 2010-02-07
I have a minimal Ubuntu install with LXDE for a desktop. It is about 1.5 Gb. I uninstalled everything I did not want that was installed with the packages. It is light and fast. I use it for something else but I am thinking about seting up a machine to run several distros in boxes and I velieve I will use something similar for the host.

---

### Post by x33a on 2010-02-07
You can try puppy linux, or slitaz. both are extremely light weight.

---

### Post by C.S.Cameron on 2010-02-07
Thanks Mkvnmtr:
I would prefer something *buntu but am now playing with NimbleX.
The version that comes with Vbox is 200MB.
I have not installed it to a flashdrive yet but it looks sort of interesting running in VirtualBox.

So how do I get Minimal Ubuntu?
Every time I get interested in a minimal install I end up downloading mini.iso which never completes an install for me.

---

### Post by C.S.Cameron on 2010-02-07
Does Puppy or Slitaz support Virtual box? I've been trying to find out how to install in DSL but can't find any method within my skill range.

---

### Post by x33a on 2010-02-07
I haven't tried puppy with virtualbox, but take a look here:

[http://puppylinux.org/news/puplets/puppy-linux-in-virtual-machine/](http://puppylinux.org/news/puplets/puppy-linux-in-virtual-machine/)

---

### Post by mkvnmtr on 2010-02-08
The minimal install will depend on your internet connection. The disk is only about 12mb and downloads everything from the repositories. You wind up with a command line base and then can add the programs you need. Without a good internet connection it will take a long time.
As for Puppy I have used it as a guest but I do not think it would make a good host.
I agree that a Ubuntu base is the easiest to work with. That is why I like LXDE. The XFCE desktop would work fine also. Not Xubuntu just XFCE4. Xbuntu is kind of heavy.
On my computer LXDE uses less resources than XFCE. Not by much.
 Another option I have tried is PCLinux with the LXDE desktop. A very nice distro but not using deb files. It seems a little harder to add wierd programs that are not in the repositories.

---

### Post by C.S.Cameron on 2010-03-10
I am trying NimbleX now. 
It is under 200 MB and comes with Vbox.
It comes with a Live USB installer but I had a bit of a hassle getting it to work on a flash drive.
It is working good for me now.

---

### Post by memilanuk on 2010-03-13
I'd be very interested in hearing more feedback on NimbleX or similar solutions... looks kinda cool!

---

### Post by juancarlospaco on 2010-03-13
*Ubuntu minimal CD is 12Mb*

---

### Post by jukingeo on 2010-03-19
> **juancarlospaco said:**
> *Ubuntu minimal CD is 12Mb*

I know that this has probably been discussed often but I figured I would hop on board as well.

I am looking to set up an emulation system for a friend that is specifically designed to play emulators only...thus the system would be playing games for MAME (Arcade games), Atari 7800/2600, Super NES, Sega Genesis....well you get the idea.

The thing is that I come across Pentium III and older Pentium 4 computers (between 300mhz and 2gighz) all the time.   So I was looking for something really lightweight and can install .deb files.

The lightest weight Linux distribution I have used to date is Puppy Linux.  This distribution is so small I could run it from a USB memory stick (pen drive).   But it has an inherent problem, it doesn't handle .deb files because it is a slackware based system.

So that bounces me back to Ubuntu, or should I say Xubuntu.    However, I been hearing that Xubuntu isn't as light as they say it is.  While I like the idea of an entire system on a pen drive that isn't my primary goal.

I did some reading up on Xubuntu and it comes with the Xfce desktop environment.  However, lately I have been reading up on another lightweight desktop environment called LXDE.

So this is my question.  Which desktop environment is faster?  Xfce or LXDE?

Overall, all I need is a distribution that can go on the internet, it can play sound, support controllers and handle installation of .deb files.  With those requirements satisfied, I should be able to easily pull off my project.

Thank You,

Geo

---

### Post by honeybear on 2011-03-14
> **mkvnmtr said:**
> I have a minimal Ubuntu install with LXDE for a desktop. It is about 1.5 Gb. I uninstalled everything I did not want that was installed with the packages. It is light and fast. I use it for something else but I am thinking about seting up a machine to run several distros in boxes and I velieve I will use something similar for the host.

I guess that there is certainly even lighter than this ...

---

### Post by jukingeo on 2011-03-17
> **honeybear said:**
> I guess that there is certainly even lighter than this ...

Yeah, that LXDE desktop I was talking about?  Well it is now part of a full Ubuntu based lightweight distribution called Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

Enyoy!

---

