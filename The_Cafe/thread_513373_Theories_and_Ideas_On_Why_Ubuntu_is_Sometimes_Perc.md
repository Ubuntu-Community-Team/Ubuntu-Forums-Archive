---
title: "Theories and Ideas On Why Ubuntu is Sometimes Perceived Slow"
date: 2007-07-30
forum: The Cafe
---

### Post by blueturtl on 2007-07-30
Every now and then some people claim in a forum post that Ubuntu runs slower on the same system as say Windows XP. Now there are at least as many or more who will say Ubuntu runs faster especially after the system has been running for some time.

Gathering bits of information here and there I have come up with explanations for the supposed sluggishness of Ubuntu.

1. The installed system has a hardware detection problem.
This is actually quite common on new systems and especially laptops. The kernel fails to identify some hardware and it either causes the hang-ups or then the hardware features are not fully utilized. This is actually a fault but sometimes the hardware simply can't be supported (closed spesifications, etc).

2. The graphics subsystems seem unresponsive compared to Windows.
This can be partly due to #1 (unaccelerated graphics) but it is often also an unfair comparison. The explorer shell is probably lighter because among other things it lacks many of the features of the Gnome and KDE desktop environments. We all know that Linux gives you more power for your clock cycles but let's be realistic, some things simply do require more and no amount of optimization will make a system with more functionality outperform one with less.

3. Loading apps/data takes longer than in Windows.
Again this can be #1 (DMA not enabled, etc) but I've also deviced a theory that this has to do with the way Linux handles hard-disks and files. I believe it has everything to do with how low disk fragmentation is achieved in Linux. The files on the hard-disk are more spread out in order to minimize devision into several fragments when files are modified later. This works wonders in the long run but causes the system to appear less responsive compared to a fresh installation of Windows. Windows piles up the files one after the other filling up the volume from start to end. The advantage is that in the beginning all the files are in single locations and physically very near each other on the disk. This reduces hard-disk seeks and therefore load time. Since hard-disk is the slowest component in the entire system this can make a dramatic difference in first impressions. Especially systems with slow hard-disks and little memory might look bad for Ubuntu. It is my belief however that once disk fragmentation increases in a Windows system the load times increase and the illusion of faster hard-disk performance breaks down.

Comment away...

---

### Post by SunnyRabbiera on 2007-07-30
actually ubuntu is pretty slow overall to me, compared to the lightning fast PCLOS that I am on now

---

### Post by LaRoza on 2007-07-30
Maybe because they are running Beryl half the time.

-EDIT Ubuntu isn't the fastest, but on a modern computer, it is a pretty good balance.

---

### Post by rich.bradshaw on 2007-07-30
I have always found that Ubuntu boots much slower - but this is because hibernate doesn't work on my laptop. Because I normally just resume from hibernate, booting from scratch in Ubuntu seems a lot slower.

To someone who doesn't know about the terminology here it would seem as if Ubuntu was slower.

---

### Post by SunnyRabbiera on 2007-07-30
it all depends I guess, but my compy doesnt have a lot of memory on her (only 252 MB) but for an odd reason PCLOS lightning even with KDE...
Ubuntu with KDE= snailspace

---

### Post by scooper on 2007-07-30
This is the opposite of my experience.

I've been through many dual boot Linux/Ubuntu/Windows setups on different hardware.  After normal tuning of the Linux side (with Nividia driver, DMA, etc) and after Windows has been used for a reasonable period (months), I've never had Linux/Ubuntu perform worse than Windows.  I always drop Beryl after playing with it.  Too much screen noise.  Booting of Windows starts off fast, but always ends up much slower after the requisite anti-virus and other crap is installed.  P2P networking performance is also much worse without a special unapproved hack.

Despite the recent moaning of the kernel developer, I also find multitasking immensely smoother under Linux.  There are many more occasions in Windows where the system becomes unresponsive.

Probably freshly-installed "demo" systems will show Windows running better.  But 90% of real world setups won't be that way.

---

### Post by Alex Fernandez on 2007-07-30
I find that Ubuntu installed from the net install mini.iso and then with only the packages I want (KDE, etc) installed via apt-get is alot faster feeling than a default livecd install.

