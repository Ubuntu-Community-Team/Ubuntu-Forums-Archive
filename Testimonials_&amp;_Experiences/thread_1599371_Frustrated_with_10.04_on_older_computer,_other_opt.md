---
title: "Frustrated with 10.04 on older computer, other options?"
date: 2010-10-17
forum: Testimonials &amp; Experiences
---

### Post by aeronutt on 2010-10-17
After ~12 hours of trying to get 10.04LTS installed and working on my Mom's (old)computer, I've just about given up. Slow boot, printer won't work, sound won't work, somehow I've added a few things to the top panel that I now can't delete, and more often than not, the window that opens when installing s/w hangs after it's finished, and graphics seems all miffed up. (FYI, 9.10 was working great, but w/o LTS, I'd rather not revert to 9.10).

Just too much stuff to expect my Mother to deal with. And I have no confidence that once I leave, major problems won't happen during a security patch etc, that will cause her to not be connected.

Is there another version of Linux that might work better on older hardware, that is stable, and has 2-3 or more years of support for a particular version? And, uses gnome so the interface will look familiar to my Mom?  Basically, she uses it for browsing via Firefox, and printing. That's really it.

This isn't meant as a rant, just the facts as they are, and hope that another version may be better for this particular use.

---

### Post by Rahul dev on 2010-10-17
ubuntu 10.10 is better than 10.4 in processing speed , you should install it.

---

### Post by TBABill on 2010-10-17
PCLinuxOS is a great, easy distro to use. It's Gnome version is ok and it is rolling release, but not a "risky" rolling release. Updates seem to be well tested before release and breakages are fixed very quickly. The forums are very helpful as well. But, they don't have a specific "LTS" version. The "current" is just kept up to date until further updating will require reinstallation of the OS to a new version. 2010 was an example of that. But it's easy to do and easy to learn.

It's an RPM based distro but it uses Synaptic just like Ubuntu. And to update all you do is go into Synaptic, click "reload", then click "mark all upgrades", click "Apply" then close it. That's it. Same with adding software...just use Synaptic. If she is familiar with it already it's an easy transition and the RPM/DEB difference becomes practically nothing for her usage.

PCLinusOS is kinda like Mint on the RPM side. So simple and it takes a lot from Mandriva, Mint, Fedora and other distros, but it's not based on any other distro. [http://www.pclinuxos.com](http://www.pclinuxos.com)

---

### Post by sanderd17 on 2010-10-17
I don't think you have problems with your computer being on an old computer (since 9.10 runs on it) but I think you have problems with drivers.

Maybe the ideal for you would be a rolling release. There aren't many rolling releases but I think Linux Mint Debian Edition (LMDE) will become a good one. I'm going to test it in Virtualbox, Let's see how it goes.

I don't yet know if LMDE comes with a lot of bloat but the advantage is: when you removed the bloat once, you don't have to reinstall it.

If you really want an OS for an old computer, try Lubuntu. You can use the same programs as in Ubuntu so your mother doesn't have to change that much.

---

### Post by TBABill on 2010-10-17
Rahul dev I would respectfully disagree. There are far more wireless, video and other posts to the forum for 10.10 than I have seen in a while. Until those problems are worked out I would caution against recommending it to someone who is trying to solve his mother's computer problems. Until it is stabilized it is probably a poor choice unless he can test it on the machine thoroughly and be willing to return in case any of the obviously needed "fixes" are downloaded and installed without further problem.

Just my 2 cents, but since it is for a computer user who may not be capable of dealing with problems on the machine, 10.10 may be a bit much for now. I found no additional speed on 10.10 and 10.04 is very quick, but each machine responds to distros differently.

---

### Post by marshmallow1304 on 2010-10-17
I'd give Debian Stable a shot.  It doesn't have a lot of frills to slow things down and it's rock solid.

---

### Post by sanderd17 on 2010-10-17
> **marshmallow1304 said:**
> I'd give Debian Stable a shot.  It doesn't have a lot of frills to slow things down and it's rock solid.

Do you have a good howto to install a debian gnome environment?

I'm always scared if I look at the number of CD's and how you need to set up everything.

I believe Debian stable is rock solid but I think it's difficult to set up, am I right?

---

### Post by aeronutt on 2010-10-17
Good ideas folks, I appreciate the input and discussion.
I think a rolling release would be problematic. One thing I didn't mention, I'm only home to update Mom's computer about once every 3-4 months, and I don't want to have to spend hours at the computer when I'm home. That's why I was excited about 10.04 LTS. And no, I don't think I'd be interested in 10.10 right now.

---

### Post by spcwingo on 2010-10-17
> **sanderd17 said:**
> Do you have a good howto to install a debian gnome environment?

I'm always scared if I look at the number of CD's and how you need to set up everything.

I believe Debian stable is rock solid but I think it's difficult to set up, am I right?

You only need the first CD and you're given the option at install time if you want a desktop environment (GNOME) or not.

---

### Post by eveningsky339 on 2010-10-17
The latest version of Puppy Linux is code-named "Lucid" because it is compatible with Lucid Lynx binaries.  It is a distro tailored to older computers so you may have better luck with it.  Not exactly a user-friendly installation, but if you know your way around GParted, you should be all set.

---

