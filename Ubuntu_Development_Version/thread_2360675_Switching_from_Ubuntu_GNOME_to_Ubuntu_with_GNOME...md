---
title: "Switching from Ubuntu GNOME to Ubuntu with GNOME..."
date: 2017-05-07
forum: Ubuntu Development Version
---

### Post by fthx on 2017-05-07
Hi,

I already use Ubuntu GNOME (ubuntu-gnome-desktop).
What should I do for now ? What meta-package should I use in the future ? ubuntu-desktop or ubuntu-gnome-desktop ?

---

### Post by corradoventu on 2017-05-07
Ubuntu Unity is becoming GNOME: on my Ubuntu Unity 17.10 last upgrades says: 
The following NEW packages will be installed:
  gcc-7-base [COLOR="#FF0000"]gnome-getting-started-docs gnome-user-guide[/COLOR] libvulkan1 linux-headers-4.10.0-21
  linux-headers-4.10.0-21-generic linux-image-4.10.0-21-generic
  linux-image-extra-4.10.0-21-generic linux-signed-image-4.10.0-21-generic xserver-xorg-legacy
if You look on Ubuntu Unity 17.10 17,10 help you will find: getting started with GNOME

---

### Post by kansasnoob on 2017-05-07
The change hasn't happened yet, but at some point in this cycle the dependencies will almost entirely change for 'ubuntu-desktop'. I suspect since Ubuntu GNOME is ending that all 'ubuntu-gnome' meta-packages will be dropped from the repos. Whatever you choose to "build" right now may not be truly representative of the final outcome.

---

