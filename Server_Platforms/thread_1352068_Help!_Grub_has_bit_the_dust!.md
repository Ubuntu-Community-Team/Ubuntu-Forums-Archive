---
title: "Help! Grub has bit the dust!"
date: 2009-12-11
forum: Server Platforms
---

### Post by Xiuh on 2009-12-11
It appears I've ran into this [Bug #462961]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/462961") that affected Grub setup when placed in a boot partitioning apart from root with an older version of it. I haven't worked much with Grub and in fact, in 9.10 I just started using lvs partitioning. Unfortunately, that really hasn't prepared me for this. I just installed a Linux dist image update and went to examine my menu.lst in the grub folder....Nowhere to be found.

I guess my initial hopes was finding someone that might of lost their menu.lst. In my case I'm guessing that grub failed to even get setup due to the UUID mixup, similar to what was described in the above bug report.

Funny enough, I hadn't even noticed this problem for well over two weeks. In that time I've done a good share of setup on the server. So I'm probably inclined to fiddle with it for awhile today. Leading me into a second question of finding some simple to follow docs for Grub2. Anyone able to point me in the direction of some quality troubleshooting documentation on Grub? Would be much appreciated.

---

### Post by Xiuh on 2009-12-11
Think I found some good documentation on Grub2 in the community docs. Not sure why I kept missing it before. Anyways, I think I'll be okay on this issue now that I have something to look at.

As you might of guessed, my problems not near as bad as I thought (That being the recent realization that grub2 renamed the menu.lst to grub.cfg).

---

### Post by TwiceOver on 2009-12-11
The actual file is /etc/default/grub

no .cfg or anything like that.  Once you are done editing, save the file and back at the prompt issue the command sudo update-grub

---

### Post by windependence on 2009-12-12
Download a copy of SuperGrubDisk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

-Tim

---

