---
title: "Which part of Ubuntu is done by Ubuntu"
date: 2007-09-27
forum: The Cafe
---

### Post by jethro10 on 2007-09-27
Hi,
Now I dont want to start a rant, i'm an ubuntu fanboy, been with it coming on 2 years now, and have installed 2 servers at work with it on and it's working fab.

But I find it hard to understand which parts of Ubuntu are done by them.
Gnome is update, gimp, OOo, etc all by their respective teams. Ubuntu just collates these really.

So where do I find ubuntu stuff, apart from artwork and colour schemes.

And how much of it feeds back upstream to add new features to already existing products?

and ideas?

Ta
Jeff

---

### Post by bonzodog on 2007-09-27
Well, thats just it you see. In reality, a linux Distribution is more or less a collection of programs brought together by the developers who get to choose what goes in or out. Almost none of Ubuntu is actually written by the Ubuntu Developers at Canonical, the only addtions that make Ubuntu unique to any other linux distribution are the Artwork/Icons and sounds.

A lot of the Ubuntu developers are also Gnome Developers, so ubuntu is having a huge impact on Gnome's development. For instance, it was an ubuntu Developer that wrote the Network Manager Applet.

---

### Post by Johnsie on 2007-09-27
Alot of the bug fixing and feature implementation is done over at [http://launchpad.net](http://launchpad.net)

Have a look on there and you will see some of the things that "Ubuntu" are doing.

---

### Post by jethro10 on 2007-09-27
> **Johnsie said:**
> Alot of the bug fixing and feature implementation is done over at [http://launchpad.net](http://launchpad.net)

Have a look on there and you will see some of the things that "Ubuntu" are doing.

Ah,
so as Ubuntu fixes debian errors (and send the fixes back?, hopefully) a better ubuntu may be something based on ubuntu like mint?

J

---

### Post by Johnsie on 2007-09-27
double post

---

### Post by Johnsie on 2007-09-27
Possibly, if Mint fix anything in Ubuntu then yes.It simply depends on your tastes or what you want from an OS.

---

### Post by 23meg on 2007-09-27
Upstart, Usplash, Ubiquity, Restricted Drivers Manager and Apport are the products that come to my mind at the moment. Ubiquity was based on the Guadalinex installer, but has improved on it a lot.

---

### Post by mostwanted on 2007-09-27
Add/Remove... is also an Ubuntu in-house program. Some of the included programs were also originally done by the greater Ubuntu community specifically for Ubuntu (such as the menu editor which is now officially a part of Gnome too).

Ubuntu also patches almost every important package to make it fit in better. Firefox is patched to provide better Gnome integration (and next month, when 7.10 is out, APT too). Gnome itself is patched in several areas (log-off menu, Appearance Preferences for example). Gnome's look is customised as well. The kernel is also a specific Ubuntu kernel with applied patches.

You will find that if you *apt-get source* programs you will download a package containing pre-patch (called *vanilla*) source and a package containg the offical patched source which the Ubuntu package is built from.

---

### Post by Anthem on 2007-09-27
A lot of the modular X stuff was done by Stone while he worked for Ubuntu.

NetworkManager, though was from RedHat.

---