---

### Post by phrostbyte on 2007-07-30
My observations on speed:
All OSes are pretty much stock.
Higher is better.

Bootup time:
Windows XP > Ubuntu > Windows Vista

Shutdown time:
Ubuntu > Windows XP > Windows Vista

OpenOffice:
Ubuntu > Windows XP > Windows Vista

Firefox:
Windows XP > Windows Vista > Ubuntu

Wifi Speed:
Ubuntu > Windows XP > Windows Vista

Memory Usage:
Windows XP > Ubuntu > Windows Vista

---

### Post by FuturePilot on 2007-07-30
Regarding #3 certain programs might take longer to load in Ubuntu than Windows because Windows pre-loads a bunch of stuff at boot up. That's why say MS Office loads faster than Open Office. That may seem like a good idea, but that's one of the big reasons Windows gets slower and slower the more stuff you install.

Nevertheless, Firefox loads faster in Feisty (even on the first time after boot) than on any other OS.\\:D/

---

### Post by stmiller on 2007-07-30
Feisty boots faster than Edgy. In Edgy, all sorts of services were loading and running which most people don't need. Including PCMCIA, RAID, and others. Most people don't know how to turn these off, or even knew they were running.

---

### Post by Dimitriid on 2007-07-30
Honestly, its a matter of an unfair comparison: Ubuntu is often compared to XP, when in reality it should be compared to Vista in which case we can easily say Ubuntu blows Vista out of the water on all these things ( speed, boot up, shut down, apps, etc )

A more fair comparison perhaps could be **X**ubuntu vs XP : Both are a bit more primitive, have less options to customize and change the "look" than the more modern counterparts but are considerably less resource intensive.

On this test of course Xubuntu imho again is much better than XP: On all these things and you can still use Compiz Fusion + Emerald + XFCE to get amazing looks with little or NO impact on a suited machine ( 512mb or so ram, maybe 128mb dedicated recent videocard, like an Nvidia 6200 maybe ) and if the machine is not up to the task it can still run on a decent level of performance ( more or less 256mb ram to have a good experience on both Xubuntu and Xp, 512 making it ideal, etc. )

---

### Post by misfitpierce on 2007-07-30
I find my install of ubuntu 64 bit to be extra speedy... It is lightning fast and I have not 1 problem.

---

### Post by jgrabham on 2007-07-30
For me (specs in sig) Ubuntu is several times faster than windows to boot.

Also, are these people counting the fact that windows takes half an hour to start antivirus, firewall, sound, etc after they logged in?

---

### Post by DoctorMO on 2007-07-30
The more the ubuntu bootup manager gets away from the catch all loading that loads services not everyone needs the better. obviously this was also something modulisation of the kernel was suppose to help with, but it doesn't help if you just load all available modules anyway ;-) I've found ubuntu to be quite quick, it can get hang ups about the network, or the video card or even sometimes mice. but fix those problems and it's quite nippy.

---

### Post by handy on 2007-07-30
People can waste a LOT of time, being concerned by a few seconds here & a few seconds there on loading & closing software!

Speed truly matters when it effects how your software *functions*.  For most people these days, I would think that high level 3D games would be the only concern re, speed. 

 Apparently Sabayon is much faster than Ubuntu or any other OS when it comes to playing Oblivion.  I can't speak from experience on that yet, I won't get my copy of Oblivion until later this week.

I will submit feedback in the games forum.

---

### Post by init1 on 2007-07-30
Ubuntu is about as fast as I could want.

---

### Post by Ace2016 on 2007-07-31
I use ubuntu with initng as init and it feels a lot faster during the startup, and i also like to see the cool coloured text scroll. Beryl + XGL make the windows very responsive and make the desktop feel much smoother. The strange thing is that beryl sucks without xgl as the xserver, its truely SLOW but when xgl is there there is a massive difference in performance. Not sure why most people with nvidia cards run beryl on plain X but XGL is important even on an nvidia card if you want speed

I don't quite know why you think xp is fast on the desktop after the first install, i always find that without the nvidia driver i can't even move the windows properly without it lagging.

