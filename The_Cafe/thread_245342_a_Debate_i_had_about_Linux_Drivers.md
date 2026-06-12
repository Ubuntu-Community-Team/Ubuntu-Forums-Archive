---
title: "a Debate i had about Linux Drivers"
date: 2006-08-27
forum: The Cafe
---

### Post by bolerodan on 2006-08-27
Hey guys, i recently had a debate about Linux drivers and windows drivers.  My one friend (who has LITTLE experience with linux mind you) is blabbering on that linux crashes alot due to its crappy made drivers and "Programs in linux crash often because; lack of drivers and crappy drivers,as well as because the people who make drivers arent the manufactures of the hardware so they are crappier" he also says "why else would linux crash because of its poor linux driver programming"

he says he is also blamming linux for its shitty drivers and that if linux was that efficent why not make a debugging system

He also said "Windows is pretty bad, but without proper driver support (by proper I mean hardware manufacturers developing drivers), linux isn't much better."

he just pulls this crap out of his ***, what would you people say to this?

---

### Post by Tomosaur on 2006-08-27
I would say that this is the wrong section, and also that your friend is an idiot :P

---

### Post by jISh on 2006-08-27
Not to mention that for many pieces of hardware, we do indeed use the Windows drivers, commonly with ndiswrapper.

And there is always ongoing development of native drivers!

---

### Post by matthew on 2006-08-27
I say for the most part your friend is misinformed and also that this thread belongs in the cafe, so I'm moving it. :)

---

### Post by bolerodan on 2006-08-27
oops sorry about posting it in the wrong section, im new around here so im still trying to find everything!

BUt yeah this guy just pulls this stuff out of his ***, without resaerching ir or experience with it.  It was pretty funny because i asked him to proove it for me and he replied "well give me a minute im gunna go read articles"

lol what ever

-Bolero

---

### Post by IYY on 2006-08-27
I don't think what he says is so far from the truth. So far, 90% of crashes I've seen on Linux systems were due to problems with drivers; usually video card drivers. I'm pretty sure that over 50% of Windows crashes are due to drivers. However, I notice that non-open drivers tend to be even worse in this aspect than open ones, so he is wrong about that part.

---

### Post by matthew on 2006-08-27
> **IYY said:**
> I don't think what he says is so far from the truth. So far, 90% of crashes I've seen on Linux systems were due to problems with drivers; usually video card drivers. I'm pretty sure that over 50% of Windows crashes are due to drivers. However, I notice that non-open drivers tend to be even worse in this aspect than open ones, so he is wrong about that part.Well, not fully. I said his friend was mostly misinformed because the problems with linux drivers that exist are not caused by linux. They result from hardware manufacturers not writing drivers, writing poor drivers that are closed source, or not releasing specs so that the community can write drivers.

The open source drivers that exist for linux, either written by the hardware manufacturer and occasionally improved by the community, or written by the community using specifications made available by the manufacturer are generally excellent.

Also, I use an ATI card with the closed-source binary 3D driver produced by ATI. It's not great, but it works. I can honestly say it doesn't crash. In fact, for me with my hardware (see the "my setup" link in my sig if you're interested) Linux is far more stable than Windows ever was...

...just my $0.02

---

### Post by bolerodan on 2006-08-27
thanks for the replys, however saying this to my friend:

"hey result from hardware manufacturers not writing drivers, writing poor drivers that are closed source, or not releasing specs so that the community can write drivers."

he will combat with "The manufactures arnt going to write crappy drivers.. THEY KNOW THEY'RE OWN HARDWARE, they made the thing, they arnt going to develop crappy drivers! The community writing drivers arnt going to be better then the actual manufactures writing drivers of their own hardware"

---

### Post by DoctorMO on 2006-08-27
The diference between closed source and open source drivers of the kind your friend is talking about.

1) An open driver once written is _always_ available to the latest versions, alowing open source to support older hardware far better.
2) An open driver is more secure because flaws can be fixed without asking companies that may have gone out of business or just don't care.
3) An open driver writen for open source is normaly far more intergrated into the system and far more stable compared to closed source drivers (regardless of platform)
4) Where full specifications are known about the hardware you will find the best drivers, this is a task of information. so hardware makers have the advantage that they don't need to research the hardware to write the drivers.
5) If we can, we make drivers that work well together, try installing 3 tv cards in windows that are from the same maker. they fall out because the versions on the driver have been made incompatble. yet the linux drivers were made to work with all hardware at the same time.


The best way: hardware makers should make their drivers for windows and release the specifications for the hardware to developers of other platforms _without_ NDAs that prevent the release of the code as GPL.

We don't want hardware makers to make drivers for linux, this would lead to nVidea and ATI type restrictions. *yak*

---

### Post by az on 2006-08-27
Binary-only drivers taint the kernel which means, among other things, you can't debug that running kernel.

Traditionaly, the most unstable part of running a linux desktop was using binary-only (provided by the MANUFACTURER) graphics drivers which would lock up your machine.

By and large, the free-libre open-source stuff is much more stable (always has been).  So that goes against what that guy says.  

