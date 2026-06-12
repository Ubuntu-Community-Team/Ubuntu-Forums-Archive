---
title: "Going back to BSD ASAP"
date: 2009-09-11
forum: Testimonials &amp; Experiences
---

### Post by Zhwazi on 2009-09-11
It tends to confuse my friends when I complain about Linux because I'm not new to it. I started using Ubuntu at 5.10 and gradually got deeper into Linux, running Gentoo for almost a year. For the past year and a half, however, I've been using primarily Opensolaris and FreeBSD, with occasional OpenBSD and Windows 7, and I have a Mac I've been very happy with. I bought a laptop (Dell E6400) knowing full well what should and should not work in Linux and free Unices. I say should, although at the time I felt this hardware would work.

Because I hate GNOME for esthetic reasons (it's not terrible but not great. It's worth tolerating to run Opensolaris as I await fully-functional KDE4 for it), and because Opensolaris doesn't appear to have any PTP support for my camera, nor support for a Wacom tablet I have, and because I'd tried to get them working in FreeBSD without much luck, I installed Kubuntu 9.04 amd64, having heard great things about it from my friends who do use Linux.

I was horribly disappointed, and continue to be. Half the time when I boot, the sound doesn't work. But only half the time. My Intel 5300AGN wifi chip "works", but frequently ceases all function and can't be brought back without unloading and reloading the kernel module controlling it. It's not a hardware problem, Opensolaris and W7 have no problems like that. My trackpad also frequently stops working at a fully-functional level and drops to a basic PS/2 mode with no sensitivity, speed control, or edge-scrolling capability. The PTP support which I left BSD in favor of is little better, as once the camera has been disconnected, it cannot be reconnected to without rebooting the computer. (I thought it was the camera at first, but only rebooting the computer ever fixes it.) I thought I was going to enjoy having natively running Skype, Wacom drivers, and PTP support, but I'd rather have a stable system that does what I expect. Not having a driver is one thing, having a mouse that unexpectedly changes its behavior radically is different.

All I'm waiting for now is the amd64 nVidia blob driver that appears to be coming quite soon to FreeBSD. Linux is so bad I'd rather grit my teeth and put up with GNASH than deal with Linux's flakiness. I used to think BSD people that said Linux was unstable and crashy were just being cocky. The same goes for the base system v. kernel + utilities thing. But from a user's perspective, using BSD actually feels like that. Apps that were written with FreeBSD as an afterthought feel to a FreeBSD user as if they were written with FreeBSD in mind, whereas apps written explicitly for Linux feel to me when using Linux like they were written for a totally different platform and then ported over.

I had to reboot W7 far less frequently than I've had to reboot Kubuntu to fix various issues, many of which still are not fixed, and I ran W7 on this laptop far longer than I have run Linux. Windows had it's own problems, but farther and fewer than Linux's. I don't like Windows, I spend every working day fixing things that any vaguely unish OS would have no trouble with, and I have to say it works better than Linux.

I'm not going to contribute code, because I see other operating systems, free ones, that aren't broken. Why fix what's broken when something else already works? They have less features (i.e. sophisticated drivers for less-than-ubiquitous hardware, things like ZFS are great features though), but I'm someone that will take fewer features over broken features any day. I don't get to use them either way, I might as well get what I'm expecting. With Kubuntu, I was expecting a Linux much improved over what I'd used 3 years ago. It's worse now.

I'm also frustrated by things like the incredibly sparse xorg.conf that comes with Kubuntu. It's a stub! Part of what makes Unix-type OSes worth using is that you get control rather than turning it over to obscure unseen forces within the operating system or application. If you have the facilities to automatically detect the settings for X, it would be better put into generating sane defaults for a xorg.conf than invisibly using the default settings. nvidia-xconfig gave me a much more usable xorg.conf that actually did what I wanted. I also have to wonder why ctrl+atl+backspace was disabled by default. I haven't had to use it in FreeBSD but it works by default there should I need it. It's frustrating to do what I've been doing on Linux and Unix for years and realize I have to switch to a tty and sudo killall Xorg when X becomes slow, kludgy, and unresponsive to anything but mouse movement (yet another issue I've yet to have on BSD or Opensolaris).

I actually have more complaints than just these, these are just the ones that pop into my head while I'm away from that laptop. I've had so many small problems trying to use Kubuntu that I won't even remember all of them until the next time it happens to me. Overall I'm incredibly disappointed. The more I look back at the Linux world the more I remember why I consider it behind me.