---

### Post by 3rdalbum on 2007-07-31
Ubuntu is perceived as slow because it comes with a whole bunch of services enabled that ordinary desktop users don't need.

By comparison, Windows XP Home doesn't - you'd have to pay for those extra services.

Also, be aware that the latest Ubuntu is many years newer than Windows XP - and the newer the software, the bigger it is.

If you add the usual suspects of anti-spyware, anti-virus, etc to Windows though, to make it usable, you lose all your speed advantages.

---

### Post by Saner on 2007-07-31
I find it pretty quick to be honest, but I have compiled my own kernel and removed all the junk I don't want or need.

But I didnt find it paticually slow when I first installed.

---

### Post by SlayerMan on 2007-07-31
First, I have to second the opinion that Windows feels faster and more responsive on most systems. I'm talking about a bare, fresh installation of Windows and Ubuntu. If you try to make Windows as secure as Ubuntu (and GNU/Linux in general), you have to install lots of third party software such as virus scanners, personal firewalls etc. If you do that, Windows gets a whole lot slower than Ubuntu.

Second, I read somewhere that Microsoft has a dedicated performance team which has only one task: make Windows as fast as possible. If the community wants Ubuntu to be faster, it has to to concentrate more on performance. Currently, the main focus seems to be on reliability and making the apps feature-rich (which is also not a bad thing IMHO).

---

### Post by graabein on 2007-07-31
Ubuntu boots slow on my desktop computer. I think it always has...



Windows XP (dual boot) is even slower though. I just feel Ubuntu should be faster than it is. Maybe it's gotten slower with the last versions?

---

### Post by argie on 2007-07-31
I know one thing. In XP, the programs have only like one icon for the folder in the Start » Programs list. In Ubuntu on slower systems, there's a short pause while the icons load (in Gnome atleast) and that makes things look slower.

---

### Post by graabein on 2007-07-31
> **argie said:**
> I know one thing. In XP, the programs have only like one icon for the folder in the Start » Programs list. In Ubuntu on slower systems, there's a short pause while the icons load (in Gnome atleast) and that makes things look slower.

Yeah man this has bothered me for ages. How come they can't preload the icons or something so they pop up with the menu and not a split second later. Just looks so unprofessional.

---

### Post by argie on 2007-07-31
> **graabein said:**
> Yeah man this has bothered me for ages. How come they can't preload the icons or something so they pop up with the menu and not a split second later. Just looks so unprofessional.

I agree completely. It's a bit of a 'yuck' factor.

---

### Post by vexorian on 2007-07-31
This is complicated.

-I do know that some SATA HD got tough issues in the drivers/etc.
-Then there is a wifi driver that is known to absolutely freeze everything.
-People like cool things so they might like to run beryl all the time, which for some comps is a really slow down cause

Regarding boot times, I once measured the time it takes from the computer to turn on until the computer is ready to be used (there's a big delay in windows after your session starts in which you cannot do anything) 

windows XP SP2 : 2 minutes
Feisty: 1 minute 23 seconds

Overall things like menus and windows are much faster in this computer on ubuntu than windows, in fact, even with compiz-fusion the interface was faster than XP.

I think it is because my graphics card is probably one of the ones that got the best working drivers.

..
Regarding menu icons, I think it would be a little faster, and also look better if gnome loaded the icons before showing the menu block, I think this should really be suggested. There should be no calls to update before the menu is rendered completely...

---

### Post by raul_ on 2007-07-31
>  Theories and Ideas On Why Ubuntu is Sometimes Perceived Slow

Because when compared to (some) other distros it is :)

Ubuntu loads a lot of unneeded things so it can recognize as much hardware as possible, and it comes with a lot of applications, so it gets bloated. I'm using Arch, and the idea is completely different: you build your distro from scratch. It's really cool because you know exactly what's going on in your computer :) and Arch is i686 optimized, so it's bullet fast. Ok, enough advertising :)

---

### Post by vexorian on 2007-07-31
Installing an application will not make your computer slower unless you run it...

---

