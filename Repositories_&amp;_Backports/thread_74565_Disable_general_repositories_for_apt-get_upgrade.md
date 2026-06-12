---
title: "Disable general repositories for apt-get upgrade"
date: 2005-10-12
forum: Repositories &amp; Backports
---

### Post by nick4mony on 2005-10-12
Hi.
I am on a dialup connection, and I would like to limit the download to the bare security-related essentials when I
   # apt-get update
   # apt-get upgrade

However, if I then say
   # apt-get install xfce-...
(or whatever software I want), I would like to actually get that software no matter which repository it is located.

==============
Questions:
 1. How do I organise the sources.list file (and/or other config files)
 2. How would this change to use mirrors in Australia (although don't use a mirror for security).
==============

BTW: I do like Ubuntu, although there's quite a few things I need that aren't in the box (xfce, named[dns], lilo-doc, apache2-doc, ...)

An example sources.list file, with an idea of what I like to achieve, in a comment tagged '###'
-----start of sources.list-------------
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

[color=blue]**### DO NOT USE REPOSITORIES BELOW FOR apt-get upgrade**[/color]
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse
```
-----end of sources.list-----

---

### Post by manicka on 2005-10-12
I believe what your asking for in the first part isn't possible.

There is a list of ubuntu mirrors here
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

### Post by lerrup on 2005-10-12
well you could use synaptic and just untick the boxes you don't want to use for updates and then reinstate when you want to install.

ALternativeely use the # key in a text editor or switch 2 lists manually.  that would do what you want.

---

### Post by UbuWu on 2005-10-12
There are very few updates besides security updates, so I don't really understand what the problem is.

---

### Post by nick4mony on 2005-10-12
[QUOTE=UbuWu]There are very few updates besides security updates, so I don't really understand what the problem is.[/QUOTE]

It will be a different story when I switch to Breezy in a few days time (no?)

---

### Post by nick4mony on 2005-10-14
Thanks very much for the answers.  To get what I'm after, I'll use the option for the alternative sources.list file when I'm 'installing' something.

---