Going back to FreeBSD ASAP. 8.0-BETAs are available and it's worth buying a supported wireless card to be able to get away from Linux without having to resort to Windows. One day I would've done this to get away from Windows.

---

### Post by Martje_001 on 2009-09-11
> **Zhwazi said:**
> Half the time when I boot, the sound doesn't work. But only half the time.Have you filled in a bug report?

> **Zhwazi said:**
> My Intel 5300AGN wifi chip "works", but frequently ceases all function and can't be brought back without unloading and reloading the kernel module controlling it.Have you filled in a bug report?

> **Zhwazi said:**
> I'm also frustrated by things like the incredibly sparse xorg.conf that comes with Kubuntu. It's a stub! Part of what makes Unix-type OSes worth using is that you get control rather than turning it over to obscure unseen forces within the operating system or application. If you have the facilities to automatically detect the settings for X, it would be better put into generating sane defaults for a xorg.conf than invisibly using the default settings. 
You can set any option you want.. If you're using radeon (the driver, check /var/log/Xorg.0.log to find out which driver you're using), type:
```
man radeon
```And there they are! All options you can set, including default ones.

Really, I like it the way it is now. I can just pull out an ATi card en put my Nvidia card in and Xorg automatically switches to nv.

---

### Post by Martje_001 on 2009-09-11
Btw: Next time you buy a pc, buy a Linux-certified one.

---

### Post by 3rdalbum on 2009-09-11
I respect your decision to stick with an open-source operating system over our free-and-open-source operating system.

Not everybody has the same experience that you have had with Kubuntu. In fact, very few do; that's why Ubuntu and Kubuntu are so tremendously popular.

If you use any distribution with Pulseaudio, you need the padevchooser program, as without it there's no easy way to configure your sound. Ubuntu does not ship with this program, or any replacement, although it's available in the repositories.

Control-Alt-Backspace is disabled by default in the recent Xorg versions (replaced with Alt-SysRq-K), and they do most of their configuration on-the-fly, hence the tiny xorg.conf.  The Linux HAL system provides Xorg with the information it needs for this automagic configuration, which may explain why your FreeBSD system still requires a full Xorg.conf file. This is not an Ubuntu change, this is an upstream change, and I believe this will be happening with FreeBSD soon as well.

Also, with respect, Ubuntu's intended audience is not really the people who like to modify their xorg.conf and not relinquish any control to their operating system. Ubuntu's intended audience ranges from newbies, to power-users/experts who want the system to behave in a sane way as much as possible and use that as the basis for tinkering or building other things. You don't sound like you fit that mould.

I can fiddle around with my system if I want to, but currently I don't. Until I feel the need to tinker, I know that Ubuntu will work the right way every time. And I value the ability to bring up an Ubuntu system from scratch in no time at all - it helped recently after a tinkering session went horribly wrong and there was no way to avoid a reinstall.

Obviously, I don't have any stability problems with Ubuntu; everything is very glitch-free for me now that I removed those bad RAM sticks. Your milage may vary. It happens, and at least you gave it a shot.

Keep a partition (or a slice) available for Ubuntu 9.10 when it comes out; this time try Gnome :-)

---

### Post by Simian Man on 2009-09-11
> **3rdalbum said:**
> I respect your decision to stick with an open-source operating system over our free-and-open-source operating system.

What on earth are you talking about?  BSD is freer than Linux is.

Also, Ubuntu does not sound like a good distro for you for a few reasons.  First of all you use KDE which is very much not the focus of Ubuntu.  Secondly you like to tweak your system at a fine grained level.  Ubuntu is not really set up for this and I have seen it break when things like that are attempted.  You should try a distribution like Arch or Slackware which are much more similar to BSD than they are to Ubuntu.

Also, in my experience Fedora is the best when it comes to hardware support, so you can see if your machine likes that any better.

Sorry your Linux experience left so much to be desired :(.

---

### Post by tubasoldier on 2009-09-11
> **Martje_001 said:**
> You can set any option you want.. If you're using radeon (the driver, check /var/log/Xorg.0.log to find out which driver you're using), type:
```
man radeon
```And there they are! All options you can set, including default ones.
Did you read what he wrote? He is obviously using an nvidia card, not an ati. 


> **Martje_001 said:**
> Btw: Next time you buy a pc, buy a Linux-certified one.
because that will fix all the bugs in Ubuntu?


