---
title: "Everything's rubbish"
date: 2010-07-21
forum: Testimonials &amp; Experiences
---

### Post by BioBiro on 2010-07-21
Hello all,

I just want to rant about my bad luck with operating systems at this moment in time.

You may (or may not) have noticed my support thread on the forum the other day. Basically, it stated that I couldn't get my Firewire soundcard to work on Ubuntu. No sound whatsoever. Which is unacceptable.

I have a soft spot for everything-BSD, so I tried PC-BSD 8 shortly after. After the (rather long) installation, all the video drivers failed except for the default VESA one. Which means that I can't change resolution, and there's no hardware acceleration, so dragging a window around causes it to redraw dozens of tedious times. Totally unusable.

Now I have Windows7 back on it. Everything is working well (and feeling familiar), when only an hour ago I had a BSOD. Something about a driver conflict. I should point out that I get a BSOD whenever my computer wakes up from going to sleep - the solution being to disable the sleep feature. I tried Ubuntu in the first place because I had installed a Win32 assembler which shortly after had caused Windows to go nuts and mangle the display whenever it felt like it.

How come nothing works properly these days?

---

### Post by earthpigg on 2010-07-21
i hate to break it to you, but it sounds like the only thing all three operating system installs had in common is the hardware.

could be something as cheap as a faulty stick of ram, or maybe your optical drive copying bad data over. who knows.

suggestion: grab an ubuntu LiveUSB (not CD, to rule out optical drive issues), run the memory test and then boot into gnome and see what the ubuntu hard disk monitor thing has to say.

---

### Post by loell on 2010-07-21
didn't you noticed the common denominator there? ;)

---

### Post by linux18 on 2010-07-21
> **BioBiro said:**
> Hello all,

I just want to rant about my bad luck with operating systems at this moment in time.

You may (or may not) have noticed my support thread on the forum the other day. Basically, it stated that I couldn't get my Firewire soundcard to work on Ubuntu. No sound whatsoever. Which is unacceptable.

I have a soft spot for everything-BSD, so I tried PC-BSD 8 shortly after. After the (rather long) installation, all the video drivers failed except for the default VESA one. Which means that I can't change resolution, and there's no hardware acceleration, so dragging a window around causes it to redraw dozens of tedious times. Totally unusable.

Now I have Windows7 back on it. Everything is working well (and feeling familiar), when only an hour ago I had a BSOD. Something about a driver conflict. I should point out that I get a BSOD whenever my computer wakes up from going to sleep - the solution being to disable the sleep feature. I tried Ubuntu in the first place because I had installed a Win32 assembler which shortly after had caused Windows to go nuts and mangle the display whenever it felt like it.

How come nothing works properly these days?
everything works fine for me, I've never BSOD'd, or had linux driver errors. The point is: everyone's experience is different and no one OS has everything you want. If you want to solve those troubles, choose an OS stick with it, and when you encounter a problem try to fix it. Eventually everything will work if you try hard enough. Sorry for the sobering news but isues like this will happen to somebody, and they just seem to be happening to you. ( BTW that's was taken from the weak anthropic principle, jfgi ) But I would like to know what hardware your on, because thats just a lot of **** thats spewing out of it . (no offense )

---

### Post by ubunterooster on 2010-07-21
> **loell said:**
> didn't you noticed the common denominator there? ;)
True, some of us just seem cursed

---

### Post by BioBiro on 2010-07-21
> **linux18 said:**
> everything works fine for me, I've never BSOD'd, or had linux driver errors. The point is: everyone's experience is different and no one OS has everything you want. If you want to solve those troubles, choose an OS stick with it, and when you encounter a problem try to fix it. Eventually everything will work if you try hard enough. Sorry for the sobering news but isues like this will happen to somebody, and they just seem to be happening to you. ( BTW that's was taken from the weak anthropic principle, jfgi ) But I would like to know what hardware your on, because thats just a lot of **** thats spewing out of it . (no offense )

