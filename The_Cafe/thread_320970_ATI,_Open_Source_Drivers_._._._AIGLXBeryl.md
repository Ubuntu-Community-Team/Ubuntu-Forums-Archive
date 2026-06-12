---
title: "ATI, Open Source Drivers . . . AIGLX/Beryl"
date: 2006-12-18
forum: The Cafe
---

### Post by Patrick-Ruff on 2006-12-18
we need to do something about this lack of good driver situation for ATI, really.  I think it's quite pathetic that us ATI users (the majority) are stuck with XGL to run beryl right.  either that or we have a very outdated card that barely runs the damn open source driver. 

really, this is pathetic. I'm forced to use a ridiculously unstable platform that runs on top of xorg just to get some decent performance out of Beryl. see, I wouldn't mind if XGL was actually stable, but it's /very/ far from that. and from what I hear you can't play games or do most anything that requires some sort of 3d acceleration . . .

I would think after my 2 years of using ubuntu that someone would bloody do something.

---

### Post by pay on 2006-12-18
I heard a few months ago that Ati/Amd were considering releasing the drivers as opensource. Has anyone heard any follow ups on this?

---

### Post by OffHand on 2006-12-18
Why don't you buy an nvidia card? What you want will not be happening any time soon I'm afraid. I bought my nvidia 6600 for 60 euro and Beryl runs perfectly on it.

---

### Post by katgfan on 2006-12-18
> **Patrick-Ruff said:**
> we need to do something about this lack of good driver situation for ATI, really.  I think it's quite pathetic that us ATI users (the majority) are stuck with XGL to run beryl right.  either that or we have a very outdated card that barely runs the damn open source driver. 

really, this is pathetic. I'm forced to use a ridiculously unstable platform that runs on top of xorg just to get some decent performance out of Beryl. see, I wouldn't mind if XGL was actually stable, but it's /very/ far from that. and from what I hear you can't play games or do most anything that requires some sort of 3d acceleration . . .

I would think after my 2 years of using ubuntu that someone would bloody do something.
I hear you man. I hear you.

---

### Post by katgfan on 2006-12-18
> **OffHand said:**
> Why don't you buy an nvidia card? What you want will not be happening any time soon I'm afraid. I bought my nvidia 6600 for 60 euro and Beryl runs perfectly on it.
I wish I could but my laptop comes with ATI. If I only knew at that time that I will have problems with it i would have chosen another model.

---

### Post by OffHand on 2006-12-18
> **katgfan said:**
> I wish I could but my laptop comes with ATI. If I only knew at that time that I will have problems with it i would have chosen another model.

Yeah, laptops is another thing. I never owned one (until recently) but I can imagine it is hard to replace, if possible at all. Owners of desktop computers should stop whining and ditch their ATI cards. Money talks...

---

### Post by MaximB on 2006-12-18
I knew about ATI problems only after I bought it and after I learned about Linux.
but I don't have real problems (except that 3d games  don't run well in XGL, but it's XGL problem) , my ATI video card runs perfectly, it's ATI 9800 Pro...I just don't get what all of you guys are talking about ;).

---

### Post by pormogo on 2006-12-19
I too would LOVE to get out of XGL I can't even seem to get DRI support from the open source driver for my 9800XT :( I read that ATI's next binary driver release should support compositing which should add support for AIGLX.

---

### Post by tribaal on 2006-12-19
Well fortunately the open source driver is good enough for Beryl/AIglx on my laptop, but the performances are by far not as good as with the binary driver...

Speaking of open source radeon driver, does anybody know where I could find a more up to date version of it? I can't even find the project's homepage or central download place... Is it tied to xorg? Would that mean I'd need to recompile all of xorg to have a newer version of the open source driver?

Cheers

- trib'

---

### Post by pormogo on 2006-12-19
has anyone been able to get the open source driver to do DRI? I have the driver installed and in use but I'm not getting dri even when I add the option to enable dri in xorg.conf :(

---

### Post by Tuna-Fish on 2006-12-19
> **MAXDDARK said:**
> I knew about ATI problems only after I bought it and after I learned about Linux.
but I don't have real problems (except that 3d games  don't run well in XGL, but it's XGL problem) , my ATI video card runs perfectly, it's ATI 9800 Pro...I just don't get what all of you guys are talking about ;).

I own 9800 too, and while it works, it hardly runs perfectly... Using UT2004 as benchmark my card, when overclocked, is roughly as fast  as my friends 6600GT. In linux using fglrx, the performance is roughly half of the 6600gt, using OS drivers it's even worse.

