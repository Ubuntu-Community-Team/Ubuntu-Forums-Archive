---
title: "Kdenlive repo question"
date: 2009-07-11
forum: Ubuntu Studio
---

### Post by Bartender on 2009-07-11
After following the instructions for getting the latest version of kdenlive
[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)

I keep getting this error (attached) when reloading Synaptic. I can click on thru and there doesn't seem to be any ill effect.

I'm not really comfortable with repos and keys and etc. but pretty sure I did it right.  kdenlive is installed and appears to be working.  Can someone tell me how to fix this?  Maybe it's something I'll have to put up with unless I uninstall the kdenlive entry in Software Sources?

Thanks!

P.S.  I just unchecked the entry that was added to Software Sources to get kdenlive and asked it to reload.  The error message did not come up, so it's definitely the sunab/ppa entry.

---

### Post by philip5 on 2009-07-12
It mean that you don't have the signing key from that PPA kdenlive repo added to apt so it can verify that the PPA packages are authentic from the PPA owner.

I also have (among a bunch of other updated packages) the latest 0.7.5 version (for the moment) of Kdenlive 0.7.5 and version 0.4.4 of the MLT engine for it on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try. In my FAQ you can read how to add my key to verify my packages.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Otherwise I think that NLE video apps in the open source arena is far behind what can be found on Windows and even OS X. If you are serious about NLE video apps then you should look at Shake ([http://www.apple.com/shake](http://www.apple.com/shake)) that Apple have bought for some time ago but is available for Linux too. It's neither free or open source but rather expensive that high end NLE video apps tend to be...

Anyway have fun with Kdenlive!

---