Thanks, heh. To be honest, i've been with Windows since version 3, so i'm fine working with/around it, and will solve this driver conflict BSOD if it repeats. Just installed Cygwin tonight so i'm having fun learning some commands.

My computer is a hand-build purchased a couple of months ago. Specs are:
Gigabyte GA-X58A-UD3R
Intel Core i7 920 @ 2.66GHz
Patriot Viper 6GB (3x2GB) DDR3 12800C8 (1600MHz)
Asus ATI Radeon HD 5850 DirectCU 1024MB GDDR5
A pair of Samsung SpinPoint F3 1TB hard drives.

---

### Post by CharlesA on 2010-07-21
My bet is hardware releated. If it happened no matter the OS, then it's having a problem with the hardware.

How are the temps and have you ran a memtest?

I've ran problems before with running RAM at a certain speed would cause the machine to crash, I ended up replacing the memory with some rated at a lower speed and that fixed the problem.

If you've got DDR3 1600, try running it at a lower speed and see what happens.

---

### Post by BioBiro on 2010-07-21
> **CharlesA said:**
> My bet is hardware releated. If it happened no matter the OS, then it's having a problem with the hardware.

How are the temps and have you ran a memtest?

I've ran problems before with running RAM at a certain speed would cause the machine to crash, I ended up replacing the memory with some rated at a lower speed and that fixed the problem.

If you've got DDR3 1600, try running it at a lower speed and see what happens.

If what happened in every OS? There doesn't seem to be a recurring problem in each of the 3 OS's I have tried recently - Ubuntu didn't support my soundcard, PC-BSD's video drivers failed, and Windows 7 gave me a BSOD because of an apparent driver conflict. I apologise if i've got the wrong end of the stick...

My temps are fine (CPU cores fluctuate around 30c-50c, Northbridge a little higher, and my GPU between 40c-60c depending on load). I will try the MemTest on Ubuntu tommorow - pretty nifty having it built into the bootable media :).

---

### Post by earthpigg on 2010-07-21
> **BioBiro said:**
> My computer is a hand-build purchased a couple of months ago. Specs are:
Gigabyte GA-X58A-UD3R
Intel Core i7 920 @ 2.66GHz
Patriot Viper 6GB (3x2GB) DDR3 12800C8 (1600MHz)
Asus ATI Radeon HD 5850 DirectCU 1024MB GDDR5
A pair of Samsung SpinPoint F3 1TB hard drives.

could be motherboard burn in failure. the problems didn't have much in common.

still have warranty paperwork on the mobo?

where you wearing a wrist strap thing? if not, where you conscious of static electricity while assembling? 

lots of people say that they've built and worked on computers for years without ever giving thought to ESD and never had a problem, but it's possible that all of those people naturally/accidentally do things that coincidentally protect the parts.

I zapped a computer about 10 years ago, so yeah... I'm not one of those people and, thus, must be aware :P

---

### Post by earthpigg on 2010-07-21
> 1 - Ubuntu didn't support my soundcard
2 - PC-BSD's video drivers failed
3- Windows 7 gave me a BSOD because of an apparent driver conflict

What if, in all three cases, the Operating System is being fed incorrect information about the hardware? That would implicate the motherboard.

May be getting a bit ahead of ourselves. Let's see what memtest and *System* -> *Administration* -> *Disk Utility* have to say.

then rule out the possibility of bad video card. 2 and 3 could be explained by video card, so we rule that out by putting the video card to the test in ubuntu (where it appeared to work): install ubuntu, and do some cube spinning and [shoot some people]("http://www.urbanterror.info/news/home/"), see if it performs as well as it should. Both compiz' benchmark plugin and urban terror's frame rate counter should be reporting well over 90fps with everything maxed out on that hardware.

if it's not the ram, hard drive, or video card... i think that just about narrows it down to the motherboard.

