---
title: "linux responsiveness"
date: 2005-12-19
forum: The Cafe
---

### Post by ae+ on 2005-12-19
Hi there

I was recently playing with a mac running OSX Tiger and one thing that i noticed that was different to Ubuntu was that the mac was a lot more responsive. 

obviously OSX is based on Unix - so how have they been able to achieve this? does the responsiveness come from the kernal or better window managers?

just curious

cheers
andrew

ps. as an aside - i used to love macs, but i find the latest implementation of osx clunky and not very user friendly. i think there are aspects of ubuntu which are more user friendly than osx. i certainly prefer ubuntu over osx anyway.

---

### Post by joshuapurcell on 2005-12-19
When you say responsive, do you mean how fast programs open up? Also, was the comparison you have made between the two OSes done on the exact same hardware?

---

### Post by super on 2005-12-19
i'm guessing the op means desktop responsiveness. to me linux is the most responsive. both winxp and osx have the dreaded 'wait' cursor. (i hate that thing!! *shudder*) at least in linux i can still switch workspaces, change the playing song, start a new solitaire game, etc...  while waiting for my program to open. :razz: 

in other words, in linux my whole desktop doesn't go unresponsive while waiting on a program to open. so it's ok that firefox and oo.org take longer to start in linux than in winxp. :D 

also i find that a nvidia/ati card with 3d acceleration makes a huge difference.

---

### Post by xequence on 2005-12-19
Windows XP is really unresponsive after a week of having it installed. Ubuntu gnome is sort of like this - as if you press 2 - 4 programs at the same time they will take forever to all come up. But you can do other things while waiting.

Ubuntu terminal is fastest. Duh.

---

### Post by gord on 2005-12-19
it really depends on your hardware and what you have going. my xp installation is extreamly responsive but thats because i have it stripped down so nearly all the services are turned off and the resolution is low (only use it for gaming). and sometimes my gnome desktop is encridbly responsive but if im doing a thousand things allready its not. 

its all relitive ;)

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=ae+]Hi there

I was recently playing with a mac running OSX Tiger and one thing that i noticed that was different to Ubuntu was that the mac was a lot more responsive. 

obviously OSX is based on Unix - so how have they been able to achieve this? does the responsiveness come from the kernal or better window managers?
[/QUOTE]

If you are talking about "snappiness" of the applications and windows its because of the superior display framework OSX has. OSX's "xserver like thing" (I know the real name, I'm trying to explain) has full hardware acceration that scales well to all graphics hardware. This is also why an iMac from three years ago at my school can have Expose with live thumbnails (aka the thumbnails in Expose show whats going on in program) without stuttering or can do the "genie effect" without blinking. 

[http://en.wikipedia.org/wiki/Quartz_Extreme](http://en.wikipedia.org/wiki/Quartz_Extreme)
> 
Starting with Mac OS X v10.2, Quartz Compositor was extended by Quartz Extreme, which uses OpenGL to render screen displays faster by presenting them as textures within a 3D OpenGL context. This permits faster compositing of screen images using 3D hardware acceleration.

In Mac OS X v10.4, Apple introduced Quartz Extreme 2D, increased the speed of the actual drawing operations as well, so that as much of the compositing and drawing was taken over by the graphics card as possible. Note that QE2D is not enabled by default, possibly due to instability. In order to enable QE2D, one must use the Quartz Debug tool included with Apple's Xcode 2.0 developer tools. QE2D will most likely be enabled permanently in a later edition of Mac OS X.

Linux's Xorg is very primative in comparision- I personally think the xserver the the most "behind" part of the Linux desktop (especially when Vista and its Aero Glass is released and we still won't have a fully functional Opengl Xserver).