My next card is very definately Nvidia.

---

### Post by Pathfinder_ on 2006-12-19
> **pormogo said:**
> has anyone been able to get the open source driver to do DRI? I have the driver installed and in use but I'm not getting dri even when I add the option to enable dri in xorg.conf :(

it worked right out of the box for me and my radeon 9000pro

---

### Post by WalmartSniperLX on 2006-12-19
All I know is that I have a laptop with a radeon 9200 (on the OS driver) that outperforms my desktop's X1600pro using the latest FGLRX driver. Talk about sad. 

If you people thought the drivers were bad for the radeon 9 - X series, check out the X1K series because there is almost no 3D OR 2D acceleration. This makes me angry:mad:

---

### Post by TBOL3 on 2006-12-19
Isn't there ATI driver's for linux?


Anyway, I have the ATI All in Wonder Radeon, unfortuenatly there is no driver for that, so I have to use the Radeon 7200 driver (wich does not do TV:( , the card has tv I/O)

---

### Post by Pathfinder_ on 2006-12-19
> **TBOL3 said:**
> [B]Isn't there ATI driver's for linux?
[/B]

Anyway, I have the ATI All in Wonder Radeon, unfortuenatly there is no driver for that, so I have to use the Radeon 7200 driver (wich does not do TV:( , the card has tv I/O)

yes there are. many refer to them as fglrx and they perform horribly.

---

### Post by Patrick-Ruff on 2006-12-24
> **OffHand said:**
> Why don't you buy an nvidia card? What you want will not be happening any time soon I'm afraid. I bought my nvidia 6600 for 60 euro and Beryl runs perfectly on it.

laptop buddy.

---

### Post by flapane on 2006-12-24
> **Patrick-Ruff said:**
> we need to do something about this lack of good driver situation for ATI, really.  I think it's quite pathetic that us ATI users (the majority) are stuck with XGL to run beryl right.  either that or we have a very outdated card that barely runs the damn open source driver. 

really, this is pathetic. I'm forced to use a ridiculously unstable platform that runs on top of xorg just to get some decent performance out of Beryl. see, I wouldn't mind if XGL was actually stable, but it's /very/ far from that. and from what I hear you can't play games or do most anything that requires some sort of 3d acceleration . . .

I would think after my 2 years of using ubuntu that someone would bloody do something.

wnat to know how I solved? X800GT Throwed off the window, and bought a 7800gt, ati can go straight to the hell

---

### Post by Patrick-Ruff on 2006-12-24
*sighs* again. . . . laptop BUDDY.  I own an nVidia in my desktop.

---

### Post by flapane on 2006-12-24
woops didn't read before... I wonder you cannot throw your ati chipset away :/
Didn't you know about those issues when you bought the laptop?

---

### Post by Patrick-Ruff on 2006-12-24
I didn't use linux when I bought the laptop . . .

---

### Post by stuh84 on 2006-12-26
I feel your pain, I have a laptop with ATI built in, and never really intended to put Ubuntu on it, but ended up doing it anyway.

I can't even get Beryl or Compiz running at all, never mind though. I have it running on dual monitors on my desktop with an NVidia :)

---

### Post by RudolfMDLT on 2006-12-26
I´ve moaned enough to last me a life time about Ati.... Doesn´t do a thing. Some one said that money talks and yeah, I agree. My next card is definitely a Nvidia. If Ati wants to lose the Opensource market share then bugger them. I do feel sorry for the guys with laptops, I run a X800 on my laptop and it´sa pain in the butt to not be able to push the card to it&#347; potential.

Anyway - Lets just hope that over the New Year AMD-Ati get a change of heart and release the drivers as opensource.

---

### Post by ButteBlues on 2006-12-26
Opensource drivers would be a dream come true. Especially as they'd probably merge the existing opensource driver into the the proprietary one, and, in effect, get a better driver overall that supports more ATI cards.

---

### Post by Knilch2000 on 2007-01-01
I got the OS radeon drivers to work with my ATI 9800 pro.
AIGLX works, direct rendering works, and beryl works :)

see my post here:
[http://www.ubuntuforums.org/showpost.php?p=1954253&postcount=75](http://www.ubuntuforums.org/showpost.php?p=1954253&postcount=75)

:)

---

### Post by Patrick-Ruff on 2007-01-01
you're one of the lucky few that have full 3d acceleration under the open source drivers . . . nothing new here.

---