### Post by hlpguru on 2010-10-17
Yeah I'm using ubuntu today with a version of 10.10.

---

### Post by leclerc65 on 2010-10-18
Lubuntu 10.04 works well for me (very old laptop where nothing works: XP, Ubuntu 10.04 ...).

---

### Post by cascade9 on 2010-10-18
> **sanderd17 said:**
> I'm always scared if I look at the number of CD's and how you need to set up everything.

I believe Debian stable is rock solid but I think it's difficult to set up, am I right?

Well, you dont need to setup 'everything', and what sertting up you do need itsnt that bad. Mind you, I know more than a few people who would disagree on that, mainly people who cant manage to install the nVidia/ATI drivers (not that you need to do that, but still....). 

BTW, squeeze is currently in a 'freeze' and its going to end up being the new stable sooner or later. It might save time and effort to just install squeeze now and avoid all the updating from lenny-> squeeze that will happen at some point. Juist make sure the repos are listed as 'squeeze' not 'testing'. ;)

---

### Post by GeeLo on 2010-10-18
> **Rahul dev said:**
> ubuntu 10.10 is better than 10.4 in processing speed , you should install it.


I 100% agree with Rahul post..

---

### Post by mastablasta on 2010-10-19
> **sanderd17 said:**
>  
I'm always scared if I look at the number of CD's and how you need to set up everything.
 
 
they also have this Debian live project or something like that that offers a live CD so oyu can test before you install if things work.

---

### Post by Spice Weasel on 2010-10-19
Why are you trying GNOME on an older computer? You'd be much better off with something like Openbox or if you need a desktop environment then LXDE or XFCE (NOT XUBUNTU. It's actually heavier than regular Ubuntu. I recommend Debian with XFCE/LXDE.).

---

### Post by mastablasta on 2010-10-19
slowness was not an issue as i understand. so since we don't know how old it is...
i have a box from arround 1998 yet it was constantly upgraded. one might say old ocmputer. but works quite well with installed XP.

---

### Post by 3Miro on 2010-10-19
CentOS is a current distribution that packages mostly outdated software (with security patches, so don't think it is unsecure). The advantage is that CentOS is probably the most stable distro out there and it run very well on old P4 computers. It is, however, harder to install then Ubuntu and I am not sure if they come with the drivers that you might need.

---

### Post by aeronutt on 2010-10-19
> **mastablasta said:**
> slowness was not an issue as i understand. so since we don't know how old it is...
i have a box from arround 1998 yet it was constantly upgraded. one might say old ocmputer. but works quite well with installed XP.

FYI, 9.10 worked fine, and once it boots in 10.04, gnome works fine (with some exceptions; eg panels didn't work at first). Bottom line, the speed of using gnome isn't an issue.  And here's an output of lspci, if that helps define how old it is.

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory 
Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics 
Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
01:09.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
```

---

### Post by mastablasta on 2010-10-20
> 00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics 
Controller 
 
This is your GPU and it probbaly the one to be causing the issues. Intel has poor linux support. also their chips are crapy.
 
BTW lspci only gives list of PCI devices. it doesn't say much about processing power or ram of the computer.
cpuid will show processor
top will show ram
 
the information are also available in the Ubuntu system monitor.
 
edit: also make sure you have enough disk space and that it is propperly partitioned.

---

### Post by klemes on 2010-10-20
> Intel has poor linux support. also their chips are crapy

I could not disagree more with this .I succesfully run Intel chipsets in three of my computers (a Debian P4, a 945GM Core 2 Duo laptop running 10.04 and a similar configured desktop with 9.10) and I have ran into zero problems.
I have also enabled the x-swat repositories (note not the x-edgers one) and have continuous update of the video drivers.
Also Intel has a dedicated site for her video drivers ([www.intellinuxgraphics.com)](www.intellinuxgraphics.com)) that gets updated very often and offers the latest drivers both stable and unstable available for download.(note:you have to compile them though).
All and all I think Intel is very serious about Linux and their products ideally suited for the OS especially when you consider that Linux does not impose so much load in the videocard GPU and other videocard solutions could be condsidered even an overkill for normal use.Also very good cost-effective line of products and you can find it everywhere in low- to middle-end machines.:guitar::popcorn:

---

### Post by mastablasta on 2010-10-20
goes for newer chipsets. they even come on computers with Ubuntu preinstalled.
 
Is Debian testing or current freeze version or still old kernel?
 
it is also true that they are good for so called "office" computers. their performce is still very poor compared to nVidia or AMD. BTW i have Intel(R) 82945G at work. office, emails, internet it's all fine. but when i try to add a relatively simple effect in inkscape the thing starts to have problems and slows down the whole thing substantially.
 
i think like ATI/AMD they didn't take linux seriously before. but maybe they do now.

---

### Post by klemes on 2010-10-21
Basically I don't disagree with you in anything just tried to offer my personal testimonial from my experience with these cards which has not been that bad after all.I don't either think that they are suited for video rendering or 3D gaming (although I haven't tried at all):-) but for watching clips in Youtube even in(1080p HDformat) and watching DVD's in vlc as well as normal 2D desktop usage they are more than adequate.It is not as if they can be compared to the latest NVIDIA or ATI cards but I reckon them to be good performers for my personal needs which are not that demanding after all.:popcorn:

---

