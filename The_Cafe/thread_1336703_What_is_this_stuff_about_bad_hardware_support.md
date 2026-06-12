---
title: "What is this stuff about bad hardware support?"
date: 2009-11-24
forum: The Cafe
---

### Post by fela on 2009-11-24
I've seen so many posts regarding bad hardware support of Linux/Ubuntu as opposed to Windows. I don't know why.

For example, I was hired by my Mum's friend to fix her Windows computer that had been riddled with viruses. Luckily she had a Windows installation CD so I went round there, Gentoo Linux system rescue CD in hand. It turned out her system really did need a full reinstall, as it would have been unrealistic trying to clean out all her viruses and have a usable system at the end of it.

So what do I do? The logical thing. I boot up the XP install CD. Everything seems to be going fine, it installs, I think 'yes, no problems...'. Big mistake.

It turns out when I boot the new installation, everything works except for, wait for it, internet. This is on a bog standard ethernet chipset, no wifi or anything like that (although I'd expect that to be detected too on an OS from 2007 - this is XP SP3).

So then I boot up my system rescue CD, configure the network with a simple [FONT="Courier New"]dhclient[/FONT], and the internet is up, albeit only on the livecd. So I start the X server and firefox, hoping to find the missing ETHERNET DRIVER (I kid you not) to enable the internet on Winderz.

Wait for it.

Her computer is a mish mash of components, pieced together from other components, and it's very old, and it doesn't have ANY manufacturer logos on it. Not even on the motherboard.

So now I'm in the situation where her computer has Windows XP SP3 on it but no ETHERNET DRIVER (I kid you not). Now what?

I tell her that I'm sorry, actually I apologize for Windows XP's *rubbish* hardware detection, and promptly leave having wasted 4+ hours desperately scouring the web for an unknown ethernet driver (it's already approaching dinner time aswell).

Couple of days later, I come back, my trusty, well, freshly burned Xubuntu 9.04 CD in hand (didn't bother with the sysresccd this time - no windows involved ;)). Start it up, no problems whatsoever...apart from, well, having to install the graphics driver to get the correct resolution. No big deal as the internet was already up and running as something so basic should be. Now it's running that as Windows is pretty much impossible to get running properly on it. It's an old AMD duron 1.2GHz machine by the way, with 256MiB RAM (ouch - that's alot!). And Geforce2 GPU - crazy fast card :)

OK, seeing as this is an anecdote I'm going to back it up with more evidence.

My computer is a custom build, Nvidia chipset Gigabyte mobo with Nvidia GF 9800GT (actually it's in my signature aswell). Everything works perfectly out of the box except the graphics driver which is a download away from Nvidia or the built in drivers manager. I expect this as it's not got anything fancy like wifi or a TV card or whatever.

I also have an LM technologies Wifi USB wireless chipset, also works perfectly OOTB (out-of-the-box) with Linux.

My dad's IBM Thinkpad laptop works completely, OOTB, with Linux too. Wifi, ATI card (compiz/hardware acceleration ootb) 'n' all. It took 12 hours, I kid you not, 12 freaking HOURS finding XP drivers for that that actually WORKED. When bought, it came with a clean and probably pirate copy of XP with no drivers at all on it, only basic functionality. The reason it took so long getting the XP drivers was because there were like 40 drivers for each lil bit of hardware that crapped themselves when run, and only 1 that actually did its job. Pretty poor experience compared with Install Linux > Do your Work.

OK, more evidence needed huh? I have a dell optiplex GX270 computer, works OOTB with Linux. I mean everything works OOTB, intel integrated GPU and everything. XP? Same situation as that laptop I'm afraid. Patterns start to emerge. Windows XP SP3 = rubbish hardware detection and if you don't know the manufacturer you're stuffed. Linux, well in my cases at least and the few other cases I've seen, = Install and go, basically. Either that or Install, get graphics driver, go.

The only case of poor hardware detection of Linux was on my dad's powermac G5. Although I can't really judge it as I only tried booting an old Linux distro (I think debian), might even of been using Linux 2.4, I forget. It was definitely a very old distro. I should try the latest Debian PPC on it to see if things have changed. Although Linux still beats Windows as Windows wouldn't even run on that machine.

Sorry if this has become a complete anti Windows rant. The point of this thread, before you ask, is to ask why so many people complain about bad Linux hardware support vs. good Windows hardware support, whereas I've seen the total opposite in mine and others' cases. I have not had a SINGLE instance of Linux not supporting my hardware, except that powermac G5.

Oh yeah, I run Linux on my server which is a very similar mobo to my computer, it has a Canon Pixma iP5300 printer which works perfectly and prints any document printed to it from Linux, Windows or OSX hosts over CUPS (+ Samba in windows' case), perfectly. Oh yeah, my mum's friend that I was talking about, she has a printer. It's an epson all-in-one printer, ya know the scanner+printer+copier all in one thingamebob. Worked OOTB, with Linux. Windows XP SP3 didn't even recognize that it was there. Shoddy, if you ask me.

Have a nice day.

---

### Post by earthpigg on 2009-11-24
to be fair:

you would need to compare hardware support of Windows XP (retail October 25, 2001) to hardware support of Debian 2.2 (August 2k) or 3.0 (July 2002).

Or, since that is looking into the Ancient Past and I am more interested in the future:

Compare Ubuntu 9.10 to Windows 7.

---

### Post by fela on 2009-11-24
> **earthpigg said:**
> to be fair:

you would need to compare hardware support of Windows XP (retail October 25, 2001) to hardware support of Debian 2.2 (August 2k) or 3.0 (July 2002).

So they don't add any drivers whatsoever in the service packs? If they do, then I should be comparing it strictly to Ubuntu 7.04 or 7.10 (it was 07 that SP3 was released, wasn't it?). I started using Ubuntu at version 7.04.

> Or, since that is looking into the Ancient Past and I am more interested in the future:

Compare Ubuntu 9.10 to Windows 7.

Well we have a clear winner. On the majority of the systems I listed, Windows 7 wouldn't begin to run on. Ubuntu 9.10 would run poorly on one of them (the old amd duron), but we have xubuntu for that.

On my computer which is new-ish, Windows 7 has the same level of hardware detection as Linux. Maybe it's finally caught up.

---

### Post by Skripka on 2009-11-24
Unless you're using a restore image CD/DVD for XP, OF COURSE IT DID NOT supply h/w drivers for **anything**.  IT NEVER HAS.  _It was NEVER designed to, or written to_.  It was designed to get you to a place where you could add drivers...unlike Ubuntu say, which has basic and generic drivers for most things included.


WinXP has always needed a driver for everything, when installing from an OEM disk.


The WinXP is NOT "shoddy".  It did what it was designed to.  Now, whether or not that is a good thing or not is another discussion.

---

### Post by fela on 2009-11-24
> **Skripka said:**
> Unless you're using a restore image CD/DVD for XP, OF COURSE IT DID NOT supply h/w drivers for anything.  IT NEVER HAS.  It was NEVER designed to, or written to.  It was designed to get you to a place where you could add drivers...unlike Ubuntu say, which has basic and generic drivers for most things included.


WinXP has always needed a driver for everything, when installing from an OEM disk.

...And that was the point of my post!

If what you say is true, and it obviously is, why do people complain about Linux having bad hardware support? More accurately, why did they when Windows XP was current?

---

### Post by juancarlospaco on 2009-11-24
> **earthpigg said:**
> 
you would need to compare hardware support of Windows XP (retail October 25, 2001) to hardware support of Debian 2.2 (August 2k)

Nah, because most Windows users stick with XP, older version,
and most Ubuntu Users sitck with newer versions.

---

### Post by Skripka on 2009-11-24
> **fela said:**
> ...And that was the point of my post!

If what you say is true, and it obviously is, why do people complain about Linux having bad hardware support? More accurately, why did they when Windows XP was current?

Why?

I have a USB microphone interface XLR->USB...Under Linux it is nothing more than a paperweight.  There is NO support for such devices at all really.  No drivers at all-even if you go looking.  Works fine under Windows/OSX.

**NONE** of the more fancy features of the on-motherboard sound system I have are available under Linux.    I get good sound, but all the more advanced features are absent.  They are right there in a Control Panel in Windows, after installing a driver off a disc.

It is situations like these that lead to Linux having a rep regarding h/w support.

---

### Post by earthpigg on 2009-11-24
doing the devils advocate thing because a counter-balance is needed. :D

i like and prefer GNU/Linux, but i do question some of the rationale...

> **fela said:**
> Well we have a clear winner. On the majority of the systems I listed, Windows 7 wouldn't begin to run on. Ubuntu 9.10 would run poorly on one of them (the old amd duron), but we have xubuntu for that.

On my computer which is new-ish, Windows 7 has the same level of hardware detection as Linux. Maybe it's finally caught up.

hmmmm... giving 'points' to ubuntu because it will run on hardware that Windows 7 will not run on seems a bit odd when the hardware in discussion ***isn't what Win7 was designed to run on.***

would you also ding points from Win7 in favor of Debian because Debian will run on PPC architecture and Win7 will not?

This would be the way I would phrase it:

> For economic, political, and a smattering of philosophical reasons, the interested parties behind Windows (MS, OEMs, and desktop/laptop computer retailers) put significantly less effort into supporting legacy hardware than the interested parties behind Ubuntu (An African dude with more than enough money to retire on and fewer stockholders to answer to, Debian, the FSF, and others).

---

### Post by hoppipolla on 2009-11-24
I've found hardware support is often fairly equal between Windows and Lin. I mean, most of my older hardware is more supported on Linux, and I can be assured of more predictable support. On Windows though, the latest hardware tends to be more supported because the companies release official drivers.

Windows may slightly have the upper hand, but I've had a rough time on there with drivers too.

---

### Post by Zoot7 on 2009-11-24
Well once it comes to "out of the box", there's no contest between Ubuntu and Windows, however once you install all the drivers with Windows, you'll generally find it's the latter that supports more devices.
And one thing you can't really refute is the fact that often the normal problems associated with Linux, generally go away once you use Windows. eg. Audio Problems, Video Problems, Patchy Wi-Fi. etc.

Don't get me wrong I'm pretty much amazed at the hardware support ever since I started dabbling with Ubuntu and other distros.
Pretty much every system I've installed Ubuntu on has picked up all the hardware effortlessly, with almost zero configuration on my part (the only exception being Video).
> **Skripka said:**
> **NONE** of the more fancy features of the on-motherboard sound system I have are available under Linux.    I get good sound, but all the more advanced features are absent.  They are right there in a Control Panel in Windows, after installing a driver off a disc..
Ditto that, there's a good few nifty power saving features that are Windows only for my board too.

---

### Post by Arup on 2009-11-24
I have a real expensive high end Yamaha pro sound card, since XPx64, there has been no drivers for it, same goes for my Genius tablet and Umax scanner, all these items work flawlessly from day one with SuSE and not Ubuntu since version 6.05 There are many hardware that don't work on Windows so the percetopn about hardware support being good is questionable. So far every bit of hardware I have thrown at Ubuntu has worked without any hitch. As for patchy wireless, never had that issue using wireless from Netgear, Linksys and Dlink. Bear in mind that most hardware manufacturers don't support Linux and therefore all the drivers are voluntary effort, having said that, I must commend on the wonderful job Linux volunteers have done so far. About problematic drivers, I had Creative drivers for my Live card giving me regular BSOD, have had some other hardware drivers in Windows doing the same as well. Least I don't get BSOD here in Linux.

---

### Post by 3rdalbum on 2009-11-24
> **Skripka said:**
> Unless you're using a restore image CD/DVD for XP, OF COURSE IT DID NOT supply h/w drivers for **anything**.  IT NEVER HAS.  _It was NEVER designed to, or written to_.

Microsoft reckons Windows XP contains 7,000 drivers, and that Vista contains 19,000. I never saw any evidence of that.

Windows 7 does actually contain some drivers. I was shocked when I installed Windows 7 onto a new computer for someone, and it actually already had drivers for everything except the video card.

Then I booted up Windows 7 with a different mouse plugged in. It didn't work until after about a minute, when it said it was installing device driver software... and then the mouse worked. Wow, how fantastic, Windows 7 was able to locate and install a driver for my completely ordinary, two-button-scroll-wheel mouse! </sarcasm>

---

### Post by alphaniner on 2009-11-24
I think Windows (XP at least) avoided providing drivers for things that were still being frequently released by the manufacturers.  A few older NICs (including even some Gbit), tape drives and tape autoloaders are among the things I've seen auto-configured.  Not to mention monitors (specifically, the resolutions they are capable of).

---

### Post by ICB on 2009-11-26
I've just tried installing Xubuntu karmic on a PIII 667, it's failed to recognize that it even has a CD drive, NIC and wifi card installed let along configure a driver for them.  2 of these 3 were working fine under XP out of the box and the wifi was easy to set up with the mfr's driver.

This is a disappointing departure from experience with hardy on more recent hardware where it did a great job to the extent that it even configured the card reader and scanner on an HP multifunction printer.

---

### Post by clanky on 2009-11-26
The reason people think that hardware support for Windows is so much better for Windows than it is with Linux is that most peoples experience with Windows is as a pre-installed OS, or even when doing a re-install it is usually with a system restore disc designed for that PC specifically, whereas most peoples' experience of Linux is downloading an image off the interwebs and then spending ages trying to get their computer to work.

In my experience Windows hardware support is generally better than Linux in as much as there is more hardware that Windows will run in the way it was designed to run than there is for Linux and in that it is easier to find / install drivers for windows than for Linux, however the gap is nowhere near as big as some people make it out to be.

For me this is just one more reason why the way forward for Linux has to be pre-installed, it is a shame that the EE-PC or whatever it was called didn't take off more, that could have really been a turning point for Linux, hopefully the failure of that particular experiment won't signal the end of PC manufacturers offering (and marketing) pre-installed Linux.

One of the other issues which Linux has that Windows doesn't is the upgrades, most people buy a computer with one version of Windows and keep that version for the life of the computer, those who tried to upgrade from win95 to XP had driver problems, likewise the poor souls who upgraded from XP to Vista, but this is a fairly rare case, most windows users don't upgrade.

You only have to look at the forums here to see how many people end up having driver issues when they upgrade from one release to the next which is much more common practice in Linux.

---

### Post by madnessjack on 2009-11-26
My experiences with Windows XP have been alrite. I do a clean   install, fish the driver CD that comes with the motherboard and it's all   done.
    With Ubuntu I've haven't had the joy of everything working straight away.   For a start the FOSS/Open source morals nature/thing requires me to add proprietary drivers manually (i don't want to argue this point, i can easily   see why this is the case). I've had to fish my wifi drivers out, then search   the internet on a Windows computer to figure out how to configure ndis using   lines of commands i don't understand.
    Obviously it'll work for some people, and for others is won't. I can't see   how you're surprised that people can't get it working. Not everyone shares   your experiences.

---

### Post by Zoot7 on 2009-11-26
Depends on the hardware really. If you make sure all your hardware is Linux friendly, then you can easily have an Mac like experience with stuff, ie. it *just* works.

---

### Post by fela on 2009-11-26
> **earthpigg said:**
> would you also ding points from Win7 in favor of Debian because Debian will run on PPC architecture and Win7 will not?

Er, yeah. Wouldn't you?

---

### Post by fela on 2009-11-26
> **madnessjack said:**
> fish the driver CD that comes with the motherboard and it's all   done.

my point exactly.

Microsoft doesn't bother to make drivers for anything, whereas Linux devs spend a massive chunk of their time making and testing drivers.

---

### Post by fela on 2009-11-26
> **hoppipolla said:**
> I've found hardware support is often fairly equal between Windows and Lin. I mean, most of my older hardware is more supported on Linux, and I can be assured of more predictable support. On Windows though, the latest hardware tends to be more supported because the companies release official drivers.

Windows may slightly have the upper hand, but I've had a rough time on there with drivers too.

Remember, I'm talking about autodetection, not whatever drivers MS-worshipping companies have produced out of their rear ends.

---

### Post by madnessjack on 2009-11-27
> **fela said:**
> my point exactly.

Microsoft doesn't bother to make drivers for anything, whereas Linux devs spend a massive chunk of their time making and testing drivers.

It's irrelevant! End users don't care about the politics, the why or the how. Hardware manufacturers make their hardware work for Windows. That's the answer to this thread. Life's a bitch ain't it?

---

### Post by Bachstelze on 2009-11-27
Get the PCIID of the device from the device manager, search Google for it, done.

Who called himself a "computer expert" again?

---

### Post by kpholmes on 2009-11-27
my printer is set up on my debian server as well, its printable by all the computers on the network. AND.. it worked out of the box with linux.  other then my experiences i have hear a lot of shotty linux printer support, but haven't expierencies it my self, as i only have 1 printer.

---

### Post by Psumi on 2009-11-27
My Canon MP190 does not work out of the box.

In fact, I have to install an old-release package (cupsys2 transition package) to get the canon drivers from canon-europe to even work.

This is the ONLY way to get the scanning function to work easily. Otherwise I have to compile an xsane git, which I cannot do anymore ever since they moved their site around to make it harder to get.

Furthermore, I have to force architecture if I am using x64,because the drivers are ONLY made for i386.

There is one hardware problem for me. Another one...

Nextly, if I go to Hardy LTS, I cannot install nvidia drivers, they will not work properly. Even the newest ones, 190 will cause compiz never to activate due to the fact jockey cannot tell if there are nvidia drivers. It was only by luck that I got compiz to activate on Hardy and I cannot do it again.

Furthermore, my Intel Core 2 Duo cannot be clocked in a way that it gets 2.8 GHz. No, Ubuntu says both cores are at 2.0 GHz rather than what the BIOS says they are (2.8 GHz.) So I had to break down and set the cores to 3.0 GHz.

---

### Post by fela on 2009-11-29
> **Bachstelze said:**
> Get the PCIID of the device from the device manager, search Google for it, done.

Who called himself a "computer expert" again?

What if you have no internet access because of no drivers, and the only way you can get it is by going back to your house 5 miles away, on a push bike?

---

### Post by fela on 2009-11-29
> **Psumi said:**
> Furthermore, my Intel Core 2 Duo cannot be clocked in a way that it gets 2.8 GHz. No, Ubuntu says both cores are at 2.0 GHz rather than what the BIOS says they are (2.8 GHz.) So I had to break down and set the cores to 3.0 GHz.

That's an Ubuntu/Linux bug. You can just clock your CPU at 2.8 and forget about it. If the BIOS says it's at 2.8GHz it's either at 2.8GHz or there's a BIOS bug. Ignore what Ubuntu/Linux says if it has a bug like that.

---

### Post by Psumi on 2009-11-29
> **fela said:**
> That's an Ubuntu/Linux bug. You can just clock your CPU at 2.8 and forget about it. If the BIOS says it's at 2.8GHz it's either at 2.8GHz or there's a BIOS bug. Ignore what Ubuntu/Linux says if it has a bug like that.

The problem is, Windows said it was at 2.8 GHz, and it felt like 3 GHz. But with Ubuntu, it felt like 2.0 GHz when Ubuntu said 2.0 GHz.

---

### Post by fela on 2009-11-29
> **Psumi said:**
> The problem is, Windows said it was at 2.8 GHz, and it felt like 3 GHz. But with Ubuntu, it felt like 2.0 GHz when Ubuntu said 2.0 GHz.

Do you really expect me to take a post like that seriously?

OK, it FELT like it was running at 2.0 GHz so it MUST be running at 2.0 GHz! It FELT like it was 3.0 GHz so obviously it's 3.0 GHz!

You can't feel CPU frequency. It just doesn't work like that. To measure it against another frequency (relatively speaking) accurately, you'd have to use a benchmark that uses alot of the CPU and not much of anything else. You can't just say it 'felt' like a certain speed because there's too many things to take into account, for example, Ubuntu might have been running an indexing service or whatnot, in the background, or maybe in Ubuntu the scheduler is more optimized for background tasks. Saying a CPU must be a certain speed because the computer does certain tasks with certain delays just doesn't add up.

---

### Post by toupeiro on 2009-11-29
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

Seems like I'm posting this a lot lately.  Its a great source for hardware thats been proven functional and rated in ubuntu.  Use it, contribute to it!

---

