---
title: "Sticky: Installing new ubuntu 11.10 Oneiric"
date: 2011-11-03
forum: The Cafe
---

### Post by christophevr on 2011-11-03
Hello All ,

I like many users at first almost took off from my chair into the sky out of madness. In a second face followed the sadness. Yes it's trough, Many things just do not work att all anymore into the new ubuntu 11.10 at base. Once a cooled down a bit, started to google around and see what was the reason for such a disastrous version. The main problem is just because the use of the new gnome3 desktop and linux kernel 3.0.0.
This leads to tremendous changes in desktop handling and graphical interface. The gnome3 needs to be learned from scratch as if it was the first time you use linux. Ok you still can use a fall back shell to the old gnome2, that is well deprecated, and in future with next releases be gone completely. Ubuntu now did well a in my opinion not so smart move to set at default only the unity shell . The unity shell is indeed very restrained. Actually it's perhaps the optimum for a tablet pc, but absolutely unusable on a desktop or laptop. This last statement is my personal opinion. From side line it's always easy to give comments. I did well find out that it's not really ubuntu which must be blamed, It's the gnome which changed so drastically at base which is the cause of that. Unity was used by ubuntu to make the changes less dramatical, unfortunately it's so incomplete that it can be considered a very bad move for a lot off ubuntu users. This just to give some info about what's happening.

How to tweak ubuntu 11.10 so that You really can use it again.

First DO NOT DO NOT !!! upgrade your current working ubuntu. Make a full backup of your current working ubuntu first. (/etc included which needs to be done with sudo)
If You can install the new ubuntu 11.10 to a other HD or partition. If You do not have other HD or partition you will have to do a fresh install and remove Your current ubuntu version. Note that You will need several days to understand the new desktop, the basic ubuntu install is very limited (far to, to be a descent desktop/laptop os)

Download the .iso file or .. like usual.
Install with dvd (or ...) The ubuntu like You did before.
Once done login . First set Your network if that needs to be tweaked . Then just add extra drivers if needed for your graphic card.
Restart ubuntu. Upgrade now your full installation. restart ubuntu again.

Now we can start tweaking

Use ctrl+alt+t to open a terminal window.
issue in that terminal  ~$ sudo apt-get install gnome-shell gnome-system-tools gnome-tweak-tool synaptic dconf-tools

Close terminal restart ubuntu. This time during login we choose gnome (not ubuntu).

Now You have again a full working environment. It will take You a lot off time to learn using this new shell. Really everything is avbl like before it's just the way of work who changed.
Once You are used to this shell it's quit ok.

Some extra stuff.
The gnome-alsamixer (needs to be installed first) does not work in oneiric.
There is currently a new working version. It's only avbl in precise. You can download it and install later with dpkg. here the link to package.

[http://launchpadlibrarian.net/83939881/gnome-alsamixer_0.9.7%7Ecvs.20060916.ds.1-2.1ubuntu1_amd64.deb](http://launchpadlibrarian.net/83939881/gnome-alsamixer_0.9.7%7Ecvs.20060916.ds.1-2.1ubuntu1_amd64.deb)

You may as well check the full bug report around it which is :

[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/849415](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/849415)

Good luck :wink:

---

