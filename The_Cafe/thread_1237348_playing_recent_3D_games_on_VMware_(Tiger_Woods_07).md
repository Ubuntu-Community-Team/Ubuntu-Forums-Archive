---
title: "playing recent 3D games on VMware (Tiger Woods 07)"
date: 2009-08-11
forum: The Cafe
---

### Post by RikoW on 2009-08-11
Dear all,

I'm not really sure where to post, but searching the forums came up with many hits in the Community Cafe, so here it goes :)

I have a Dell E4300 with an Intel GMA 4500 graphics chip and running an XP guest in VM WS 6.5 with activated 3D acceleration. *dxdiag* on XP shows that directX is supported (with tests passed) except for *AGP texture acceleration* - see attachment.

However, when trying to run Tiger Woods PGA 2007, I don't even get a splash screen. The hourglass spins for several seconds and then just stops.

Did anybody succeed in running recent 3D games successfully on VMware and were any tweaks necessary.

Thanks for any hints,

                 Riko

---

### Post by Dark Aspect on 2009-08-11
I've ran several games via VMs and I'll say this, use [wine]("http://www.winehq.org/") instead. Virtual machines are too slow as a general rule to get a decent frame rate. If wine fails, your not completely out of luck, you can try [Virtualbox]("http://www.virtualbox.org/").

I've had some luck running older games with Virtualbox:

[[IMG]http://img2.imageshack.us/img2/7624/vbox13.th.png[/IMG]](http://img2.imageshack.us/img2/7624/vbox13.png)

Be sure to increase the vram emulation too, that can have an obvious effect.

---

### Post by bodyharvester on 2009-08-11
you know, now that i think of it im pretty sure ive had problems like this in the past, if your computer is failing to create the display it must be graphics/video

i cant offer much, more i learn about linux the less i remember about wnidows, is there an options/settings where you can set the game to run in safe mode before you actually start it? posting thios in howtogeek.com may help, its more windows than linux and full of gamers

good luck

---

### Post by RikoW on 2009-08-11
@Dark Aspect:

I haven't tried VB since a long time, because I liked the unity mode of VM, however I practice it is not very usable. I'll give virtualbox a spin.

I was not able to even install TW2007 in wine (well actually cxgames). But I saw at least partial success with an older wine version on TW 2005. Maybe it's worth to try that, too. I'll report back :)

@bodyharvester:
safemode is a good idea (if available). As I said there isn't even a splash screen so far.

Thanks for you reply, guys :)

       Cheers,

                   Riko

---

### Post by bodyharvester on 2009-08-11
intel hasnt provided great graphics drivers for linux

sorry, but be prepared for less performance, if your graphics cards apply:(

---

### Post by Dark Aspect on 2009-08-11
> **RikoW said:**
> I haven't tried VB since a long time, because I liked the unity mode of VM, however I practice it is not very usable. I'll give virtualbox a spin.

I was not able to even install TW2007 in wine (well actually cxgames). But I saw at least partial success with an older wine version on TW 2005. Maybe it's worth to try that, too. I'll report back :)

Set the installer to win98 mode inside winecfg and reload wine. See the [Application database]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11956") for more information.

---

### Post by RikoW on 2009-08-21
Okay, I think I finally give up :(

I went back from TW 2007 to 2005 to 2003 and none of them would run on either wine, vmware and virtualbox.

I got as far as installing to starting TW2005 in wine, could select a player and course, but when I started the game it either froze or crashed.

In vmware, TW 2005 and 2003 complained about not enough video memory even though dxdiag reports 128 MB, which should be plenty. In virtualbox, I didn't even manege to install TW2003.

So much for that idea!

Cheers,

                Riko

---

### Post by RikoW on 2009-08-24
OK, just in case anybody is interested. TW2003 seems to work on VMware **without** setting 3D graphics for the display :) Performance only sometimes lags when they show a replay of the shot ... so don't play to nicely :)

Haven't tried all the gadgets yet, but basic playing works fine.

Cheers,

                 Riko

---