> **3rdalbum said:**
> I respect your decision to stick with an open-source operating system over our free-and-open-source operating system.

Keep a partition (or a slice) available for Ubuntu 9.10 when it comes out; this time try Gnome :-)

I too respect his decision to stick with OpenSolaris. Its a fine OS and is extremely stable. The stability is even noticeable on the live CD. I've just never had the time to install it myself, as it needs to reformat the entire hard drive. Also after reading what he says about Gnome I would think suggesting Gnome is not going to help much either. The consumer prefers KDE so you suggest Gnome? Awesome. Similar experiences are why I no longer shop at Best Buy. When I want what I came in to buy and you try to sell me something else then I'm not too happy about it.

the CTL-ALT-Backspace thing bugs me too. Quite a bit.

IMO its unfortunate that you tried Kubuntu as the Linux to come back to. I've lost confidence in the Kubuntu team's ability to put together a system with the least amount of bugs. Kubuntu has never really been great but it has gotten terrible over the last few releases.

Zhwazi obviously has experience running Linux having run Gentoo for a year. I think the complete issue here is that he has found Ubuntu to be full of crazy bugs. Take a gander at Launchpad and its easy to see that bug reports are obviously not taken into consideration much. If they were then the bug reports would be taken care of in a more efficient manner.

---

### Post by Zhwazi on 2009-09-11
> **Martje_001 said:**
> Have you filled in a bug report?
No, nor have I looked.

> Have you filled in a bug report?
There already is one.

> You can set any option you want.. If you're using radeon (the driver, check /var/log/Xorg.0.log to find out which driver you're using), type:
```
man radeon
```And there they are! All options you can set, including default ones.

Really, I like it the way it is now. I can just pull out an ATi card en put my Nvidia card in and Xorg automatically switches to nv.
...how often do you switch cards exactly?

> Btw: Next time you buy a pc, buy a Linux-certified one.
This sounds incredibly demeaning from where I'm standing. I'm going to buy a computer on it's technical merits. I bought this one for it's servicability, that it has the specs that I want, has no crummy failure-prone gimmicky parts on it, because I could get it without Windows (it came with FreeDOS), and because I have access to all the documentation for it. I checked that the parts I planned to use were compatible with other operating systems than Windows. Not Linux specifically, but I'm not having any hardware compatibility issues that could be expected. The Intel Wifilink 5300AGN is claimed to work in Linux. It's claimed to work in OpenBSD and Opensolaris. It works great in Opensolaris, never drops connection or stops working. That's the only hardware compatibility problem I'm having, and other OSes with inferior hardware support are doing better than Linux on it. Don't even insinuate or imply that it's my fault or the manufacturer's fault for not doing the research or not caring. And while I couldn't expect you to have known this in advance, it's very frustrating to be told to trust somebody else's word that it works when I did the research myself.

Just so that you know, my other other laptop is a Mini 9 that came with Ubuntu. I can't say it's given me any problems, however I did install OpenBSD on it first thing after getting it (I was planning on that when I originally bought it), so Linux didn't get much of a chance. Love OpenBSD though.

---

### Post by SunnyRabbiera on 2009-09-11
Kubuntu has always been flaky, thats why I typically dont use it.
If I want KDE I just settle for gnome in Ubuntu and work my way up to KDE using the repos.
Its easy enough to do.

---

### Post by Zhwazi on 2009-09-11
> **3rdalbum said:**
> I respect your decision to stick with an open-source operating system over our free-and-open-source operating system.
In before BSD v GPL holy war. See what Simian Man wrote.

> Not everybody has the same experience that you have had with Kubuntu. In fact, very few do; that's why Ubuntu and Kubuntu are so tremendously popular.
I'm aware, which is probably why the disappointment is so great, I had high expectations.

> If you use any distribution with Pulseaudio, you need the padevchooser program, as without it there's no easy way to configure your sound. Ubuntu does not ship with this program, or any replacement, although it's available in the repositories.
If you need it then why isn't it included?

> Control-Alt-Backspace is disabled by default in the recent Xorg versions (replaced with Alt-SysRq-K), and they do most of their configuration on-the-fly, hence the tiny xorg.conf.  The Linux HAL system provides Xorg with the information it needs for this automagic configuration, which may explain why your FreeBSD system still requires a full Xorg.conf file. This is not an Ubuntu change, this is an upstream change, and I believe this will be happening with FreeBSD soon as well.
I haven't heard anything of that, I'll be sure to keep a copy of my xorg.conf handy.