[http://www.freedesktop.org/~jonsmirl/graphics.html](http://www.freedesktop.org/~jonsmirl/graphics.html)

Yet I still answered my Linux Gnome box. Why? Because first of all I use Xcompmgr near full time and with xcompmgr I get the same hardware acceration that comes with Macs (well....not the same, its far more primitive...."a toy" in comparison) and Nvidia's drivers make this all fast.

[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

Second of all, I have never used a Mac that costs more than $2000 and I have never seen a $2000 or less Mac that even compares to the speed of my AMD 3800+ X2. The two cores make it seem like Gnome is much "snappier" because when I am doing something on one core the other is allowed to do the heavy CPU work Metacity (the Gnome window manager) needs to do its stuff.

Its sad that a $500 Macmini can "feel" faster than a $1000 Dell with Ubuntu because of this, but personally a Mini does not meet any of my top needs (like easy dual monitor setups).

---

### Post by ae+ on 2005-12-19
Thanks poofyhairguy,

Thats exactly the answer i was after. 

In response to other questions - I was using a iMac whose hardware was considerably worse than my ubuntu box. Obviously programs were a lot faster in Ubuntu. what was slower was desktop responsiveness. Sorry for not making this clearer.

---

### Post by prizrak on 2005-12-20
The Xserver is very much behind the times, anyway you slice it Linux is more of a work OS than a play OS. Most of it evolved accordingly, it can multitask like nobody's business and a 100% CPU load does not stop your computer cold in its tracks. But the graphics are very crude and unoptimized. The worst is laptops since they don't normally get nVidia and ATI cards

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=ae+]Thanks poofyhairguy,

Thats exactly the answer i was after. 
[/QUOTE]

Glad to be helpful.

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=prizrak]The Xserver is very much behind the times, anyway you slice it Linux is more of a work OS than a play OS. [/QUOTE]

Except for the whole E17 crowd. And people like me.


>  The worst is laptops since they don't normally get nVidia and ATI cards

Actually those Intel cards are great- their specs are open. In a year the average laptop with an Intel Graphics card will be better for desktop eye candy in Linux than a brand new ATI card (that is from the r300 or better series).

---

### Post by raublekick on 2005-12-20
[QUOTE=poofyhairguy]Actually those Intel cards are great- their specs are open. In a year the average laptop with an Intel Graphics card will be better for desktop eye candy in Linux than a brand new ATI card (that is from the r300 or better series).[/QUOTE]


Reeeeaaaally?

That's quite interesting to hear. I never looked into it much but I got the impression that they were a pain in Linux. But, I've been thinking about buying a laptop, and that's good to know. I need to buy something from Dell or HP, or anywhere that let's me pay monthly, and it's hard to find nvidea chipsets in laptops with other specs I want.


More ontopic, I find Ubuntu (and Linux in general) to be way more responsive than both OSX and XP. Like others said, even though programs may open slower, you aren't stuck twiddling your thumbs until it does. I think it's safe to say that most, if not all, computer users multitask, so being able to do simple little things while waiting for something to open is really nice.

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=raublekick]Reeeeaaaally?

That's quite interesting to hear. I never looked into it much but I got the impression that they were a pain in Linux.[/QUOTE]

You know that famous video of Luminocity, and how everyone brags that it runs on a "cheap laptop?" It does that because the Intel card in that cheap laptop has a good opensource driver. When I ran Luminocity on my high end computer with a new ATI card (flgrx) it was slow as all get out.

Intel is one of the best supporters of Linux. I think they got mad that MS broke the deal between them (to have a release every few years to force people to upgrade more). Or they got made because MS picked AMD's 64 bit extensions over theirs. Either way, we benefit.

>  But, I've been thinking about buying a laptop, and that's good to know. I need to buy something from Dell or HP, or anywhere that let's me pay monthly, and it's hard to find nvidea chipsets in laptops with other specs I want.


I have one suggestion then:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)

---

### Post by dare2dreamer on 2005-12-20
Maybe I've gone to deep-geek for my own good, but did anyone else read the poll and think, "Hey, rxvt/aterm/xterminal/etc is way faster than gnome-terminal!"

I think my constant switching between an ubuntu desktop and a damnsmalllinux laptop is showing again. ;-)

---

### Post by angkor on 2005-12-20
[QUOTE=dare2dreamer]"Hey, rxvt/aterm/xterminal/etc is way faster than gnome-terminal!"[/QUOTE]

Don't know about the others but aterm is definately waay faster. I thought the OP meant the console which is of course the most responsive of all the options.

Yet I chose OSX because it's not fair comparing a text-mode to full graphical mode. I only have experience on Powermac G5 of a friend of mine. The damn thing cost more than 3500 bucks but it's responsive like hell...:) But hey I've never seen Ubuntu run on a machine with 2 64bit 2Ghz+ procs + 4G Ram so I can't say for sure the Mac is more responsive.

---

### Post by Jason-X on 2005-12-20
Ubuntu breezy on my G4 iMac (1000 MHz, 256MB) is very fast. Compaired to OS X Tiger it feels like I've doubled my Memory and CPU. Everything feels alot snappier.:).

I had to go around to a friends house this morning to show her how to do something in OS X and I could not believe how slow and bloated it felt off to Ubuntu/Gnome.

.....and people say Gnome is slow and bloated:rolleyes:

