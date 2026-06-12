---
title: "Resolution issue with Ubuntu 16.04 when projected on a particular Optoma projector"
date: 2022-03-12
forum: Ubuntu Cloud and Juju
---

### Post by viraajan on 2022-03-12
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]We are using an Acer Veriton M200 which came with a preloaded Windows 10 SL. We formatted it and installed Ubuntu 16.04. I am unable to change the resolution when I connect this to Optoma CS308ST Projector. If I connect it to a Monitor, or other models of Optoma, the resolution works well and I am able to get the option to change the resolution.[/COLOR]

[COLOR=#000000]Only with this particular model that Ubutu does not display any resolution excep the native 800X600. Seeking support from Optoma or Acer was of no help as they concluded it by saying that the hardware was functioning normally.[/COLOR]

[COLOR=#000000]Please help me with this issue.[/COLOR]

[COLOR=#000000]Acer M200 with Other projector brands & other models of Optoma brand - WORKING[/COLOR]
[COLOR=#000000]Acer M200 with Monitor - WORKING[/COLOR]
[COLOR=#000000]Optoma CS308 with Laptop/other PC - Working.[/COLOR]
[COLOR=#000000]Only Acer M200 with Optoma CS 308 does not have the option to change the resolution.[/COLOR]

[COLOR=#000000]Please help.[/COLOR]

[COLOR=#000000]Thanks[/COLOR]
[COLOR=#000000]Vidhya[/COLOR]

---

### Post by TheFu on 2022-03-13
16.04 support ended in 2021.
Please move to a supported release.

The _Ubuntu Desktop Guide_ has instructions for controlling the video resolution. Google finds it easily.
[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/) is for 21.10 release, which isn't an LTS. You probably want to load 20.04 if you need it today, then search for that desktop guide starting from [https://help.ubuntu.com/](https://help.ubuntu.com/) which has a link to the 20.04 guide.
Look for the section "Change the resolution or orientation of the screen"
Choose a resolution and update rate that the projector supports.

---

### Post by guiverc on 2022-03-13
You weren't very specific about your product, ie. Server or Desktop system, nor which kernel stack you were using (*the installation media used will control that default*), **however** as already suggested - Ubuntu 16.04 LTS reached the end of it *standard* or *public* support some time ago.

I'd suggest reading [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

When a release reaches EOL (*including End of Public Support*), many mirrors/sites drop support for it completely.  Thus it'll be harder now; esp. given security certificates on your *fresh* 16.04 install will be *outdated* or *incorrect* unless you've enabled ESM & updated them.

If you're talking about Ubuntu Desktop 16.04; I hope you noted what & how packages are now supported; ie. many *deb* packages provided on installation media are now EOL; with packages only supported via *snap* packages you need to manually installed as per documentation (migration from 16.04 LTS to 16.04 ESM). eg. [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm) and following articles.  (*there are a couple of wiki pages on the programs on installation media that are now only supported via snap package & how to convert; but I don't use 16.04 ESM & the transition was some time ago now so I've forgotten - pages like [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04)*)

---

