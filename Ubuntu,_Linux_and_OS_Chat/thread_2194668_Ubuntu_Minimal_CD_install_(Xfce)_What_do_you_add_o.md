---
title: "Ubuntu Minimal CD install (Xfce) What do you add on to it?"
date: 2013-12-19
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2013-12-19
My first Ubuntu *Minimal CD*  install. (13.10)

xfce4, xfce4-goodies, gdm, xorg

synaptic, gufw, gparted, that's all for now.

What do you add to yours?

Thanks, for the ideas.

---

### Post by Irihapeti on 2013-12-19
It depends very much on what you're going to use it for. Usually the first things I add are a browser, image viewer, geany (not necessary if you're happy with mousepad/leafpad), media player, CUPS if I'm going to be printing, bluetooth if I need it to talk to bluetooth devices (usually do) and nm-applet. I tend to use the --no-install-recommends setting so that a whole lot of extra stuff doesn't get pulled in.

I usually install some word processing/spreadsheet software as well. I happen to prefer OpenOffice, but of course there are other options. That's why I like doing minimal installs - what I add afterwards is my own choice rather than someone else's. (And you learn a lot about the system when things don't quite work the way you thought they would. :) )

---

### Post by vasa1 on 2013-12-20
> I tend to use the --no-recommends setting so that a whole lot of extra stuff doesn't get pulled in.^ Shouldn't that be --no-install-recommends ?

---

### Post by Irihapeti on 2013-12-20
> **vasa1 said:**
> ^ Shouldn't that be --no-install-recommends ?

Thanks, you're right. :oops: I've corrected the previous post.

Synaptic can also be set not to install recommended packages as dependencies.

---

### Post by DuckHook on 2013-12-20
When I go minimal, I'm going pure command-line. This may not be what you are looking for, but if it is, then:

mc
htop
iotop
iftop
fbterm
screen
byobu
aptitude
links2
fbi
mutt
sc
wordgrinder
rtorrent
nfs-common
autofs
usbmount
cups

It appears that you are going GUI, so most of these packages are superfluous or pointless. But you may still find a few of them useful, especially *autofs*.

---

### Post by mikodo on 2013-12-20
Thanks, for the suggestions everyone.

Yes, DuckHook you are right. I need a Gui.

---