### Post by HermanAB on 2007-07-31
Hmm, I always turn off a zoo of daemons after installing Linux (any version).  I guess it takes a little bit of experience to know which daemons are not useful, but I always turn off crap like the Microsoft Auto DNS, Bluetooth, At Daemon, and so on - typically about 10 daemons are just a total waste.  Some distributions will install Apache and let it run whether you wanted it or not, slowing any desktop machine down to a crawl.

If you want raw speed, then you have to switch to a simpler window manager.  KDE and Gnome both run great on IceWM and horribly slow on their own bloated window managers.  Beryl and Compiz are also a total waste of resources - nice for 5 minutes of playing around, but best disabled thereafter.

Cheers,

Herman

---

### Post by nrs on 2007-07-31
Because in at least some areas it is. 

If I were coming from Windows, the first thing that would strike me would be the slow load time, at least compared to Windows XP. However, a Vista comparison would be more accurate and fair. 

Secondly, GTK+ has notorious resize/redraw issues that will greatly amplify any **perceived** slowness in other areas. This isn't really a Linux problem, as far as I can tell. KDE/Qt don't seem to suffer from this at all.

---

### Post by Shadows_Fall on 2007-07-31
Right now I'm not so happy with Ubuntu, as it's taken about five and a half hours for it to install on my laptop...

( 1.20 ghz, 256 ram, 20 gb hdd )

Oh and did I mention, I'm waiting for step four of the install process to come up?

Edit: I stand corrected, it's just finishing loading the partitioner, and is still loading the, "how do you want to partition the disk" screen...

---

### Post by vexorian on 2007-07-31
> **Shadows_Fall said:**
> Right now I'm not so happy with Ubuntu, as it's taken about five and a half hours for it to install on my laptop...

( 1.20 ghz, 256 ram, 20 gb hdd )

Oh and did I mention, I'm waiting for step four of the install process to come up?

Edit: I stand corrected, it's just finishing loading the partitioner, and is still loading the, "how do you want to partition the disk" screen...
It usually takes a lot of time if you are using another language and ubuntu didn't come with it and then it begins downloading language packages, so please don't make an opera out of it.

---

### Post by Shadows_Fall on 2007-07-31
Ok for number one, I'm using ENG, and it doesn't even have a connection. And for number two, I believe I have the right to be a little mad when it takes five hours to install an OS.

---

### Post by vexorian on 2007-07-31
Ah I didn't see your edit when I was typing last post.

5 hours for the partitioner to load means that it had a hard time trying to load your hard drive, it is probably a wrongly supported one, I would simply give up the installation and wait another year for more luck, or battle dragons and try to make it work correctly, if installer is having issues the OS will also have them.

---

### Post by Shadows_Fall on 2007-07-31
Well I keep hoping I just have a very slow CD drive,
as I've wanted to put Linix on my laptop for a few years,
but with all of the different distros, I kept putting it off,
up to now, and I like Ubuntu. But I guess I'll see if I get a laptop
with linix on it or not... Sometime today...

---

### Post by handy on 2007-07-31
If you find that Ubuntu doesn't support your hardware, you might want to try looking at some other distro's.  You could ask on their forums if anyone has had success with your model notebook before possibly wasting your time.  PC-BSD is worth a look too.

Your LiveCD experience was ok?

You could use [***_Distrowatch_***]("http://distrowatch.com/") to find info' & links to forums of different distro's & OS's.

---

### Post by HermanAB on 2007-07-31
How many hours???  There is something wrong.  Linux (any distribution) should install in about 45 minutes on a machine like that.

If it consistently screws up with Ubuntu, then you should try a different distribution, eg. Mandriva or Fedora.  The install process is extremely hardware dependent and each distribution has a different method to figure out what hardware you got.  

The distribution with the best wizards, is still Mandriva - Ubuntu comes a close second, Fedora a more distant third and the worst is Slackware (not recommended for ordinary mortals!).

'Hope that helps!

Herman.

---

### Post by juxtaposed on 2007-07-31
> Theories and Ideas On Why Ubuntu is Sometimes Perceived Slow

Because it is. It's slower then debian for me.

