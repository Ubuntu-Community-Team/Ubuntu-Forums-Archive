---
title: "Xen with VGA passthrough"
date: 2013-05-07
forum: Virtualisation
---

### Post by heiko_s on 2013-05-07
Not sure this is the right place to post, but if you are interested in trying Xen with VGA passthrough, have a look at this: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013").

The how-to uses Linux Mint, which is based on Ubuntu. It should be easier to accomplish using Ubuntu, since Ubuntu has LVM support from within the installer.

Feedback is welcome. If necessary, I may modify the how-to for Ubuntu and post it on the Ubuntu forum.

Given the right hardware, VGA passthrough is real cool. My Windows 7 VM feels like running on native hardware. Here a benchmark:

[IMG]http://www.pbase.com/merhav/image/149363639/original.jpg[/IMG]

My graphics card is a bit weak, though. Not meant for gaming.

Other alternatives are kvm, which is developing fast. kvm will probably require a 3.9 kernel for VGA passthrough to work nicely (even with some Nvidia cards), so kernel compilation may be necessary. This how-to may help: [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787").

---

