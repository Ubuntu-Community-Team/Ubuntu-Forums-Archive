---
title: "GNU/Hurd coming to Debian... eventually..."
date: 2011-07-15
forum: The Cafe
---

### Post by ninjaaron on 2011-07-15
[I]Hurd Progresses - Debian GNU/Hurd by end of 2012?

Hurd logo The GNU Hurd developers are moving forward with their work on the free software operating system. According to the most recent progress report from the project, there is now a "real plan" to release a Hurd variant of Debian with the release of Debian 7.0 Wheezy.

Debian is a project renowned for releasing only when it is ready though, and currently Wheezy is expected towards the end of 2012 or beginning of 2013. The progress of the Hurd specific components of that release are being tracked on a Debian Wiki page. Debian maintainer Samuel Thibault has already produced a Debian GNU/Hurd CD Set with a graphic installer which is available to download.

Other Hurd developments include Google Summer of Code work being performed by Jérémie Koenig, who is not only improving the port of Java on Hurd but also improving the operating system's handling of signals. The availability of bounties for Hurd work and a planned Hurd meeting at the GNU Hackers Meeting in Paris this August, is also noted.[/I]

[http://www.h-online.com/open/news/item/Hurd-Progresses-Debian-GNU-Hurd-by-end-of-2012-1279253.html]("http://www.h-online.com/open/news/item/Hurd-Progresses-Debian-GNU-Hurd-by-end-of-2012-1279253.html")


Interesting.  I'd sure be willing to try it so long as there isn't any regression in hardware and software support.

---

### Post by Dustin2128 on 2011-07-15
You can bet there will be regression in hardware support- or rather hardware that was never supported in the first place. HURD is so outdated that it would take years to make it usable.

---

### Post by dasan on 2011-07-15
I too Want to have micro kernel which doesn't need and restarts, crash free system
Welcome hurd it was a long time waiting

---

### Post by Quadunit404 on 2011-07-15
> **dustin2128 said:**
> you can bet there will be regression in hardware support- or rather hardware that was never supported in the first place. **hurd is so outdated that it would take years to make it usable.**

+1

I don't really see how this is a good idea.

---

### Post by Dustin2128 on 2011-07-15
Even if you wanted to for whatever reason, the FSF is still very into the cathedral development model- they'd be starved for developers. Not to mention I've heard that the code base isn't exactly top notch.

---

### Post by Primefalcon on 2011-07-15
I wouldn't use it, they're far too against any use of proprietary software at all for my liking, Which means the hardware support we enjoy because of binary blobs would be non-existant!

---

### Post by Dustin2128 on 2011-07-15
I don't think so- latest debian has no blobs and is very usable, with a variety of hardware. ATi open video drivers are excellent, almost all intel video drivers are open, and open wireless drivers are better than you think. However, the level of hardware support will likely be pathetic because it's been out of development for longer than Duke Nukem Forever, and the majority of focus in the meantime has been in linux. Not that they couldn't get the excellent open drivers that we enjoy ported- it would take a *helluvalong *time.

---

### Post by MrNatewood on 2011-07-15
I don't get it. What is the big difference from:
[http://www.debian.org/ports/hurd/hurd-cd](http://www.debian.org/ports/hurd/hurd-cd)
?

---

### Post by NightwishFan on 2011-07-15
Tried it in virtualbox; It does not like virtualbox. Seems to have slow IO performance. If I had vtx support I would try kvm. It took ages just to install the base system so I did not bother to install a simple gui.

It seems the devs are optimistic they can bring something to the table. You would have to lurk the mailing lists to know for sure.

Personally I welcome the Hurd becoming usable. Not that it would be a linux/bsd killer or anything... It would make Debian able to run on one of three kernels of your choice. The GNU/KFreeBSD port is already pretty excellent. This is a video I did a while back (of debian freebsd). It is neat that my custom web browser works. :) Hopefully Hurd can catch up!
[http://www.youtube.com/watch?v=vqY5C_cCeqg](http://www.youtube.com/watch?v=vqY5C_cCeqg)

---

### Post by grahammechanical on 2011-07-15
Yes to all the above comments. What do I know anyway? But

there will be no dispute about this being called GNU/Linux.

Regards.

---

### Post by handy on 2011-07-15
There is Arch Hurd too:

[http://www.archhurd.org/](http://www.archhurd.org/)

---

### Post by forrestcupp on 2011-07-15
So now you'll be able to run Debian on the exact same computer setup that the Hurd was created on. :)

I'm all for it. Maybe we'll offload some of the crazies. ;)

---

### Post by MonolithImmortal on 2011-07-15
This is why I think RMS was somewhat forward thinking with the Gnu/Linux stuff. It helps it differentiate between Gnu/Linux Gnu/Hurd and Gnu/kFreeBSD. Not to mention FreeBSD proper and the like. Are there any other kernels that run Gnu?

Not to say that I'm a zealot about it using the phrase Gnu/Linux.

---

### Post by conundrumx on 2011-07-15
I just looked up "too little, too late" in the dictionary and "HURD" was printed thousands of times...

---

### Post by mips on 2011-07-15
I'm all for micro kernels but somehow I can't see using Hurd until maybe I use a zimmer frame to get around with.

So what kernel did they end up deciding on as they looked at so many?

---

### Post by Dustin2128 on 2011-07-15
Mach kernel I believe.

---

### Post by Hwæt on 2011-07-15
> **grahammechanical said:**
> Yes to all the above comments. What do I know anyway? But

there will be no dispute about this being called GNU/Linux.

Regards.

Of course not, but there will be needless bickering about whether to call it GNU/GNU or GNU+GNU

---

### Post by Primefalcon on 2011-07-15
Even without the kernal only a tiny portion of the code is GNU 8% to be precise, gnome and x.org take up * as well alone btw so does kde alone hell even Mozilla's firefox (which is in most dists) takes up 8%.... so..... yeah

so going bt the 8% we should be calling it s gnu/linux/mozilla/gnome/kde and whatever else

---

### Post by koenn on 2011-07-15
> **Dustin2128 said:**
>  Not to mention I've heard that the code base isn't exactly top notch.
Why spread rumors ?
The code base is available online, whu don't you have a look at it and point out some of the major flaws ?

---

### Post by DangerOnTheRanger on 2011-07-15
Development of Hurd is proceeding at Mach 0.00000000001...

---

### Post by mips on 2011-07-15
> **Dustin2128 said:**
> Mach kernel I believe.

No, technically there were so many better alternatives.

---

### Post by Bandit on 2011-07-15
> **Dustin2128 said:**
> You can bet there will be regression in hardware support- or rather hardware that was never supported in the first place. HURD is so outdated that it would take years to make it usable.

++This++


Say by by to what commercial support there was..

---

### Post by Dustin2128 on 2011-07-15
> **koenn said:**
> Why spread rumors ?
The code base is available online, whu don't you have a look at it and point out some of the major flaws ?
Because I suck at C?

---

### Post by wolfen69 on 2011-07-15
> **Primefalcon said:**
> I wouldn't use it, they're far too against any use of proprietary software at all for my liking, Which means the hardware support we enjoy because of binary blobs would be non-existant!

This.

If you can get by with it, more power to you. But I like all the bells and whistles too much to give up ubuntu, fedora, etc....

I might play around with it in vbox or something though. But I couldn't see myself using it as my everyday OS.

---

### Post by Bandit on 2011-07-15
> **wolfen69 said:**
> This.

If you can get by with it, more power to you. But I like all the bells and whistles too much to give up ubuntu, fedora, etc....

I might play around with it in vbox or something though. But I couldn't see myself using it as my everyday OS.

Like wise. Its hard enough to get people to use Linux as it is, take away wireless support and nv/ati drivers. That is enough to prevent anyone from using it. 

If Debian does stop using Linux and becomes a Hurd OS then its just going to make my option simpler. Stick with Ubuntu. Just install a dif DE.. :P

---

### Post by krapp on 2011-07-15
> **Bandit said:**
> Like wise. Its hard enough to get people to use Linux as it is, take away wireless support and nv/ati drivers. That is enough to prevent anyone from using it. 

If Debian does stop using Linux and becomes a Hurd OS then its just going to make my option simpler. Stick with Ubuntu. Just install a dif DE.. :P

LOL--and where would that leave Ubuntu (without Debian GNU/Linux)?

---

### Post by NightwishFan on 2011-07-15
> **Bandit said:**
> If Debian does stop using Linux and becomes a Hurd OS

It isnt.

---

### Post by Bandit on 2011-07-15
> **krapp said:**
> LOL--and where would that leave Ubuntu (without Debian GNU/Linux)?

Compiling our own Kernel..  Ubuntu doesnt need Debian anymore. Dont get my wrong I am a huge Debian fan and the whole hurd thing is disturbing to me. 
But Ubuntu has the user base now to be self sustaining for the most part.

---

### Post by Bandit on 2011-07-15
> **NightwishFan said:**
> It isnt.

Didnt say it was, I said "IF". That leaves room for speculation.

---

### Post by NightwishFan on 2011-07-15
> **Bandit said:**
> Didnt say it was, I said "IF". That leaves room for speculation.
There is no room for speculation. It is not technically feasible least for the next year or two.

How is HURD disturbing for you? Debian already has a working FreeBSD port and Linux is still there.

---

### Post by riemann_zeta on 2011-07-15
> **Bandit said:**
> the whole hurd thing is disturbing to me. 

Why would it be disturbing? It's not like Debian is dropping its use of Linux. HURD is like running Linux on a potato; it's pretty cool, but potatoes are not going to replace your desktop in the near future.

---

### Post by krapp on 2011-07-15
> **Bandit said:**
> Compiling our own Kernel.. Ubuntu doesnt need Debian anymore. Dont get my wrong I am a huge Debian fan and the whole hurd thing is disturbing to me. 
But Ubuntu has the user base now to be self sustaining for the most part.

Unless I am mistaken, Ubuntu gets a lot more from Debian than just a kernel.

Also, Hurd isn't a threat to the Linux kernel, and probably never will be. Debian's main offering will be GNU/Linux for the foreseeable future.

---

### Post by Mr. Picklesworth on 2011-07-16
It'll be interesting if Hurd tries to compete on some level. Perhaps, if they're interested in winning mind-share, the FSF might adopt a little of the pragmatism that has served Linux so well. (If they don't, I'll continue to expect very little from the project).

---

### Post by wolfen69 on 2011-07-16
> **krapp said:**
> LOL--and where would that leave Ubuntu (without Debian GNU/Linux)?

It would leave ubuntu in the position of having no choice but to carry on. (debian) I'm *sure* a bunch of devs would jump on ship. They are not going to just let "debian" die. Pulease........ :rolleyes:

---

### Post by Bandit on 2011-07-16
> **NightwishFan said:**
> There is no room for speculation. It is not technically feasible least for the next year or two.

How is HURD disturbing for you? Debian already has a working FreeBSD port and Linux is still there.

If Debian was to use Hurd as a replacement kernel, as in no longer using the Linux kernel. Then it would loose lots of driver support IMHO, particularity binary driver support from commercial companies. I have no problem with the BSD kernel support. Debian package manager with the solid BSD kernel can have it place in certain market niches. Now lets say they stay with Linux as main kernel and just offer HURD along with the BSD as options. Then all is good with that. But IMHO replace Linux kernel with the Hurd one would be a recession in development.

---

### Post by Bandit on 2011-07-16
> **krapp said:**
> Unless I am mistaken, Ubuntu gets a lot more from Debian than just a kernel.

Also, Hurd isn't a threat to the Linux kernel, and probably never will be. Debian's main offering will be GNU/Linux for the foreseeable future.

Not really meaning to sound like Ubuntu doesn't, just pointing out Ubuntu doesn't have to anymore. If push comes to shove it may be a tough transition but I feel Ubuntu would manage on its own without Debian.

---

### Post by wolfen69 on 2011-07-16
> **Bandit said:**
> but I feel Ubuntu would manage on its own without Debian.

See my post above, I agree. Enough debian devs would work with ubuntu to make it viable. Heck, ubuntu IS debian, just changed a bit. ;)

---

### Post by NightwishFan on 2011-07-16
> **Bandit said:**
> Now lets say they stay with Linux as main kernel and just offer HURD along with the BSD as options.
That is exactly what they are doing. You can download a different CD to install any one of the kernels. :)