> Also, with respect, Ubuntu's intended audience is not really the people who like to modify their xorg.conf and not relinquish any control to their operating system. Ubuntu's intended audience ranges from newbies, to power-users/experts who want the system to behave in a sane way as much as possible and use that as the basis for tinkering or building other things. You don't sound like you fit that mould.
I wanted something that worked out of the box. I haven't done any major tweaking to the OS. My default shell is zsh and I changed my KDE theme using the stuff in KDE for changing themes. That's about it. I haven't asked it to be mine yet, I've only asked it to work, I haven't gotten past that stage yet :(

> Keep a partition (or a slice) available for Ubuntu 9.10 when it comes out; this time try Gnome :-)
Blaaah, I don't like GNOME :(

---

### Post by Zhwazi on 2009-09-11
> IMO its unfortunate that you tried Kubuntu as the Linux to come back to. I've lost confidence in the Kubuntu team's ability to put together a system with the least amount of bugs. Kubuntu has never really been great but it has gotten terrible over the last few releases.
Ah, wish I'd known that before, I always saw *buntu as the easy Linux that just works, so Kubuntu seemed like the obvious choice for a laptop OS to not have to tinker with. May need to try something else then.

---

### Post by Martje_001 on 2009-09-11
> **tubasoldier said:**
> Did you read what he wrote? He is obviously using an nvidia card, not an ati. 
Did *you* read what *I* wrote? I only gave an example. He should do
```
man nv
```

> ...how often do you switch cards exactly?
Much more often than I want to go into the terminal and fix my xorg.conf.

Really, you can set whatever you want in xorg.conf. I don't get your point.

---

### Post by tubasoldier on 2009-09-11
> **Zhwazi said:**
> Ah, wish I'd known that before, I always saw *buntu as the easy Linux that just works, so Kubuntu seemed like the obvious choice for a laptop OS to not have to tinker with. May need to try something else then.

Like I said earlier we could go on suggesting all sorts of other distributions for you. You come across as an experienced user who could figure that out for yourself. Distrowatch is by far the best place to start.

---

### Post by Zhwazi on 2009-09-11
> **tubasoldier said:**
> Like I said earlier we could go on suggesting all sorts of other distributions for you. You come across as an experienced user who could figure that out for yourself. Distrowatch is by far the best place to start.

I've been away from the Linux scene for over a year, and away from the Ubuntu scene for two, and last I recalled Ubuntu was among the best. Ubuntu's always been the "You don't need to give it much thought" distro to me, which is what I wanted this time around. So honestly, I didn't give it much thought. Though I will say the last time I tried to install Fedora SELinux prevented me from partitioning.

I'll probably give Slack a shot at it. I already have a partition set aside for a secondary OS, wasn't sure what to put there though.

---

### Post by Zhwazi on 2009-09-11
> **Martje_001 said:**
> Did *you* read what *I* wrote? I only gave an example. He should do
```
man nv
```


Much more often than I want to go into the terminal and fix my xorg.conf.

Really, you can set whatever you want in xorg.conf. I don't get your point.

My point is "I want a full xorg.conf" not "I don't know what to do now that xorg.conf is a placeholder". I want to know what it thinks my mouse devices are and what resolutions it thinks its allowed to run at. I have special configuration for different mice that I use on those systems I choose to tweak, and it'd be nice to know things like that before I try to tweak anything.

If I switched cards that often I'd keep an xorg.conf.nv and a xorg.conf.ati and make a script to automatically symlink appropriately on startup, but that's just me and my silly little hacks with reliable and easily-understood no-black-box elements of my system.

It would have been more helpful if you had said "run nvidia-xconfig" instead of "man radeon", because that would have given me a reasonable xorg.conf and been directly relevant. I had already figured that out in the process of getting the blob to work, but it would've been more appreciated :/

---

### Post by Chronon on 2009-09-11
> **tubasoldier said:**
> Take a gander at Launchpad and its easy to see that bug reports are obviously not taken into consideration much. If they were then the bug reports would be taken care of in a more efficient manner.

Non sequitur.

---

