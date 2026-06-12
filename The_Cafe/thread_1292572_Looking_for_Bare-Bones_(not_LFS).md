---
title: "Looking for Bare-Bones (not LFS)"
date: 2009-10-16
forum: The Cafe
---

### Post by CTDaemon on 2009-10-16
I saw another post concerning a Bare-bones Linux system, but it didn't answer my question, so I want to give some details about what specifically I'm searching for:
I want a basic Linux, with only the kernel, the bare necessities to boot up, a simple GUI, networking, and a command line. No programs, no add-ons, except for something to help me with managing packages & working with basics. I want this because I don't want to have a bunch of programs & packages I never use, and I want the freedom to modify my system completely as I please. I have some experience using the command line, but I don't know how to use the Terminal for things such as scripts (as used in LFS) or Bash... As well, LFS is, to my knowledge outdated. Thanks for your help and any advice you can give me.

If possible, I would also like to know the best software sources. And is it possible to use sources from multiple distributions, or can you only use one? I never understood how each distro is related/ separate from the others... (Linux n00b, obviously)](*,)

---

### Post by Xatolos on 2009-10-16
Ok.... sounds like your looking for a Linux that holds the least amount of space on the HD. If thats the case I might suggest you look at Damn Small Linux [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) which is like 50 megs total.
Sorry I've never used it though but I hope that helps you in your search.

---

### Post by earthpigg on 2009-10-16
ubuntu command line only install, and then install gdm and openbox.

sudo apt-get install gdm openbox



i think that should satisfy your needs.

---

### Post by juancarlospaco on 2009-10-16
Use the minimal install *(9Mb .iso)*, and compile using the sources*(not the packages)*

:)

---

### Post by earthpigg on 2009-10-16
(by the time you get X and a window manager, you will be VERY far from 'bare bones', FYI.)

as for software sources:

1) take a look here: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

2) source code is source code. you can compile it yourself and install it directly from the program's sourceforge or similar website -- but a .deb PACKAGE contains nifty things like handy install scripts and dependancies. you wont get that compiling yourself.

3) take a look here, too: [http://en.wikipedia.org/wiki/Alien_(software](http://en.wikipedia.org/wiki/Alien_(software)) .... but not all packages have the same features! this may be hit or miss, im not sure. ive never used it so i cant speak for its quality and reliability.

---

### Post by schauerlich on 2009-10-16
If you don't mind learning the *BSD way of things, installing FreeBSD with the X-User distro enabled will get you something similar to what you want.

---

### Post by Icehuck on 2009-10-16
Arch and Slackware are very good choices for bare bones and you will learn a few things as you go. You can get all the software you want for either of the two and if you really need something you can compile from source.

In slackware you are responsible for your own dependencies but with this you never get anything you don't need. Arch's package manager is pretty slick as well.

---

### Post by CTDaemon on 2009-10-17
Thanks for all these great ideas. By far, my favorite is the CLI-only and adding the basic GUI interface, its perfect. Thanks, and I'll be sure to try out all these ideas. Also, if anyone has a list of the bare necessities to get a system booted and run smoothly (the libs, packages, etc.), please email this list to me. I know it might be a long one, but I just want to be "in-the-know" so I can hopefully one day make a custom Linux distro myself. I love Ubuntu! (And I feel "happy"...)

---

### Post by xuCGC002 on 2009-10-17
Oh, another small distro is [Tinycore]("http://tinycorelinux.com/"), if you're interested.

---

### Post by RATM_Owns on 2009-10-17
> **earthpigg said:**
> ubuntu command line only install, and then install gdm and openbox.

sudo apt-get install gdm openbox



i think that should satisfy your needs.
Gdm. Too heavy.

Just put "exec openbox" in ~/.xinitrc.

Or use SLiM.

---

### Post by ugm6hr on 2009-10-17
Don't know how "simple" a GUI you want, but if you want Gnome:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

