---
title: "why do we have 2-3 version of xorg one is enough"
date: 2013-09-15
forum: Ubuntu, Linux and OS Chat
---

### Post by josephdavidrich115 on 2013-09-15
[ATTACH=CONFIG]246262[/ATTACH]  

guy are we trying to confuse users or make it easy as this is ridiculous one version NOT MILLIONS 12.04 xorg is <snip> sort it out please if you work for canonical with the desktop environment side sort it out I don't see other distro making this mistake so why this one :confused:

---

### Post by tgalati4 on 2013-09-15
You might have a PPA that points to a different version.  So you have the default xorg version and the PPA version and the pieces required for proprietary ATI graphics cards.  It's a bit of a mess, but then graphics have always been a mess in linux.

---

### Post by kostkon on 2013-09-15
It's because of [this]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

---

### Post by cariboo on 2013-09-16
The only confusion is your own. I you choose to stick with 12.04, you keep the same xorg-server. If you choose to install the point release, then you get the newer xorg-server.

You could also say the same thing about the kernel, 12.04 uses the 3.2 kernel, and 12.04.1+ uses the 3.5 kerenl

To install the point releases, you have to purposely do an dist-upgrade, or do a fresh install. 

The average new user, isn't going to use synaptic, they are going to stick with the Software Centre, and Update manager for all their needs, and unless they are computer enthusiast, they won't even be aware of the point releases

---

### Post by josephdavidrich115 on 2013-09-16
it still completely pointless if you cannot get xorg right I don't think your get mir right

---

### Post by josephdavidrich115 on 2013-09-16
nope this what comes on default for 12.04

---

### Post by deadflowr on 2013-09-16
> **josephdavidrich115 said:**
> it still completely pointless if you cannot get xorg right I don't think your get mir right

How so?

Production environments can't depend on a rolling X stack.
And newer hardware wouldn't be supported on the older X stack.
The solution, per LTS are point releases, which offer upgraded X and kernels which will run on newer systems.

However, the envionments which can't be messed around with, can keep using the old stacks without problems.
It's well explain in the link kostkon provided.

---

### Post by deadflowr on 2013-09-16
> **josephdavidrich115 said:**
> nope this what comes on default for 12.04

What do you mean?

depending on which version of 12.04 you installed, you will either have xserver-xorg installed, or xserver-xorg-lts-quantal installed, or xserver-xorg-lts-raring installed.(I'm using xserver-xorg as a generic catchall for all the various xorg packages.)
But you don't and won't have all three installed.

However, they are all available in the repositories.

---

### Post by grahammechanical on 2013-09-18
> [COLOR=#000000]it still completely pointless if you cannot get xorg right I don't think your get mir right[/COLOR]

The Ubuntu developers are not responsible for xorg. Actually xorg is X organisation.

[http://www.x.org/wiki/](http://www.x.org/wiki/)

So, if anyone is not getting X11 right it is the X.org Foundation and you should take your complaint to them. The X11 code is open source. This means that the Ubuntu developers can take the X11 code and patch it so that the Xserver works on different graphic hardware and with proprietary video drivers as well as open source video drivers.

If you think that xorg is not right then you should support the development of MIR as a replacement to X11. That there is a need to replace X11 is seen by the fact that something known as Wayland/Weston is being developed. So, why do the Ubuntu developers not want to use the Wayland protocol? 

[https://wiki.ubuntu.com/Mir/Spec](https://wiki.ubuntu.com/Mir/Spec)

The developers do not think that either X or Wayland are suitable for Ubuntu on phones and tablets. And the developers have taken things a step further. First there will be MIR on Ubuntu phones and tablets and then there will be MIR on Ubuntu desktops. As a step towards this we have Xmir which replaces the Xserver. This will be the default installation of 13.10 using the open source video drivers.

I have been using Ubuntu 13.10+xmir for weeks. I cannot tell the difference between an install of 13.10 running on xmir and an install of 13.10 running on xserver. And neither will you if you try it out. Here are the results of an independent comparison of Xmir against Xserver. Out of 26 tests Xmir performed as well as, if not better than Xserver in 13 of the tests.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_saucy_mesa92&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_saucy_mesa92&num=1)

The Ubuntu platform for mobile devices is called Ubuntu Touch and it is already running on MIR on mobile devices.

Regards.

---