---

### Post by prizrak on 2005-12-20
[QUOTE=poofyhairguy]Except for the whole E17 crowd. And people like me.




Actually those Intel cards are great- their specs are open. In a year the average laptop with an Intel Graphics card will be better for desktop eye candy in Linux than a brand new ATI card (that is from the r300 or better series).[/QUOTE]
E17 still runs on the same ole X, I think the backend could benefit from being redone (unfortunately I don't have enough programming knowledge to help with that). Eyecandy is not the biggest issue, the speed is. My desktop and my laptop have very close specs cept for the video (desktop runs a GF4MXsomething (can't remember which one I remember its the one with AGP8X interface)) and the desktop is noticeably snappier than the laptop. The laptop ain't slow with openbox as a WM but desktop still wins.

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=ae+]Hi there

I was recently playing with a mac running OSX Tiger and one thing that i noticed that was different to Ubuntu was that the mac was a lot more responsive. 

obviously OSX is based on Unix - so how have they been able to achieve this? does the responsiveness come from the kernal or better window managers?
[/QUOTE]
I feel the responsiveness is also the result of lack of drivers for hardware. linux-hardware-specific-+-working-correctly-drivers are hard to find. 
PS. terminal in Win is very responsive as well :P

---

### Post by raublekick on 2005-12-20
[QUOTE=poofyhairguy]I have one suggestion then:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)[/QUOTE]