before ripping it out and making a warranty claim, however, unplug everything and plug it back in. seriously. even if it looks plugged in and you can feel that it is indeed firmly plugged in, unplug it and plug it back in. that's made a difference for me in the past.

---

### Post by RJARRRPCGP on 2010-07-21
> **BioBiro said:**
>  caused Windows to go nuts and mangle the display whenever it felt like it.


Sounds like a graphics hardware issue. Sorry. :(

TBH, sounds like a bad video card. :(

---

### Post by BioBiro on 2010-07-21
> **earthpigg said:**
> What if, in all three cases, the Operating System is being fed incorrect information about the hardware? That would implicate the motherboard.

May be getting a bit ahead of ourselves. Let's see what memtest and *System* -> *Administration* -> *Disk Utility* have to say.

Good advice, but yeah, a geezer warned of the dangers of static  electricity. I rub my hands on some grounded metal before touching any  internals.

I will do the above tommorow and report back.

While I appreciate this generous advice, I kind of expected this thread to be more like an episode of 'Cheers' where everybody sits around getting drunk complaining about things.

---

### Post by earthpigg on 2010-07-21
> Good advice, but yeah, a geezer warned of the dangers of static  electricity. I rub my hands on some grounded metal before touching any  internals.

im no electrician, but i've always been told that (after touching grounded metal as you describe) you are supposed to touch the case or PSU, which will evenly distribute any charge you still carry, prior to touching any internals.

> While I appreciate this generous advice, I kind of expected this thread to be more like an episode of 'Cheers' where everybody sits around getting drunk complaining about things.

cant drink, busy procrastinating.

---

### Post by BioBiro on 2010-07-22
> **earthpigg said:**
> May be getting a bit ahead of ourselves. Let's see what memtest and *System* -> *Administration* -> *Disk Utility* have to say.

Update...mate!

Did a SMART Test within 'Disk Utility' on both drives and it showed no errors. By the way - I didn't know I could see the temps of my hard drives! They're around 35c. How cool. Wish Ubuntu worked with my sound card so I could use it properly :(.

MemTest+ passed 100% successfully with no red in sight.

---

### Post by SunnyRabbiera on 2010-07-22
> **BioBiro said:**
> If what happened in every OS? There doesn't seem to be a recurring problem in each of the 3 OS's I have tried recently - Ubuntu didn't support my soundcard, PC-BSD's video drivers failed, and Windows 7 gave me a BSOD because of an apparent driver conflict. I apologise if i've got the wrong end of the stick...

My temps are fine (CPU cores fluctuate around 30c-50c, Northbridge a little higher, and my GPU between 40c-60c depending on load). I will try the MemTest on Ubuntu tommorow - pretty nifty having it built into the bootable media :).

Well maybe you should try another linux, after all Ubuntu is not the only fish in the sea.

---

### Post by Riffer on 2010-07-22
I checked the specks of your MB because I assume that you're using its onboard sound.  The sound chipset is "Realtek ALC889", and after 30 seconds search I found this site

[http://www.opendrivers.com/driver/273359/realtek-hd-audio-codecs-driver-5.04-linux-%282.4-or-2.6%29-free-download.html](http://www.opendrivers.com/driver/273359/realtek-hd-audio-codecs-driver-5.04-linux-%282.4-or-2.6%29-free-download.html)

Which are the drivers for your chipset.

I'm sure that you can find even more info on how to set up your sound chipset in Ubuntu/Linux.

---

### Post by ubunterooster on 2010-07-22
> **SunnyRabbiera said:**
> Well maybe you should try another linux, after all Ubuntu is not the only fish in the sea.
For more distros:  [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by BioBiro on 2010-07-22
> **Riffer said:**
> I checked the specks of your MB because I assume that you're using its onboard sound.  The sound chipset is "Realtek ALC889", and after 30 seconds search I found this site

[http://www.opendrivers.com/driver/273359/realtek-hd-audio-codecs-driver-5.04-linux-%282.4-or-2.6%29-free-download.html](http://www.opendrivers.com/driver/273359/realtek-hd-audio-codecs-driver-5.04-linux-%282.4-or-2.6%29-free-download.html)

Which are the drivers for your chipset.

I'm sure that you can find even more info on how to set up your sound chipset in Ubuntu/Linux.

Thanks, but I want to use my external FireWire soundcard, which is an M-Audio FireWire Solo. There's tons of information on it for Linux use, but at the end of the day I just couldn't make it work.

I'm downloading Fedora and PCLinuxOS to try out later today. Perhaps I will have more success with them than Ubuntu.

---

### Post by masque7 on 2010-07-22
You seem to use a gaming PC if I'm correct? ATI have never been good for graphics driver support on anything but Windows (and I hear people complaining about that). For developers to make open source drivers, ATI would have to meet them at least half way. The same goes with a lot of specialist hardware and peripherals. Most of it is designed to run on Windows.

Taking it you've tried the ATI proprietary drivers if they're available for your card? 

Unless you're rendering HD video or something like that, I've never known someone with such high specs to use Linux. It sounds like you have hardware issues to me as well, although I don't know if that was obvious!

---

### Post by BioBiro on 2010-07-22
> **masque7 said:**
> ...I've never known someone with such high specs to use Linux.

Oh that's awfully kind of you ;). Yes I do enjoy playing games from time to time, but it's an all-round beast of a machine for me. I actually thought I could make the switch to Ubuntu full-time, as the games I play (mostly sim-racing) have a good reputation for running under WINE, and apparently my Logitech G-25 Force Feedback wheel/pedals just about...sort of...works.

 What hardware issues? I ran MemTest86 and got no errors. I've checked my hard disks with the Ubuntu tool and Chkdsk on Windows and got no errors. My temps are fine. I don't have a great reputation for building PC's but this is my first that seems to work just fine!

I did try the ATI proprietary drivers under Ubuntu, but when the desktop (or is it called 'X'?) launched it scrambled the display for a split second each time I booted up into Ubuntu, so I switched to whatever the intial default one was. And anyway - I don't have any graphics problems under Ubuntu - it looks delicious. The only thing holding me back is my FireWire soundcard.

And by the way - there's only really two creators of desktop-level video cards - NVidia and ATI, and the market split isn't *too *far off 50/50 i'm sure. How can you say "Linux doesn't like ATI cards"? Isn't that half of Ubuntu's demographic gone?

---

### Post by masque7 on 2010-07-22
> **BioBiro said:**
> good reputation for running under WINE, and apparently my Logitech G-25 Force Feedback wheel/pedals just about...sort of...works.
WINE is fine for general programs that don't rely too heavily on the Windows API. If you have Windows which is the operating system that your peripherals and software work on, there's only 2 outcomes WINE will give you: luck, and headaches. Why are you using Linux?

 [QUOTE=BioBiro]What hardware issues?[/QUOTE]
It's just simple logic. Multiple operating systems, crashing(?) on all. Has to be hardware.

X (aka Xorg, X11) is the system that 'draws' the graphics onto your screen, communicates with your mouse and keyboard, . There are then desktop environments and window managers which comprise of the graphics, toolkits, default programs, and how they are placed onto the screen.

From my own experience and that of others, ATI cards on Linux are problematic due to driver support. There aren't always open source drivers available, so you have to grab fglrx or the ATI proprietary driver. ATI stop supporting some cards. Again, these are designed to work on Windows, whilst nvidia provide Linux with a lot more. It's just a common fact; one you'll find after experience of either using them, or seeing forum threads.

[IMG]http://solognu.files.wordpress.com/2008/07/rms-sign.jpg[/IMG]

---

### Post by BioBiro on 2010-07-22
> **masque7 said:**
> WINE is fine for general programs that don't rely too heavily on the Windows API. If you have Windows which is the operating system that your peripherals and software work on, there's only 2 outcomes WINE will give you: luck, and headaches. Why are you using Linux?

Cool - I didn't know that about ATI. I trust your word, and i'm sure i'll come across similar statements in the future.

'Why am I using Linux?' is a good question. Erm...well, everyone likes a change! Windows has caused me many major problems in the past, and several times I have been willing to switch to another operating system. Now is one of those times. Linux (according to W3 statistics) is slowly growing in popularity, and i'm forever told that it is aiming strongly at the desktop market. So, I assumed I could take a nice new PC and do everything I did on Windows on it...and more. [B]I almost can.

[/B]The other reason is because I want to develop general Unix skills, which may help me in my career (well, eventually - I graduated a couple of months ago). If I force myself to use Linux rather than Windows, i'll learn fast. I don't know where I want to specialise (e.g. BSD, Linux, HP-UX/AIX, Solaris), but Linux is a good place to start, right? :)

---

### Post by BioBiro on 2010-07-22
I can now report that both the live CD versions of PCLinuxOS and Fedora 13 recognized my motherboard's integrated Intel audio perfectly. What they did not do, however, was detect any presence of my FireWire soundcard. Apart from that it really is a sweet piece of OS...

---

### Post by masque7 on 2010-07-22
> **BioBiro said:**
> The other reason is because I want to develop general Unix skills, which may help me in my career (well, eventually - I graduated a couple of months ago). If I force myself to use Linux rather than Windows, i'll learn fast. I don't know where I want to specialise (e.g. BSD, Linux, HP-UX/AIX, Solaris), but Linux is a good place to start, right? :)
WINE is a hack, don't expect to play your games in it. You'll waste a lot of time trying to get things working. If you want your games play them on the native O/S unless in the WINE appdb they have a gold rating.

I had issues with an Audigy Soundblaster soundcard in Windows 7. It found me a driver, but I guess it wasn't compatible with x86_64, as it worked fine on XP x86. I removed the card and W7 was working fine. 

I'll leave you with a quote "If you learn Ubuntu, you'll know Ubuntu. If you learn Slackware, you'll know Linux."

In other words, Ubuntu is not the disto you want to be using if you want to actually learn Linux or *nix skills, as it hides a lot from the user. If you want a distro where everything "just works", Ubuntu's done that really well (or at least is trying to). Sure, Ubuntu is a good start, but if you want a distro to really learn how GNU/Linux works use something that you'll actually build, and configure such as Slackware, which is about as close to true UNIX Linux gets, and is the oldest distro out there. Other 'manual' distros would be Arch, and Gentoo (if you're willing to compile all of your own software from the ground up, which shouldn't take long with your machine). If you're really serious about it all, you could take a look at a distro called Linux From Scratch.

---

### Post by earthpigg on 2010-07-22
i googled for "M-Audio FireWire Solo linux" and got this:

[http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

it looks to be from 2008, so be sure to read recent comments... 

what other methods have you tried?

---

### Post by earthpigg on 2010-07-22
> **masque7 said:**
> In other words, Ubuntu is not the disto you want to be using if you want to actually learn Linux or *nix skills, as it hides a lot from the user. If you want a distro where everything "just works", Ubuntu's done that really well (or at least is trying to). Sure, Ubuntu is a good start, but if you want a distro to really learn how GNU/Linux works use something that you'll actually build, and configure such as Slackware, which is about as close to true UNIX Linux gets, and is the oldest distro out there. Other 'manual' distros would be Arch, and Gentoo (if you're willing to compile all of your own software from the ground up, which shouldn't take long with your machine). If you're really serious about it all, you could take a look at a distro called Linux From Scratch.

slack, arch, or gentoo... a basic graphical desktop install with hardware configured and whatnot (for a novice) will take you at least several hours. i suggest doing that in a VM to get the feel for it before diving in. prior to attempting to get your very first native install of any of the above, set aside an entire weekend for it, and if you get it done by lunch on Saturday then consider yourself lucky.

don't expect any of these do-it-yourself distros to have any distro specific documentation for new/exotic hardware - there is a very real chance you will be the first one to try combining hardware X with distro Y using kernel/driver Z. you are then expected to figure it all out yourself, document how you did it, and then share it with the rest of the arch/gentoo/slack community.

if you are the first person to figure something out in the commercial distribution Ubuntu, it is regarded as your choice to share or not share the information. go on the Arch forums and say "Hi, i figured out how to do something, but I don't feel like documenting it and sharing it" and you will have a far less friendly response. not that the Arch forums aren't friendly, but every forum has it's quirks and sore spots. including this one. 

take the arch/gentoo/slack monster on when you are ready -- ubuntu is just fine to learn unix on, the only difference is that it will not ***force*** you to.

---

### Post by masque7 on 2010-07-22
If you've built it yourself, you'll know where  everything is, and how everything works. If you've adopted this pre-built system, it is extremely  hard to figure out how things work, there's more to look through. 

You can fire up a terminal on Ubuntu and learn your way through  UNIX commands you'll be learning backwards, because Ubuntu is aimed at providing a graphic system ready for you to use, this takes it away from the intricate workings of the system. Hiding these things away from you makes finding them and learning about GNU/Linux so much harder.

Where's X? What's it do? What are daemons? What ones are running? You set it up this in distos like Arch. When things go wrong in Ubuntu, it's so much harder. For example, if there's a problem with the evince document viewer or totem, the fact that Ubuntu has renamed these to "document viewer" and "totem" just doesn't help. It's taking you further way from the source, making it harder to return. As I said, if you learn Ubuntu, that's what you'll know.

Oh, and the aforementioned distros: Arch, Slack, and Gentoo have fantastic, renowned guides and tutorials and documentation easily available. There's bound to be different attitude from the community between those that have built their operating system, and those that have had something provided to them without choice. Arguably, Ubuntu forces you not to learn UNIX.

Of course, all this may give you an idea of how you'd go around feeling a bit more confident and using the skills and knowledge you've gained to try and get some of that specific hardware working.. in theory.. :)

---

### Post by BioBiro on 2010-07-23
> **earthpigg said:**
> i googled for "M-Audio FireWire Solo linux" and got this:

[http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

it looks to be from 2008, so be sure to read recent comments... 

what other methods have you tried?

I spent quite a bit of time reading that article, and reading other bits and bobs on the Internet (too much to go back and find). I had trouble using the 'realtime kernel' - JACK kept informing me that I wasn't using it, even though i'd followed various instructions on doing so. I also got sample rate errors for which I could find no solution (no results on Google).

> **masque7 said:**
> Oh, and the aforementioned distros: Arch, Slack, and Gentoo have  fantastic, renowned guides and tutorials and documentation easily  available. There's bound to be different attitude from the community  between those that have built their operating system, and those that  have had something provided to them without choice. Arguably, Ubuntu  forces you not to learn UNIX.

We're talking the same language now! I've had a look and Arch Linux and Slackware seem interesting. Doing things manually does teach a lot - i've setup FreeBSD (following the excellent official handbook) with X and KDE/Gnome a few times before, and it taught me 'a bit' (and takes an entire day!). I imagine spending time with Arch or Slackware will be a better place to start than Ubuntu. Even LFS looks like fun \\:D/ - maybe in a while. Thanks.

---

### Post by earthpigg on 2010-07-23
i suggest arch over slackware.

---

### Post by anon.jdh on 2010-07-23
I'm gonna chime in here.

Attitude really can make or break your experiences. Laugh it off and look at it more like Legos.

I've personally never met an Operating System that I didn't dislike but I mold the ones I have into ones that I love.

Don't get so discouraged, Unix and Linux are actually extremely simple. It just took me a decade to figure that out.

---

### Post by masque7 on 2010-07-23
> **earthpigg said:**
> i suggest arch over slackware.
Why's that then?

---