---

### Post by wojox on 2011-07-16
> **handy said:**
> There is Arch Hurd too:

[http://www.archhurd.org/](http://www.archhurd.org/)

I've been meaning to try that. Have you given it a spin handy?

I did a fresh install of Arch and loaded DWM. I've been configuring and compiling for a day and a half. :P 

I love C code. :popcorn:

---

### Post by Bandit on 2011-07-16
> **wolfen69 said:**
> See my post above, I agree. Enough debian devs would work with ubuntu to make it viable. Heck, ubuntu IS debian, just changed a bit. ;)
Definitely :)


> **NightwishFan said:**
> That is exactly what they are doing. You can download a different CD to install any one of the kernels. :)
Thats good. I know how rebellious Debi-tons can be against anything non-free. They make a great OS and would sadden me to see them go all south.

---

### Post by wolfen69 on 2011-07-16
What's the line on GNU/Hurd making it as a serious OS? 500,000,000 to 1? :)  I would bet against it at this point. I'm all for upstarts, but gnu/hurd has been around how long? I just don't see it. <scratches head>

---

### Post by wojox on 2011-07-16
> **wolfen69 said:**
> Heck, ubuntu IS debian, just changed a bit. ;)

Your right. Ubuntu made Debian usable. :P

---

### Post by wolfen69 on 2011-07-16
> **wojox said:**
> Your right. Ubuntu made Debian usable. :P

