---
title: "A debate: Linux really about choice?"
date: 2006-04-28
forum: The Cafe
---

### Post by Donshyoku on 2006-04-28
I have always heard again and again that Linux is all about choice.  The choice to use your software how you wany, modify it if you want, leave it alone if you want.  I highly agree that this is true, but does the same thing stack for the hardware side?

I've been looking for TV tuners and everywhere I go, I am getting the idea that my choice is very limited.  I understand that hardware is a tough business especially without open standards or open source drivers.  I haven't been told once by a Windows user (please don't think me rude, this is only my experience) that I should use Windows for choice.  Yet, Linux users (and yes, I am generalizing) tote the banner of choice around.

So it comes down to a simple thing... Does choice apply to hardware?  Or am I stuck paying 2x or 3x as much for a tuner that will work in Linux?  Are companies that don't supply open source drivers or release a standards document for thier product excluded for choice?

Or am I just getting too far into my linguistics studies as an English major?

I figured it was worth a debate.  Every day on this forum, I see that people tell someone else to research before they buy.  Though this is not a bad thing at any rate, does it restrict choice?

If you've been restricted in your choice of hardware (tuners are espeically a problem right now), then perhaps you know how I feel...

---

### Post by juicybananahead on 2006-04-28
What can one say? Printers and wireless cards are other big problem areas... alas, there is little that can be done in the meantime except choose to help out with the efforts to reverse engineer such proprietary hardware. Don't be afraid to contribute to open-source.

Edit: As an English major your choices might be limited, but I believe that documentation projects are always screaming out for new people

---

### Post by helpme on 2006-04-28
1. Linux isn't about choice. In fact, it isn't about anything, or rather, it's about a lot of different things to a lot of different people.

2. It's pretty pointless to hold Linux responsible for something it has only a limited influence on, namely hardware support.

3. I don't really see your point.

---

### Post by Stormy Eyes on 2006-04-28
[QUOTE=Donshyoku]I have always heard again and again that Linux is all about choice.  The choice to use your software how you wany, modify it if you want, leave it alone if you want.  I highly agree that this is true, but does the same thing stack for the hardware side?[/QUOTE]

No, it doesn't. You've got choices in software. However, the Linux hackers or the FSF or Canonical have no control over the hardware manufacturers. They can't make them release the specs for their gear. The best they can do, if they can't persuade a manufacturer to release specs for a component, is reverse-engineer it in order to make their own drivers. Therefore, choice in software has nothing to do with choice in hardware.

---

### Post by mentallysilent on 2006-04-28
I completely agree with your point about the hardware aspect of things under linux. Your choice of hardware is indeed limited not because of how that particular electronic circuit is put together but because of driver issue. Hardware vendors, thanks to Microsoft's monopoly, don't bother releasing drivers for other operating systems especially the 'open source' ones. In the rare case that they do, the driver comes in binary form and is licensed proprietary. What is more, hardware vendors do not release their product specs. The courageous souls who venture upon developing linux drivers for these devices will largely reverse engineer/hack things together just to get the device to perform its "basic" task...forget the extra "features"...I for one have the BCM4306 wireless card on my laptop that does not have a linux driver so im left with using ndiswrapper and the windows driver. So I suppose the pain you feel is the price you pay for being "different" from the average windows user and I believe in the near future as the popularity of linux increases the problems on the hardware side will slowly be solved.

---

### Post by imagine on 2006-04-28
Free software is about free knowledge, free information, free ideas. Free means here that everybody has access to them, can use them and that they aren't "owned" or controlled by anybody. This again is essential to have *any* choice, especially in a long-term view.
The reason why you're choice on tv tuners or printers is limited is because they don't have an open interface, firmware, etc, which makes you dependent on the manufacturers (ie non-free).

---

### Post by aysiu on 2006-04-28
Who cares if you can buy whatever hardware you want if you can't control your software?

I would much rather buy hardware for Linux and be able to install an OS without activating it, and customize my desktop easily without Windowblinds or some other pay-for/nagware application... than be able to buy whatever hardware I want and then be locked into Microsoft's way of doing things for everyday computing.

I don't *buy* computers (or computer parts) every day, but I do *use* a computer every day.

---

### Post by Ensnared on 2006-04-28
Traditionally, Linux have always had very good support for old hardware, and lately (well, "lately" - maybe the last 6-7 years or so) it's also gotten support for popular new hardware fairly quick. This doesn't seem to be quite the case anymore though, especially where wireless adapters are concerned. Wireless in Linux is a hassle, and that's a pretty big deal since wireless networks seem to have exploded in popularity just the last couple of years. Personally I find it strange that this is the case, as Linux is an OS so heavily geared towards networking.

So you do have a point. Basically, if you want the newest and most powerfull hardware - atleast for a desktop but probably other systems as well - Linux is probably not the right choice. You'll likely have tons of problems getting it to work - if you're very unlucky the installer won't even run because the kernel doesn't work with your hardware - and in many cases you wont' be able to make it work until someone writes a driver for it, which could be in two days, or in two years.
There are often workarounds though - an example from personal experience: when the ATI Rage128 cards came on the market (ATI Rage Fury), there were no drivers for it at all in Linux, and ATI naturally didn't provide anything like that. But one could get X working using the frame buffer device as the graphics adapter. It required compiling the kernel (which I suspect most Linux-users were fairly familiar with at the time), and it wasn't fast, but it was better than nothing (yes, I count 640x480 resolution with the basic VGA driver on a 17" monitor as "nothing" ;)). Luckily, SuSE eventually developed a driver for it for XFree86.
However, the fact remains - for some hardware issues, there are no workarounds, and in such cases involving mainboard devices and chipsets, that often means Linux will not work at all.

You do have hardware compatibility lists that can be consulted, just like for Windows, but the difference is the hardware manufacturers provide Windows drivers, so even if it's not on the Windows HCL, chances are it will work. With Linux, it's the other way around more often than not - and even something that is supposed to be compatible doesn't always work. I find the HCL's for the various Linux distros to be fairly conservative though, so if it's actually listed on that, chances are it will work. But with all Linux distros, the kernel is pretty much the same, so a hardware device working on one distro is possible to get working on any distro, but the level of manual interaction one has to perform in order to make it work will of course differ.

I wouldn't go as far as to say this invalidates the "Linux is about choice" statement though. The incredibly wide range of options in software - even high quality software - far outweigh the few hardware issues that exist as far as I'm concerned.
The whole idea of switching to Linux is also about choice - most people never choose Windows; they don't choose at all. They buy the computer and use what's on it, and that is usually Windows. There are very few Linux PC's one can buy in this way, and usually, buying such a computer is also a result of choosing to use Linux - or choosing something other than Windows, but one could just as easily go for Mac in that case.

So there are several ways to look at the statement. OS-wise I'd say Linux can be about choice. The same goes for software. Hardware-wise, one can't say you're exactly _limited_ in your choice of hardware, but certain hardware might prove troublesome.

---

### Post by Kvark on 2006-04-28
You are asking the question the wrong way around. It is not Linux developers that need to release PC drivers. It is PC manufacturers that need to release Linux drivers. So the real question is...

There are countless PC components to choose from. But is PC really about choice? Does choice apply to software too or only to hardware? Can you choose which OS to use with the many different PC hardware parts available?

Which OS comes preinstalled on almost all desktop PCs? Which OS are the "PC" versions of games made for? Which OS do they help you with when you call support? Which OS does everyone assume that you run on your desktop PC? That's right, as far as hardware manufacturers and almost everyone else are concerned "desktop PC = Windows computer". If you want to use another OS instead of Windows on the desktop, they expect you to go buy a mac with OSX.

---

### Post by prizrak on 2006-04-28
Well actually Linux is about choice in hardware as well. Even Ubuntu runs on both PPC and x86 machines. There are other Linux distros that can run on SPARC, VMS, even XBOX :) The constraint is only in the hardware choice for x86 PC's for the most part. Also Linux hardware compatibility is a bit of a tricky beast because there are actually very few companies that make unique hardware. Most hardware is based around a reference board or a main chip that a company that specializes in that particular area provides. Many times the device itself will not be listed as supported but it will still work with Linux because it uses the same reference board as a supported devices. A good example would be Atheros based wi-fi cards. Atheros is completely supported by Ubuntu (and Linux in general) so you can more or less bet that anything based on it will work with Linux with no pain (as it did for me).

---

### Post by Christmas on 2006-04-28
> I've been looking for TV tuners and everywhere I go, I am getting the idea that my choice is very limited.
I use Leadtek TV2000 XP and it's a very good TV-Tunner, Debian and Ubuntu detected it, I recommend this.

On-topic: Speaking of software, it is the user's choice, he's free to do anything with its programs and OS but the hardware is indeed a problem. I have a friend who aquired an external soundcard and couldn't find any drivers for it. He used Knoppix and he couldn't make it work. However Ubuntu detected it. Seems like if the developers know what they are doing and try to cover as much hardware as they can, there is no need for official drivers but (there is always a but) these drivers are not fully compatible or don't take the full advantage from the hardware. For example, the ALSA driver works for me but the quality is weak when the volume is high. My motherboards manufacturer (ASUS) released a driver for Linux, ALSA 0.9.6, which I couldn't install as I'm still a newbie and my Kernel configuration and compilation failed :(. 
BTW does anybody know if my ALSA driver released by ASUS are the same with the driver included in Ubuntu?

---

### Post by jpkotta on 2006-04-28
There is less hardware choice in Linux.  Period.  Whatever the reasons, that's the way it is.  There are also many pieces of software that we can't use either, so one could argue that there is less choice in software as well, but I don't think that really holds up.

imagine said something about the long term view.  I think the open source model is unbeatable in the long term.  Linux (across all distributions) is getting incrementally better all the time.  We're still gaining market share,quickly.  Eventually, I think there's going to be a tipping point and hardware manufacturers will no longer ignore us.  The trouble is, it might be many years away, and Microsoft will try to sabotage it.

---

### Post by Donshyoku on 2006-04-29
I certainly believe that hardware makers are to blame.  I commend the programmers that are making proprietary hardware (funny to see the MCE TV tuners working in Linux, hehe) work in Linux.

It is just that Linux can end up being more expensive.  I have bought two TV tuners both around $30, and can't get them working in much of a fashion.  Yes, the manufacturers are to blame.  But it just seems so much easier for me to spend half the price and use it in Windows.

I've been playing with Linux for a few years and I have seen dramatic improvements.  I guess my arguement is very simple, and a little cliche for this forum it seems!  :p 

I am hoping that LSB will be adopted to good effect and really improve the support for software.  If software becomes fairly uniform, I predict (especially with a lot more awareness of Linux these days) that hardware manufacturers will build in a fashion that can at least be compatible.

---

### Post by jobezone on 2006-04-29
> I have always heard again and again that Linux is all about choice.
Linux, or GNU/Linux is about whatever you want. For me, it's about freedom in computing.

---

### Post by egon spengler on 2006-05-01
[QUOTE=Donshyoku]I have always heard again and again that Linux is all about choice.  The choice to use your software how you wany, modify it if you want, leave it alone if you want.  I highly agree that this is true, but does the same thing stack for the hardware side?[/QUOTE]

This is severly flawed logic, a Linux distro provides you with software and (as you agree yourself) plenty of choice regarding that software. What a Linux distro does NOT do is provide you with hardware, so how do you make the leap that Linux is failing in it's duty to provide choice of hardware? It is the manufacturers who only support one OS that are failing to provide choice.

---

### Post by htinn on 2006-05-01
Dear OP:

Linux is software. Hardware is hardware. I assume you are aware of the difference.

---

### Post by prizrak on 2006-05-01
[QUOTE=jpkotta]There is less hardware choice in Linux.  Period.  Whatever the reasons, that's the way it is.  There are also many pieces of software that we can't use either, so one could argue that there is less choice in software as well, but I don't think that really holds up.

imagine said something about the long term view.  I think the open source model is unbeatable in the long term.  Linux (across all distributions) is getting incrementally better all the time.  We're still gaining market share,quickly.  Eventually, I think there's going to be a tipping point and hardware manufacturers will no longer ignore us.  The trouble is, it might be many years away, and Microsoft will try to sabotage it.[/QUOTE]
You are wrong there isn't less hardware choice in Linux. Linux has been ported to just about any architecture you can think of. Including cell phones and routers, now in the x86 world Linux has less hardware choices but not overall.

---