> People can waste a LOT of time, being concerned by a few seconds here & a few seconds there on loading & closing software!

Speed truly matters when it effects how your software functions. For most people these days, I would think that high level 3D games would be the only concern re, speed. 

Yea. Startup speed isn't a big deal to me (within reason), I want my OS to feel fast most of all.

---

### Post by lisati on 2007-07-31
> **FuturePilot said:**
> Regarding #3 certain programs might take longer to load in Ubuntu than Windows because Windows pre-loads a bunch of stuff at boot up. That's why say MS Office loads faster than Open Office. That may seem like a good idea, but that's one of the big reasons Windows gets slower and slower the more stuff you install.

Nevertheless, Firefox loads faster in Feisty (even on the first time after boot) than on any other OS.\\:D/

The downside of Windoze (or whatever) preloading stuff is that depending on what (and how much) gets loaded, it can slow the boot process. When loading XP Home on my desktop, it sometimes seems to take forever and occasionally gives the appearance of freezing.... my older Win98SE machine is particularly horrible and the WiFI I set up on it is easily thrown off balance.

---

### Post by Shadows_Fall on 2007-07-31
> **handy said:**
> If you find that Ubuntu doesn't support your hardware, you might want to try looking at some other distro's.  You could ask on their forums if anyone has had success with your model notebook before possibly wasting your time.  PC-BSD is worth a look too.

Your LiveCD experience was ok?

You could use [***_Distrowatch_***]("http://distrowatch.com/") to find info' & links to forums of different distro's & OS's.

No the liveCD was horrible, it had to read the disk for 2 seconds every time I moved my mouse. So I take it this is a good sign, a sign that my CD drive sucks, and is only going 4-8X.

It's been about eight hours now, and it's loading step seven, I believe,
the step after it allows you to import accounts.

I had to wait one or two hours for it to load, only to click next...

---

### Post by juxtaposed on 2007-07-31
> It's been about eight hours now, and it's loading step seven, I believe,
the step after it allows you to import accounts.

I had to wait one or two hours for it to load, only to click next...

Thats really odd. Ubuntu installs really fast for me. It's like 20 minutes or so. Much faster then when it used the debian installer.

---

### Post by HermanAB on 2007-07-31
Shadows: As I said before, there is something wrong with this setup.  Chances are that you shall wait days for the install to complete, only to find that it won't run anyway.  If it was me, I would have rebooted 7 hours ago already.

I guess that you are only waiting for the install as a kind of (non)mental exercise...

---

### Post by Shadows_Fall on 2007-07-31
> **HermanAB said:**
> Shadows: As I said before, there is something wrong with this setup.  Chances are that you shall wait days for the install to complete, only to find that it won't run anyway.  If it was me, I would have rebooted 7 hours ago already.

I guess that you are only waiting for the install as a kind of (non)mental exercise...

Well I have no use for my laptop, as the battery died, so I don't care if it takes it two days. Also I'm curious about Linux, and want to try it out.
So it'll install it and it'll like it. lol

Plus it's like I said, I think my CDROM is crappy, so I'm hoping I'll run fine, once it's on the HDD. If not then that's fine, I'll look for a different distro, and try my luck with it.

---

### Post by handy on 2007-08-01
> **Shadows_Fall said:**
> Well I have no use for my laptop, as the battery died, so I don't care if it takes it two days. Also I'm curious about Linux, and want to try it out.
So it'll install it and it'll like it. lol

Plus it's like I said, I think my CDROM is crappy, so I'm hoping I'll run fine, once it's on the HDD. If not then that's fine, I'll look for a different distro, and try my luck with it.

I expect that you will search for a distro' that has the lowest hardware requirements. :)

---

### Post by aysiu on 2007-08-01
I think there are too many factors involved here:
Hardware support--optimization with certain drivers
Preloading of applications in Windows
Bogged down Windows
Variation among Linux distros
Desktop environment used (Gnome, KDE, Xfce... or window manager like IceWM or Fluxbox)
Applications used (Quod Libet instead of Rhythmbox, Galeon instead of Firefox, etc.)

---