Thanks for the link. Unfortunately none of those meet mydesired specs (100GB hard drive, 1GB RAM)

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=prizrak]E17 still runs on the same ole X, I think the backend could benefit from being redone (unfortunately I don't have enough programming knowledge to help with that).[/QUOTE]

Don't worry- the best eye candy programmer in Linuxland is working on it.

> 
 Eyecandy is not the biggest issue, the speed is. 

Both problems have the same solution.

> 
My desktop and my laptop have very close specs cept for the video (desktop runs a GF4MXsomething (can't remember which one I remember its the one with AGP8X interface)) and the desktop is noticeably snappier than the laptop. 

Because of Nvidia's renderaccel? Its great for 2D speed.

---

### Post by prizrak on 2005-12-20
> Because of Nvidia's renderaccel? Its great for 2D speed.
Not sure why but it's REAL good :) (I use the nVidia proprietary driver)

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=prizrak]Not sure why but it's REAL good :) (I use the nVidia proprietary driver)[/QUOTE]

Renderaccel is Nvidia's EXA.

---

### Post by daveisadork on 2005-12-20
Using Ubuntu 5.10 on an Intel P4 system with a GeForce PCX5750 and proprietary drivers, it blows everything out of the water. So silky smooth and fast, no tearing or sticking of windows like Windows. OSX has always felt sluggish to me... almost like it can't keep up while I'm trying to work. 

For example, using two screens, many times I'll need to "throw" a window from one screen to the other. With my Ubuntu rig, it's a simple click and flick of the wrist. Attemping it the same way with OSX moves the window about 100 pixels, you have to be very deliberate with it. Windows is just annoying.

---

### Post by reedlaw on 2005-12-20
Why does my Gnome with Nvidia drivers (GeForce FX 52000) feel so slow?  Should I uninstall the packaged drivers and install the latest from Nvidia?  When I switch between Evolution and Firefox I can see the windows being refreshed before my eyes.  In Windows I remember switching windows seemed almost instantaneous.  Also, I can't playback a full 720p HDTV video that I downloaded.  I could play them back in Windows on the same machine.  They are only short trailers but both the sound and video lag and drop huge quantities of frames.

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=reedlaw]Why does my Gnome with Nvidia drivers (GeForce FX 52000) feel so slow?  Should I uninstall the packaged drivers and install the latest from Nvidia?  When I switch between Evolution and Firefox I can see the windows being refreshed before my eyes.  In Windows I remember switching windows seemed almost instantaneous.  Also, I can't playback a full 720p HDTV video that I downloaded.  I could play them back in Windows on the same machine.  They are only short trailers but both the sound and video lag and drop huge quantities of frames.[/QUOTE]

Sounds like you need some XFCE love (for the record I also have a 5200 and its renderaccel is not near as fast as my 6600 GT in the same machine- limit of hardware).

sudo apt-get install xubuntu-desktop

---

### Post by poofyhairguy on 2005-12-20
[QUOTE=daveisadork]Using Ubuntu 5.10 on an Intel P4 system with a GeForce PCX5750 and proprietary drivers, it blows everything out of the water. So silky smooth and fast, no tearing or sticking of windows like Windows. OSX has always felt sluggish to me... almost like it can't keep up while I'm trying to work. 
[/QUOTE]

Its not OSX- its the damn CPUs that come with the Macs. My sister has a new Powerbook and its easy to max out that G4. There is a reason Apple is finally getting on the x86 train.

---

### Post by reedlaw on 2005-12-21
> Sounds like you need some XFCE love (for the record I also have a 5200 and its renderaccel is not near as fast as my 6600 GT in the same machine- limit of hardware).

sudo apt-get install xubuntu-desktop

I have installed XFCE and I get about the same results playing back 720p HDTV movie trailers.  I am thinking of trying Gentoo or FreeBSD on this machine to see if I can get any better results.  Open Source must have a way to compete with Windows in video playback.  It seems like codecs are no problem but the framerate and CPU usage are ridiculous.

---

### Post by poofyhairguy on 2005-12-21
[QUOTE=reedlaw]I have installed XFCE and I get about the same results playing back 720p HDTV movie trailers.  I am thinking of trying Gentoo or FreeBSD on this machine to see if I can get any better results.  Open Source must have a way to compete with Windows in video playback.  It seems like codecs are no problem but the framerate and CPU usage are ridiculous.[/QUOTE]

For those files I have the best luck with the VLC.

Or you can use Gxine and go into the options and turn down the post processing a little. Its set really high by default.

---

### Post by reedlaw on 2005-12-21
I was using VLC too for best results.  Even so the video is unwatchable.  I just tried gxine without any better results.

---

### Post by suoko on 2005-12-22
I'd like to see gnome responsiveness by enabling renderaccel on my geforce 256 but unfortunatley it freezes the whole OS !!
Does anyone know if that's because of nvidia legacy drivers?
Why the renderaccell option is causing the freeze?
Do I have to tweak something before enabling it?

---

### Post by suoko on 2005-12-27
Now that I switched from metaciy to sawfish I'm happy to say gnome is now more responsive.

Long live to sawfish !!

---

### Post by BSDFreak on 2005-12-27
[QUOTE=poofyhairguy]For those files I have the best luck with the VLC.

Or you can use Gxine and go into the options and turn down the post processing a little. Its set really high by default.[/QUOTE]

Or Mplayer and if you have ANYTHIGN above a 300Mhz cpu you'll be able to pull that post processing slider all the way up.

---

### Post by GoA on 2005-12-28
Windows XP is a lot faster than ubuntu on single application speed. However, Ubuntu is a lot better on multitasking, because it was designed for that. But on my use, I prefer single application speed because I don't do heavy multitasking. Because of that, Windows XP feels faster.

---

### Post by poofyhairguy on 2005-12-28
[QUOTE=suoko]I'd like to see gnome responsiveness by enabling renderaccel on my geforce 256 but unfortunatley it freezes the whole OS !!
Does anyone know if that's because of nvidia legacy drivers?
Why the renderaccell option is causing the freeze?
Do I have to tweak something before enabling it?[/QUOTE]

The card is too weak.

---

### Post by reedlaw on 2005-12-30
From the Wiki, apparently legacy GForce cards don't support RenderAccel.  Although my desktop has a GForce 5200 I can't tell exactly what benefit the RenderAccel brings.  Windows refresh and responsiveness are about the same in my laptop with i915 video.

---

### Post by poofyhairguy on 2005-12-30
[QUOTE=reedlaw]From the Wiki, apparently legacy GForce cards don't support RenderAccel.  Although my desktop has a GForce 5200 I can't tell exactly what benefit the RenderAccel brings.  Windows refresh and responsiveness are about the same in my laptop with i915 video.[/QUOTE]

I've had many Nvidia cards in Linux (Geforce 420 GO, Geforce 4 MX 64 mb, Geforce 5200 64mb, 6600 GT 128 mb) and the only one that really gave me stable and fast renderaccel and composite is my 6600 GT. 

Not to say you can't use it on older cards. Renderaccell worked on the 5200 FX, just not composite as much. I think RAM is hte big limitation.

---

### Post by reedlaw on 2005-12-31
My sister's desktop has a GForce2 MX 100/200 and it crashes regularly when doing 3d acceleration.  When an OpenGL screensaver starts or I open tuxracer it will regularly crash after about 10 seconds.  Has anyone else ever experienced this problem?  Should I file a bug?  This behaviour did not exist in Windows, so it isn't hardware related.  I have RenderAccel off and nvidia-glx-legacy drivers.

---