### Post by HappyFeet on 2009-09-11
It's funny how people say that their hardware is not at fault when they have problems, yet, when I build my own pc's, I make sure they are linux compatible, and guess what? Not one single problem, ever. Please, don't tell me about problems, as I fix windows machines for a living. Oh, and btw, if linux is so bad, how come all 15 of my customers that now use ubuntu, have not had 1 problem? (yes, I do periodic check backs) Please don't insult the linux community with such drivel. I have no doubt you may have problems, but 40+ successful installs tell me that maybe the user should look in the mirror for the source of his problems.

I am all for you using whatever OS makes you happy, but I am just tired of people complaining. Maybe I should go to the windows message boards and complain over there about my displeasure with windows lately. We'll see how far that gets me, and what it accomplishes.

If you are not willing to help make it better, then why complain? Have a nice day.

---

### Post by Zhwazi on 2009-09-11
> **HappyFeet said:**
> It's funny how people say that their hardware is not at fault when they have problems, yet, when I build my own pc's, I make sure they are linux compatible, and guess what? Not one single problem, ever. Please, don't tell me about problems, as I fix windows machines for a living. Oh, and btw, if linux is so bad, how come all 15 of my customers that now use ubuntu, have not had 1 problem? (yes, I do periodic check backs) Please don't insult the linux community with such drivel. I have no doubt you may have problems, but 40+ successful installs tell me that maybe the user should look in the mirror for the source of his problems.
Fine, you're a technician that fixes Windows machines for a living *just like I do*. So you know how this works.

-It's not the hardware, because other operating systems run fine on it.
-It's not hardware compatibility, because my hardware *is* compatible. I bought a wifi card separately from the computer because I wanted a high-quality and compatible wifi card. And I got that.
-It shouldn't be the software itself, because Ubuntu is a good distro.
-It's not the interaction between the software and user incompetence because I know how these things work and have done nothing to break them.
-It's not the interaction between the software and user expertise because I haven't made any drastic modifications to the system.
-It's not the user himself because I'm certainly not new to this.

You can suspect the user and the operating system. Given that the same issues don't happen with the same user and a different operating system, suspecting the user should be deffered in favor of suspecting the operating system.

Have I made any ill steps in what I've decided here?

> I am all for you using whatever OS makes you happy, but I am just tired of people complaining.
Well then fix it :/

> Maybe I should go to the windows message boards and complain over there about my displeasure with windows lately. We'll see how far that gets me, and what it accomplishes.
Windows users aren't the ones that boast how their open and free system can be modified and fixed by anyone that wants to do it, so it shouldn't be expected that it would be morally compelling even in the unlikely chance you ran across a Microsoft programmer there.

> If you are not willing to help make it better, then why complain? Have a nice day.
Because it is through complaint that people generally get an idea of what is creating problems that dissatisfy people and drive them away from the operating system they are working on and trying to spread. Bug reports are too narrow in scope as a way to explain my dissatisfaction at what appears to be systematic problem, not a mere product of numerous unrelated bugs.


Your condescending tone goes unappreciated.

---

### Post by HappyFeet on 2009-09-11
> **Zhwazi said:**
> 
Your condescending tone goes unappreciated.
Ask me if I care.

You said it yourself that it can not be the hardware if other OS's run fine on it. But if linux does not run good on it, **then it is not linux compatible**. If it was, then it would run good. Use some common sense, for the love of god. I'm done here, goodbye and good luck.

---

### Post by Tamlynmac on 2009-09-11
> HappyFeet

You said it yourself that it can not be the hardware if other OS's run fine on it. But if linux does not run good on it, **then it is not linux compatible**.

With over thirty Ubuntu installs, I must agree with your statements. All installs that gave me problems were hardware related. Generally, video, network or audio. Once the offending hardware was replaced with Linux compatible hardware, the install went without issue.

I've heard many a claim that it worked in Windows, so it must a problem with Ubuntu/Linux. Few realize that the mfg drivers are essential in determining which OS the hardware will perform on. The concept that all hardware will work with every OS is extremely naive.

When considering either a new system or replacement parts (assuming one is considering using a Linux distro) I always recommend purchase of compatible hardware only. This fundamentally eliminates any issues with installation or functionality.

Just makes sense. Use hardware that's compatible with your OS of choice or risk functionality problems. :-k

---

### Post by Sef on 2009-09-11
__Zhwazi can use whatever operating system that works best for them with whatever desktop manager that they like.  That is what open source is about whether it is under the GPL, LGPL, or another open source license.

This thread needs to coll off; therefore, I am locking it.

---

