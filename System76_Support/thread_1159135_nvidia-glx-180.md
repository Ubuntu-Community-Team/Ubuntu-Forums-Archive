---
title: "nvidia-glx-180"
date: 2009-05-14
forum: System76 Support
---

### Post by Lee_Machine on 2009-05-14
Any possible fix regarding the nvidia 180 bug, where just before shutdown the screen goes all white, pink, and purple?

Computer affected is Panp4n

I was hoping the S76 driver that came out a few days ago would do it.

Here is the bug report 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/329427](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/329427)

Anyway's from the gist of it only nvidia can fix it...that's closed source for ya. Also from what I have been reading nvidia is known to only jump on bugs that are critical.


On a last note there is an alternate known as Nouveau, and it is an open source alternative to nvidia's driver.

The driver was accepted in the Jaunty repos, but is still considered experimental, and not for wide use. 

Fedora 11 comes out soon and will feature the Nouveau driver by default. I'll test it out and let you guys know how well it works on the pangolin. 

Anyone that wants to test it out under ubuntu Jaunty here ya go

[http://packages.ubuntu.com/jaunty/xserver-xorg-video-nouveau](http://packages.ubuntu.com/jaunty/xserver-xorg-video-nouveau)

---

### Post by thomasaaron on 2009-05-14
I don't know of a way yet to fix the discoloration. If your computer fails to shut down while using that driver, though, you can run...

sudo apt-get install linux-backports-modules-jaunty

---

### Post by Lee_Machine on 2009-05-14
yep, i'm sure the next release of the driver accepted by ubuntu will have the fix.

Yeah the newest S76 driver installs the backports.

Thanks again,

---

### Post by flukeairwalker on 2009-05-15
Are you talking about this thing? It happens to me too but I never thought much about it since it doesn't seem to affect the shutdown negatively. Anything I can do to fix it?

---

### Post by Lee_Machine on 2009-05-16
From what I read over at Lauchpad no. It's an issue with the x.org and the nvidia 173 and 180 drivers. 

But that the blame is on nvidia...I've been trying a few things no dice so far. But if I find a fix I will make sure to post it here.

---