Well, a geek could argue that it didn't need "usability". Debian was just fine the way it was. It's up to people to learn how to use Debian. 

I understand that attitude, but don't advocate it. Debian is an *awesome* OS, but still has chinks in the armor. But overall, the debian way of doing things is incredible. Don't get me wrong, I love linux as a whole, and am not just an ubuntu fanboy. I love linux as a whole. 

I'm old enough to where things "just work". I demand it. I'm too old to go out all night and get crazy. Hmmm...... can't believe I just said that. 25 years ago, I was partying like you wouldnt believe. Thankfully, I've chilled out and just try and have fun. Ubuntuforums are by far the best forums around. People get real.

---

### Post by handy on 2011-07-16
> **wojox said:**
> I've been meaning to try that. Have you given it a spin handy?

...


No, I just keep an eye on it, I expect I'll have a look at it in the future providing development continues. I see it as a tough thing to be involved in as so much time is spent working out how to make things work, all the while knowing that it is most likely years away from being useful.

I imagine that a lot of people have burnt out their enthusiasm for the project.

I'd love to see Hurd & Arch Hurd come to fruition for many reasons.

---

### Post by wolfen69 on 2011-07-16
Oh Ghawd. Same ol'

---

### Post by Barrucadu on 2011-07-16
Apparently some people took this as meaning Hurd will hit a 1.0 release in time for 2012/2013 (this caused quite a discussion in #hurd). What is meant is that Hurd will be stable enough for Debian GNU/Hurd to be released (which of course doesn't need the Hurd to be anywhere *near* finished, just more stable).

To clarify a point some people may misunderstand, the Hurd won't be afflicted with ancient drivers. There has been much work on porting DDE to Mach, which would allow the use of Linux 2.6.29 drivers without any code changes (theoretically), just recompilation. Currently it works pretty well for NICs, I'm not sure what the work is concentrating on at the moment but of course a large area of interest is SATA hard drives, so I wouldn't be surprised if that got support over the coming months.

Additionally, Debian has decided that Pulseaudio is an important thing to port, which would bring sound to the Hurd (albeit still having to go through another computer as there are no sound drivers yet). The opinion I've seen of many people is that there is not much being done on the Hurd, but if you just look at the mailing list, you will see that there is a lot of work going on. The problem is just that there are very few active developers, so of course these things seem slow in comparison to, say, Linux.

---

### Post by Bandit on 2011-07-16
What I mostly dont understand is why develope HURD kernel? If its just for the heck of it by some people that are just board and have to much time on their hands. All good I guess. But there is nothing wrong with the Linux kernel. Linus is the last person I see trying to tern super evil genius on us at this point.

---

### Post by forrestcupp on 2011-07-16
> **krapp said:**
> LOL--and where would that leave Ubuntu (without Debian GNU/Linux)?

> **NightwishFan said:**
> There is no room for speculation. It is not technically feasible least for the next year or two.

How is HURD disturbing for you? Debian already has a working FreeBSD port and Linux is still there.

Exactly. Debian is not *switching* to HURD. They are just evidently offering it as another *choice*, like BSD. They're never going to get rid of Linux.

---

### Post by mips on 2011-07-16
> **Barrucadu said:**
> Apparently some people took this as meaning Hurd will hit a 1.0 release in time for 2012/2013 (this caused quite a discussion in #hurd). What is meant is that Hurd will be stable enough for Debian GNU/Hurd to be released (which of course doesn't need the Hurd to be anywhere *near* finished, just more stable).

+1

[http://www.gnu.org/software/hurd/microkernel/mach/gnumach/hardware_compatibility_list.html](http://www.gnu.org/software/hurd/microkernel/mach/gnumach/hardware_compatibility_list.html)

> **CPU Architecture**

GNU Mach current only supports the x86 (alias ia32 or i386) architecture.

amd64/ix64 should work in 32-bit compatibility mode. However, in practice amd64 systems seem to be troublesome more often than not. This is probably related to the same (chipset-related) problems we often see with recent machines; but it seems that amd64 ones use problematic chipsets particularily often. So far we haven't heard of similar problems with Intel's eqivalent ix64 (or EM64T as it used to be called) -- but maybe that just means fewer people tried running the Hurd on such machines 

Support for running GNU Mach (and a complete GNU/Hurd system) in a Xen domU (again on x86 only) is being worked on.

Read about further ports.


**Memory**

GNU Mach will use a maximum of 1 GiB of RAM. If your system has more, the surplus will silently be ignored. (In past times, this would hinder GNU Mach from booting at all, but this has been fixed, so you no longer need to apply GRUB's uppermem directive.)


**Video Cards**

Debian distributes a version of X.org. If your video card driver depends on a special kernel interface such as that provided by the agpgart kernel module for the Linux kernel, then your video card will only be supported by the VESA driver.

Using an internal i815 videocard won't work (at least when using the specialized driver), because of missing AGP GART support in GNU Mach.


**Sound**

No sound cards are supported at this time.


**USB 1.1/2.0**

USB is not supported at this time.

However, USB-type keyboards and mice may (and have been reported to) work nevertheless, given that the hardware / BIOS is doing emulation to the supported legacy interfaces.


**IEEE 1394 (Firewire)**

IEEE 1394 is not supported at this time


**Storage**

All common IDE drives should work. Some drive geometries do not work, e.g. drives with hundreds of GiB of storage space, see GNU Savannah bug #26425.

SATA drives may work in compatibility mode.


**Device Drivers**

GNU Mach Reference Manual, Configuration contains a list of device drivers that are included in GNU Mach and elaborates on the hardware devices they support.


**User Success Reports**

These boards are known to work. Gnumach/Hurd has been installed and run on these board successfully.

ASUS P2B motherboard with an Intel PII 450MHz CPU with Intel Pro/100 NIC in PCI slot
Intel SE-440BX motherboard
VIA EPIA-M Mini-ITX motherboard with VIA Nehemiah C3 1Ghz processor. Onboard NIC (VIA Rhine) works good.
Compaq Deskpro ENS, Pentium3 (666 MHz upgraded to 1 GHz), Intel i815 chipset, chipset integrated NIC (detected twice, but works fine with eth0; trying to access eth1 confuses the driver and makes the system unusable), Matrox Mystique 220 (PCI) graphics card. Also works with rtl8029 (NE2000 PCI) NIC when onboard NIC disabled in BIOS setup.
Abit BX6 Rev. 2.0 with Celeron 400, after disabling "memory hole at 15MB" option in BIOS setup. (Otherwise, Mach detects only 15MiB of RAM, making Hurd run extremely slow and instable.) Should also work with PentiumII or Pentium3.


**User Failure Reports**

Some people couldn't get these hardware combinations to work with Hurd.

Note: The Debian GNU/Hurd installer actually runs on Linux, so it (almost) always works. The critical bit is booting after installation.

ASUS P5A motherboard and AMD K6-2 333MHz CPU - doesn't boot
ASUS P2B-LS motherboard with an Intel PII-MMX 400 MHz CPU - this board had a defective onboard NIC (that could not be disable in BIOS) and working 3COM Etherlink III NIC in a PCI bus slot. This combination worked with GNU/Linux. The 3COM NIC is known to work with the Hurd. However, while gnumach/Hurd will boot on this system, it is confused by the defective onboard NIC and unable to use the 3COM NIC. Attempting to start networking generates a continous stream of eth0 and eth1 reset messages on the console that renders the system unusable.
ASrock 775Twins-HDTV with a Pentium D 810 (533 MGz FSB/2600GHz core -- information no longer present on intel's site). Doesn't boot.

---

### Post by Bandit on 2011-07-16
LOL O' My.. Does look like HURD is moving at the speed of sloth!.. lol

---

### Post by NightwishFan on 2011-07-16
Last time I tried the installer it looked like it booted hurd to install.

---

### Post by mmairs on 2011-07-16
Running under VMWare Player 3.0.1.
Occasionally sluggish, occasionally blindingly fast.  Always Not UNIX.
I do not recommend dvd.iso or netinst.iso ATT.  I'll get back to you when I get X to display.

---

### Post by Primefalcon on 2011-07-17
> **Mr. Picklesworth said:**
> It'll be interesting if Hurd tries to compete on some level. Perhaps, if they're interested in winning mind-share, the FSF might adopt a little of the pragmatism that has served Linux so well. (If they don't, I'll continue to expect very little from the project).
The FSF adopt pragmatism... That'll never happen.... and hurd will never be used mainstream even in the Linux community.

However having said that having the FSF does create an extreme viewpoint so we can at least come to a middle point.

---

### Post by 8_Bit on 2011-07-17
No amd64 support? Well that kills it for me right there. :( I'll definitely try it out in a VM though.

---

### Post by mmairs on 2011-07-17
It's a pleasure... mostly.  Microkernel snappiness overall reminiscent of QNX.  Also similarly, very little works exactly how you expect: exciting!  Got X going thanks to handheldCar@Debian User Forum's minimal xorg.conf:
***
Section "Pointer"
  Protocol "osmouse"
  Device "/dev/mouse"
EndSection
***
Playing with WMs et cetera... gotta give it a =D> ATM.

---