Also, in the past few years, the ATI proprietary (binary-only) drivers seem to have become much more stable.  Has he tried linux recently?

---

### Post by gnomeuser on 2006-08-27
Out of the box no OS supports more hardware than Linux and the drivers in the kernel are of a much higher quality than propritary ones. Just read LKML and watch the number of comments on intially proposed drivers from companies.

Gregh Kroah-Hartmanns OLS keynote touched upon this in great detail but the simple answer is that your friend is dead wrong.

The only areas we lack in is WiFi, >r300 ATI cards and nvidia cards. Wifi is being worked on, you are encouraged to bother your vendor till they provide specs. nvidia and ATI well... tough luck complain till something happens, vote with your buck..

---

### Post by atrus123 on 2006-08-28
> **gnomeuser said:**
> Out of the box no OS supports more hardware than Linux and the drivers in the kernel are of a much higher quality than propritary ones. Just read LKML and watch the number of comments on intially proposed drivers from companies.

Yep.  Compare a Windows install to a Linux install on any-given-laptop.

After you install Windows, are you done?  Nope, unless you have the restore discs (and a lot of people don't), you will need to go to the manufacturers website and download a bunch of drivers.  Of course, if you have certain brands, like Gateway, some of your drivers won't even be there, and you'll have to run an unidentified device detector (think lspci for windows) in order to figure out what you need and track it down.

I work part time as a tech at a major PC retailer while I work on my graduate degree, and I experience such problems with Windows XP every day. 

What I really hate is that amorphous "! PCI Device"  that shows up in the Device Manager after a lot of installs.  It usually takes a good bit of time figuring that one out.

And Linux?

Chances are, if you're running an up-to-date distro like Ubuntu or SuSE, most or all drivers will be taken care of for you, most of which provided in the kernel itself.  Of course, wireless can still be a chore for new Linux users, but that's really the only thing I have a problem with anymore.  In my opinion, it is much easier to install Ubuntu than Windows these days.

Oh, and it's a lot quicker too.

(I've heard Vista is going to take forever to install.  Anyone tried it who cares to comment?)

---

### Post by The Noble on 2006-08-28
I installed Vista a while ago (beta 1 if I remember), and used it for about a day before getting bored. Install was not bad enough to scream at, and it was very nice looking; it even looks like the fully installed desktop while setting options. No complaints from me there, I did not really notice. I did not time, but it did not piss me off, which is what really matters. Actually, on first boot the nice effects were there, no need to tinker with an ugly desktop to get Aero :P. From what I used, Vista was very nice. No crashes, albeit unusable in my mind.

From my limited experience, Linux either works or it doesn't. It is almost a luck of the draw. If you have something borked, it can take hours to fix.

---

### Post by DoctorMO on 2006-08-28
Yes, personaly I count Compiz/Xglx as not quite finished yet and anyone installing it is just giving it a bit of a test drive.

Sometimes Linux configuration can be too much hastle, take my scanner for instance it's got a special firmware file I need and a switch I need to give sane every time I want to scan. but the problem is that linux has no idea if this device is the thing it is or the other 12 models which exactly the same product and manufacturer id. (not linux fault really) but there is no satisfactory way to select what model it is and have all that configuration business taken care of for me.

---

### Post by Terracotta on 2006-08-28
> **bolerodan said:**
> thanks for the replys, however saying this to my friend:

"hey result from hardware manufacturers not writing drivers, writing poor drivers that are closed source, or not releasing specs so that the community can write drivers."

he will combat with "The manufactures arnt going to write crappy drivers.. THEY KNOW THEY'RE OWN HARDWARE, they made the thing, they arnt going to develop crappy drivers! The community writing drivers arnt going to be better then the actual manufactures writing drivers of their own hardware"
It's not like a company is ONE person that knows all, there are the persons that develop the hardware and write specifications for the software developers so they can write drivers. So the drivers are manufactured separate from the hardware based on documentation given by the hardware engineers. Now if the hardware engineers publish the documentations needed to write drivers open source developers know as much as the closed source developers so they both will write drivers that will perform equally as well.

Now the open model is far superior for several reasons:
1) Everybody can come in and look at the code and can improve the code where as with the closed model you'll have a few developers and hence you'll be stuck in the same way of thinking, more people leads to more different ideas what leads to better solutions popping up.

2)People working on graphics drivers for one company for example can use their expertise and work on graphics drivers for other companies.

3)Drivers for old hardware not supported anymore by the manufacturer can still be supported on linux.

If things work out of the box in linux they tend to be a lot easier and faster than in the windows world, if things don't work in linux they're a mess to get them working. (for example installing software from the repo's is easy as hell, installing from source uhuh right, hardware supported by the linux kernel works quite well and out of the box, installing drivers from source ugh right, (nvidia drivers are easy enough as well but that's because they are... in the repos)).

---

### Post by Terracotta on 2006-08-28
double post

---

### Post by .t. on 2006-08-28
Crappy drivers do cause crashes, but those are usually either the unmaintained, or the closed ones. Also, Linux has one of the best debuggers on the planet; the holy GDB!

And that makes my 400th post; or should I say bean...

---

