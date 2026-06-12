---
title: "Canonical's statement on i386 clarification?"
date: 2019-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by LwIh%*7 on 2019-06-26
According to this: [https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts](https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts)

Will that mean that steam technically speaking should be able to run as normal for Ubuntu 19.10 and 20.04 LTS and beyond if already installed? Could someone clarify this explanation for me will we loose our game files and have to reinstall steam or can we continue as normal with steam on the Ubuntu system beyond 19.10+. Will they possibly make it possible so that we won't have to re-download our games etc.

---

### Post by CatKiller on 2019-06-27
There's no "technically speaking" about it: it will work fine. Normal users should be using LTS releases anyway. 

Ubuntu will, at some point, remove all i386 binaries from the repositories. They've been discussing that since the release of 18.04 LTS, and they already don't make i386 install images. They were going to test that removal in 19.10 in preparation for 20.04 LTS.

As it turns out, neither Wine nor Steam were adequately prepared for a move to a purely 64-bit environment by 2023. As a result, Ubuntu will include the i386 binaries needed by those applications, and whichever ones the community says that they really need, in 19.10 and 20.04 LTS, to give those users more time to adjust.

---

### Post by LwIh%*7 on 2019-06-30
So am I right in stating that steam will eventually be 64-bit with the necessary 32-bit libraries in steam's runtime. Will this be the long-term plans for steam? Out of interest. It would be nice eventually if steam had a native 64-bit client with all of the 32-bit libraries in the runtime then it won't matter if Canonical cuts 32-bit fully because steam will natively support it with the 64-bit client if I'm not mistaken.

---

### Post by CatKiller on 2019-06-30
I expect that Steam will eventually be available as a 64-bit application. It already is on OS X. Putting whichever 32-bit libraries they need into their runtime seems sensible to me, since they use that anyway.

Longer term than that, I don't know. The Ubuntu devs are more fans of snaps than I am, and they aren't keen on the steam package in the repository because it doesn't clean up after itself, so if Steam starts being distributed as a snap that would be fine as far as the Ubuntu devs are concerned, I think. It would be a self-contained thing that would have whatever libraries it wanted inside.

I suspect that there might be a way to move away from multiarch for running stuff; when an application calls a 32-bit function, it might be possible for a 64-bit library to provide the function instead, but with things like 32-bit pointers and the like. There's already something like that in the kernel, x32, which was done for performance rather than compatibility, but no one uses it. I don't know if that could be repurposed for that, but it seems possible to me.

---

### Post by kurt18947 on 2019-06-30
I hope Brother is paying attention to this. I've had excellent luck with Brother printers & scanners on Ubuntu. At least some of their drivers have 'i386' in the file name. As long as the appropriate libraries are available I guess I need not be concerned.

---

### Post by CatKiller on 2019-06-30
Hardware manufacturers have had to have a 64-bit workflow for their drivers since the release of Windows 7: Microsoft made it a requirement that they had to have a 64-bit driver as well if they were going to be allowed to use a 32-bit driver, and they have more sway than we do. The only companies that won't do the minimal step of releasing 64-bit drivers when support for 32-bit drivers lapses are the ones that *really* don't want to support their hardware. Sadly, there are some companies with that attitude.

---

### Post by wildmanne39 on 2019-06-30
It looks like for now Canonical will have support for 32bit to some extent for steam/wine and maybe some other apps, here is an interesting read, this person has steam/wine working in 64bit.

[https://blog.simos.info/i-am-running-steam-wine-on-ubuntu-19-10-no-32-bit-on-the-host/](https://blog.simos.info/i-am-running-steam-wine-on-ubuntu-19-10-no-32-bit-on-the-host/)

I am not suggesting everyone do it this way, I am just presenting options.

---

### Post by mastablasta on 2019-07-01
i was always a bit suspicious with the repositories distribution system. sure it takes up less space because you have shared libraries, and all is centralised and backwards compatibility will be taken care of. or so i was told. but it seems they can just decide to drop it and then you are left with more than half of staff not working. in windows libraries come with programs and suplement those on the system if necessary. that's why i can stil play a game on windows 10 that was made for windows 95 back in 1997. install and play. the only ones that had issues with XP and newer were DOS games but DOS box, it's optimisation (i remember the first versions...) and a bit more powerful CPU solved it more than adequately by adding some features in the process as well (making movies, screenshots...). this wasn't done overnight. and also many DOS programs actually worked in XP as well. until win 8 we could run a DOS based ERP (we had data there for some old stuff that people were still buying). I can't run it directly in win10 it seems (the launcher doesn't start it), or at least not without admin setup. luckily we don't need it anymore.

in ubuntu we will have a couple of years old stuff that will no longer work. if i saw correctly smoking guns have only 386 version. 

snaps is probably ok for any future 32bit apps, but i doubt people will start making them for older ones.

---

### Post by CatKiller on 2019-07-01
WoW64, which is the way Windows does it, is like the old ia32-libs method. Multiarch is already better than that. WoW64 can't even handle 16-bit applications, even though they run natively on AMD64. 

Ubuntu aren't taking multiarch away, they just don't want to build 32-bit binaries of every library in the main repository any more. Those binaries could be done in the ports repository, or people could make a PPA of the ones they need, or containerised applications could include them, or whatever.

All the wailing and gnashing of teeth is extremely silly.

---

### Post by mastablasta on 2019-07-04
as long as the 32 bit apps continue to work as they do now, i don't see a problem. but as soon as they stop working i would have a problem. 

and from what i can tell and from the experiments made, they stop working (which makes sense).

---

### Post by ardouronerous on 2019-07-08
[QUOTE=CatKiller]The only companies that won't do the minimal step of releasing 64-bit drivers when support for 32-bit drivers lapses are the ones that *really* don't want to support their hardware. Sadly, there are some companies with that attitude.[/QUOTE]

Brother Industries releases their printer drivers for Linux under 32-bit, but I wouldn't say Brother Industries doesn't really want to support their hardware. AFAIK, Brother is one of the leading manufacturers of printers that supports Linux, in every forum I've been to, Brother is the most recommended brand for Linux because they really support Linux.

I'm just guessing here, so take my opinion like a grain of salt, but the problem I see though is, Brother already released their drivers for Linux and doesn't want to be bothered with it anymore I think, I think Brother wants the Linux community to fix the issue ourselves, like convert their drivers into 64-bit ourselves.

[QUOTE=CatKiller]Hardware manufacturers have had to have a 64-bit workflow for their  drivers since the release of Windows 7: Microsoft made it a requirement  that they had to have a 64-bit driver as well if they were going to be  allowed to use a 32-bit driver, and they have more sway than we do.[/QUOTE]

For Windows only. Manufacturers have more incentive to support Windows intensively than Linux unfortunately, because of Linux's low market share on the Desktop market. If a company does support Linux, it's just gives little support, like creating a driver for Linux only for 32-bit.

---

