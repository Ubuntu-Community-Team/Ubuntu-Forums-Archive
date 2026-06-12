---
title: "Improving the speed and responsiveness of Ubuntu/GNOME."
date: 2007-08-27
forum: The Cafe
---

### Post by PrimoTurbo on 2007-08-27
**_[COLOR="Red"]EDIT: Here are 2 videos comparing the speed of my Windows XP tweaked setup and Ubuntu 7.04 which is also very tweaked. The software used to record both uses quite a bit of CPU so this is not a 100% accurate representation of speed and responsiveness. However it's a decent idea or maybe even benchmark/indication of the problem. Also keep in mind Ubuntu [U]doesn't have the resizing artifacts_ you see this is due to _gtk-recordMyDesktop_ not recording it correctly. Both desktops are about 20-30% faster with out the recording software, but still Ubuntu is significantly slower then Windows XP!!![/COLOR][/U]**

**Ubuntu 7.04** (Slow, sluggish and not very responsive) - [http://www.mediafire.com/?agyc15ebtug](http://www.mediafire.com/?agyc15ebtug) (**Download 7MB**)
**VS**
**Windows XP Pro** (Very responsive and fast) - [http://www.youtube.com/watch?v=qPhbHp7WhGg](http://www.youtube.com/watch?v=qPhbHp7WhGg)


I'm not satisfied with my Ubuntu performance, even with a tweaked system and using a light Desktop Environment like Xubuntu I notice little to no improvement in responsiveness of the interface and the general speed of the system.

**My system specs are the following:**
Pentium 4 1.6Ghz
Generic 768MB of DDR RAM PC2100
Western Digital 250GB Hard Drive
ATI 9700 Pro 128MB

I'm using a new up to date install of Ubuntu 7.04, I have installed the ATI restricted fglrx driver. My 3D performance works nearly thesame as  on Windows, Quake3 engine based games run at over 100FPS with everything on except AA and VSync. I have no issues as far as 3D.

My boot speed is also very fast and nearly identical to my Windows XP partition, around 30 seconds.

Currently I have a vanilla setup of Ubuntu/GNOME with NO compiz/beryl or any other special effects. I have the same problems under XFCE & KDE

**[COLOR="Red"]My problems:[/COLOR]**
[LIST]
[*]Slow rendering of windows and slight artifacts left after minimizing for approximately 0.5 seconds, for example favicon in Firefox.
[*]Resizing, minimizing is a few seconds slower compared to my Windows setup.
[*]Having multiple windows open overlaying each other greatly decreases the overall responsiveness of resizing, moving and minimizing windows.
[*]Sluggish Firefox performance compared to Windows XP, especially in regards to scrolling.
[*]Slight delay and drawing of menu and desktop icons, approximately half a second of delay.
[*]High CPU usage when scrolling, minimizing, resizing and moving windows. Approximately 50-70% CPU usage.
[/LIST]

My RAM usage on Ubuntu is very low compared to Windows XP, Ubuntu uses about 140-160MB of RAM while Windows XP uses around 170-200MB.

I tried downgrading libxll to 6_1.0.3 and forcing version, as suggested here. - [COLOR="Red"][B][URL="
https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815"]Sluggish rendering since xorg 7.2 update[/URL][/B][/COLOR]

I didn't notice any real improvement.

I have tried most of the links crimesaucer has provided me in my other threads (Thanks BTW), but I only noticed slight application startup increases and not general rendering issues that I have.

> **crimesaucer said:**
> I used a lot of tips from this sidux list I found. I checked most of the tips out on Google and they seemed to be used in many different guides for speeding up your system: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

I only used the tips that I felt comfortable with on my laptop.

However, I didn't agree with all of the Firefox about:config tips, I prefer to follow this guide: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

....using the 2.0.0.5 settings from this page: [http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)

and also these pages:
[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)
[http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Layout.word+select.stop+at+punctuation](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Layout.word+select.stop+at+punctuation)
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)


> **crimesaucer said:**
> I found this off of digg.com: [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

and: [http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

...they basically say the same things.

This also helped a little: [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

and Swiftweasel: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)



....also, for both of my posts, they have a setting for "vm.swappiness=0" which I didn't do because I only have 512MB ram and I figured I wouldn't mess with my swap file, because sometimes I need it.

> **crimesaucer said:**
> That was a very good link, the problem is, that a few (almost half) of those are very old (for Dapper)...but there is a lot of real good info in most of those links, just make sure it's current.


What's good about a lot of those links, plus the links that I posted, is that they have the same tweaks for basically all of the settings like Broadband Internet, Swapping, and Concurrent Booting, so at least you know the info is correct, and you have more then one source of info to feel safe about these system tweaks.


Since I originally used this guide a while back (as well as a couple others that were on your page because all of them had the same info): [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)


And then added these ones from your page today: [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

another about Local DNS: [http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)


...and this one for noatime,data=writeback and: [http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)


...and I finally tried prelinking, and I can say that my computer feels even faster now...and it was already fast.

I also tried various kernels and even built my own with no changes in speed what so ever. IceWeasle, Firefox and SwiftFox all work at the same speed. 

==========================

**[COLOR="Green"]HAS ANYONE ELSE EXPERIENCED SUCH PROBLEMS and IF SO, CAN YOU PLEASE PLEASE HELP ME!!! Sorry about the CAPS I'm just really frustrated with my poor Ubuntu performance. [/COLOR]**

The default "ATI" video driver gives me the same performance on Ubuntu except I also have poor 3D performance.

What else can I try, I think what's happening is that my video card is not rendering my desktop but my CPU is and therefore I get slowdowns and spikes. Thanks.

---

### Post by RAV TUX on 2007-08-27
What other distros have you tried?

---

### Post by PrimoTurbo on 2007-08-27
PCLinuxOS = A little faster than Ubuntu
Fedora = same as Ubuntu or slower
Sabayon = same as Ubuntu
Debian = same as Ubuntu
MEPIS = same as Ubuntu
Mandriva = same as Ubuntu
Puppy = Fast as hell but, but I want something more modern
Vector = Faster than Ubuntu
Freespire = same as Ubuntu
SUSE = slower than Ubuntu
Xandors = a bit faster than Ubuntu

I used more but I can't remember now.

---

### Post by FuturePilot on 2007-08-27
> Sluggish Firefox performance compared to Windows XP, especially in regards to scrolling.
I think that is just Firefox. Firefox acts differently on Linux. It's slower for some reason.
> High CPU usage when scrolling, minimizing, resizing and moving windows. Approximately 50-70% CPU usage.
Might be normal. I get about 50-70% CPU spikes when doing that stuff in Windows too.

---

### Post by PrimoTurbo on 2007-08-27
I also get high CPU use in Windows but not as high as Linux and Windows is a lot more smoother and responsive than Xubuntu for example.

Also I am very picky about menu delay and such, I need it as fast as possible.

Here is a video I made a while back showing the rendering speed of Windows XP, keep in mind that the recording software CamStudio that I used to make the video slowed my desktop performance quite a bit.

[http://www.youtube.com/watch?v=qPhbHp7WhGg](http://www.youtube.com/watch?v=qPhbHp7WhGg)

I haven't been able to do a video of Ubuntu because running any recording software greatly slows everything down and video has a bunch of artifacts. Maybe I will try it however.

---

### Post by FuturePilot on 2007-08-27
> **PrimoTurbo said:**
> I also get high CPU use in Windows but not as high as Linux and Windows is a lot more smoother and responsive than Xubuntu for example.
Regarding the sluggishness you might want to take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=478309") I made a while ago, specifically at [this post (#6)]("http://ubuntuforums.org/showthread.php?t=478309&postcount=#6")

---

### Post by crjackson on 2007-08-27
> **PrimoTurbo said:**
> I also get high CPU use in Windows but not as high as Linux and Windows is a lot more smoother and responsive than Xubuntu for example.

Also I am very picky about menu delay and such, I need it as fast as possible.

Here is a video I made a while back showing the rendering speed of Windows XP, keep in mind that the recording software CamStudio that I used to make the video slowed my desktop performance quite a bit.

[http://www.youtube.com/watch?v=qPhbHp7WhGg](http://www.youtube.com/watch?v=qPhbHp7WhGg)

I haven't been able to do a video of Ubuntu because running any recording software greatly slows everything down and video has a bunch of artifacts. Maybe I will try it however.

The menu delay is a pet peeve of mine too.  It can be easily tweaked for no delay.  If you are looking for that let me know and I'll hook it up for you.

I'm at work right now so it'll have to wait until I get home.

I also do other tweaks to speed up the gnome interface but tell me what you have done already.  You said you have it tweaked so it may be beating a dead horse.  How did you tweak?

---

### Post by Acglaphotis on 2007-08-27
There is a menu delay in the deafult gnome menu. Make a file called .gtkrc-2.0 and add this line to it
```

gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0 

```

That will speed up the menus a little.

---

### Post by PrimoTurbo on 2007-08-27
> **crjackson said:**
> The menu delay is a pet peeve of mine too.  It can be easily tweaked for no delay.  If you are looking for that let me know and I'll hook it up for you.

I'm at work right now so it'll have to wait until I get home.

I also do other tweaks to speed up the gnome interface but tell me what you have done already.  You said you have it tweaked so it may be beating a dead horse.  How did you tweak?

I removed the minimize animation with gconf-editor, and all the stuff mentioned above.

Why what tweak can u suggest as far as menu delay for GNOME?

---

### Post by PrimoTurbo on 2007-08-27
> **Acglaphotis said:**
> There is a menu delay in the deafult gnome menu. Make a file called .gtkrc-2.0 and add this line to it
```

gtk-menu-popup-delay = 0"| tee -a .gtkrc-2.0 

```

That will speed up the menus a little.

I actually did this already, it doesn't have any real effect for me. The problem is with xorg I think, it's very slow in general.

Is it possible to replace it or fix it some how?

---

### Post by crjackson on 2007-08-27
> **PrimoTurbo said:**
> I actually did this already, it doesn't have any real effect for me. The problem is with xorg I think, it's very slow in general.

Is it possible to replace it or fix it some how?

That menu tweak makes a HUGE difference on my systems, also using reduced resources for metacity is something I was going to mention, and turning off global animation.  You may have already done these things though.

My tweaked out XP and tweaked out ubuntu run neck and neck, with the edge for ubuntu...

---

### Post by PrimoTurbo on 2007-08-27
> **crjackson said:**
> That menu tweak makes a HUGE difference on my systems, also using reduced resources for metacity is something I was going to mention, and turning off global animation.  You may have already done these things though.

My tweaked out XP and tweaked out ubuntu run neck and neck, with the edge for ubuntu...

Can you explain more about reduced resources, is the gconf-editor tweak that adds wireframes and no minimize animation? I removed the wireframe by enabling ATP btw.

How do you turn OFF global animation?

I'm going to post a video of my Ubuntu sluggish & slow desktop in a second.

---

### Post by macogw on 2007-08-27
I think it's weird how people say this.  It seems like the older the hardware, the bigger a speed difference in Ubuntu's favor.  People with 5-ish year old boxes always say Windows was faster, but my 9-year-old was faster with Ubuntu than XP (and now it's even faster with Debian and E17).

---

### Post by Anthem on 2007-08-27
Can somebody explain the menu delay thing?  What possible purpose does that serve?

---

### Post by Crashmaxx on 2007-08-28
I'm guessing its the ATi card and the open driver. They just aren't that great all the time. And there may be something in the xorg.conf that is causing it, but I have no idea.

I have a similar setup, and have used ubuntu on a lot less powerful systems. But I can't remember having any of the problems you describe. I just tried a few and they are almost instantaneous. I use Swiftfox, but I don't remember having issues with Firefox either, and it scrolls about as fast as I can spin the wheel. All the resizing and such, is pretty close to real time.

The only time I have seen this kind of thing, is my brother's computer with the nv driver. I installed the nvidia driver and it was like mine is now.

The proprietary nvidia drivers work great, I haven't had such success with any of the ATi drivers. So I would say that is where the majority of the problem lies.

---

### Post by FuturePilot on 2007-08-28
> **macogw said:**
> I think it's weird how people say this.  It seems like the older the hardware, the bigger a speed difference in Ubuntu's favor.  People with 5-ish year old boxes always say Windows was faster, but my 9-year-old was faster with Ubuntu than XP (and now it's even faster with Debian and E17).

I have a 5 year old laptop and Ubuntu is way faster than Windows. Even a clean install of Windows:p

---

### Post by stmiller on 2007-08-28
> **PrimoTurbo said:**
> 

**[COLOR="Red"]My problems:[/COLOR]**
[LIST]
[*]Slow rendering of windows and slight artifacts left after minimizing for approximately 0.5 seconds, for example favicon in Firefox.
[*]Resizing, minimizing is a few seconds slower compared to my Windows setup.
[*]Having multiple windows open overlaying each other greatly decreases the overall responsiveness of resizing, moving and minimizing windows.
[*]Sluggish Firefox performance compared to Windows XP, especially in regards to scrolling.
[*]Slight delay and drawing of menu and desktop icons, approximately half a second of delay.
[*]High CPU usage when scrolling, minimizing, resizing and moving windows. Approximately 50-70% CPU usage.
[/LIST]


I hate to give you the bad news, but these are all symptoms of a crappy video driver. ATI is bad under Linux. Try to specify a non-3D driver (fbdev) in your xorg.conf and see if all of these problems instantly go away. Then you have your answer.

Your only other options are to hack a better xorg.conf for your card (if you need 3D).

---

### Post by PrimoTurbo on 2007-08-28
I've been trying to put up a video of my Ubuntu desktop for the past hour and recordMyDesktop is such a POS. I get a 7mb file that's about 1 minute long, video player reports it's 1 hour and 47 minutes long and YouTube also thinks the file is too long. FFS, I can't find a way to fix it either....GRRR

Here is my tweaked xorg.org but even the default version gives me the exact same performance! :(

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
 	Option 		"DRI" 		"true"
 	Option 		"RenderAccel" 	"true"
 	Option 		"EnablePageFlip" "true"
 	Option 		"XAANoOffscreenPixmaps"
 	Option 		"AGPMode" 	"4"
 	Option 		"AccelMethod" 	"XAA"
 	Option 		"ColorTiling" 	"on"
 	Option 		"AGPFastWrite" 	"on"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

Also I removed resolutions that I don't use.

---

### Post by stmiller on 2007-08-28
I'm not sure if the Community Cafe is a place for troubleshooting. There are already tons of threads and ubuntu how-tos for tweaking ATI xorg.conf settings...

---

### Post by PrimoTurbo on 2007-08-28
Alright here it is:

Here are 2 videos comparing the speed of my Windows XP tweaked setup and Ubuntu 7.04 which is also very tweaked. The software used to record both uses quite a bit of CPU so this is not a 100% accurate representation of speed and responsiveness. However it's a decent idea or maybe even benchmark/indication of the problem. Also keep in mind Ubuntu doesn't have the resizing artifacts you see this is due to gtk-recordMyDesktop not recording it correctly. Both desktops are about 20-30% faster with out the recording software, but still Ubuntu is significantly slower then Windows XP!!!

**Ubuntu 7.04 (Slow, sluggish and not very responsive)** - [http://www.mediafire.com/?agyc15ebtug](http://www.mediafire.com/?agyc15ebtug) (Download 7MB)
_VS_
**Windows XP Pro (Very responsive and fast)** - [http://www.youtube.com/watch?v=qPhbHp7WhGg](http://www.youtube.com/watch?v=qPhbHp7WhGg)

---

### Post by slavik on 2007-08-28
even though the linux kernel might be unresponsive at times, it does have more throughput than you might think. this is one of the reasons why someone left the kernel project (I forget his name) ...

2.6.23 should have group scheduling for the CFS which would allow the kernelto give more CPU to interactive user's tasks as a whole. :)

---

### Post by PrimoTurbo on 2007-08-28
So tell me no one else experiences such issues on a medium/low system, I mean I know my computer is old but it's still very functional and I would think that it should be more then enough for general use...

Anyone else has any more ideas?..

Is it possible to replace xorg, are there other alternatives?...

---

### Post by Crashmaxx on 2007-08-28
Honestly, your best bet is just to use integrated Intel graphics (if you mobo has that) or buy an Nvidia card. You can get a 6000 series one for less then $50 now. I run a 6300 with 128mb of ram and it just flys. Even with beryl and a lot of effects it just runs great.

That may not be what you are looking for and their may be some other solution as there are at least 3 different ATi drivers (ati, radeon, fglrx) and a lot of xorg settings.

But the propriety nvidia drivers are just so much better and new open source ones are under development, that it is just easier to use them instead.

---

### Post by mips on 2007-08-28
Try KDE ?

---

### Post by lonce on 2007-08-28
I put together a "How To" for tweaking ubuntu.  Its hosted at my wiki.  If you do a search for "speed up Ubuntu" in google, it should be the first or second listed.  It got dugg and I have had allot of reponses saying it helped allot.

Here is the link.

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

---

### Post by reacocard on 2007-08-28
> **lonce said:**
> I put together a "How To" for tweaking ubuntu.  Its hosted at my wiki.  If you do a search for "speed up Ubuntu" in google, it should be the first or second listed.  It got dugg and I have had allot of reponses saying it helped allot.

Here is the link.

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

kmandla also has a speed-tweaking guide: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)
it has everything yours does and more.

On another note, I find that my system actually seems smoother and more-responsive with compiz enabled. I currently run compiz atop a minimal xfce and it's blazing fast.

---

### Post by Wolki on 2007-08-28
> **Anthem said:**
> Can somebody explain the menu delay thing?  What possible purpose does that serve?

It makes the menus seem more stable. If you disable the menu delay, submenus will open even if you don't intend them to, leading to more visual noise and distraction, and in the end making you slower.

It might be a couple of miliseconds too long, but not enough that it bothered me yet.

---

### Post by crjackson on 2007-08-28
> **PrimoTurbo said:**
> Can you explain more about reduced resources, is the gconf-editor tweak that adds wireframes and no minimize animation? I removed the wireframe by enabling ATP btw.

How do you turn OFF global animation?

I'm going to post a video of my Ubuntu sluggish & slow desktop in a second.

I'm at work right now so I'll have to answer this when I get home.  I'll have to look through the editor and find the settings.  The way to get rid of the wire frames and show the whole window when dragging is to ENABEL desktop application accessibility.

---

### Post by FuturePilot on 2007-08-28
> **PrimoTurbo said:**
> 

Is it possible to replace xorg, are there other alternatives?...
I think [this ]("http://ubuntuforums.org/showpost.php?p=2873259&postcount=6")should answer your question

---

### Post by PrimoTurbo on 2007-08-29
Thanks for your help, I have posted a version of my original post on my blog [http://ubuntucorner.blogspot.com](http://ubuntucorner.blogspot.com) in case someone else comes across it.

---

### Post by crjackson on 2007-08-30
> **PrimoTurbo said:**
> Can you explain more about reduced resources, is the gconf-editor tweak that adds wireframes and no minimize animation? I removed the wireframe by enabling ATP btw.

How do you turn OFF global animation?

I'm going to post a video of my Ubuntu sluggish & slow desktop in a second.
```
 gconf-editor
```

from there go to:
/apps/metacity/general and check off reduced_resourses

also:
/apps/panel/global and uncheck enable_animations

also:
/desktop/gnome/interface and check off the box for accessibility

---

### Post by Altarbo on 2007-08-30
This has already been mentioned, but the problem is most likely with your video card driver.  You could try changing your driver to "fbdev" (non accelerated general purpose driver) in your xorg.conf.

If you're not sure that it's your video card driver and want to test, you could do so by installing and setting up Compiz.  If your card has working drivers then the cpu load of rendering the screen will be increased, but passed to the gpu, so your box will become faster.  If your card has faulty drivers, then cpu load will just be increased and your box will slow down.

In the future, if you want to build or buy a Linux box, I'd recommend getting an Nvidia card.  The drivers written by Nvidia are much better.  (I guess ATI doesn't see Linux as a big enough market?)

---

### Post by Guus on 2007-08-30
You could try using Epiphany instead of Firefox, it uses the same rendering engine as Fiefox (Gecko) but its alot lighter

You could also try Abiword and Gnumeric for wriing and spreadsheet tasks :)

---

### Post by happysmileman on 2007-08-30
> **macogw said:**
> I think it's weird how people say this.  It seems like the older the hardware, the bigger a speed difference in Ubuntu's favor.  People with 5-ish year old boxes always say Windows was faster, but my 9-year-old was faster with Ubuntu than XP (and now it's even faster with Debian and E17).

I have 5 year old box, Kubuntu kicks XP's ***

---

### Post by smartboyathome on 2007-08-30
> **Guus said:**
> You could try using Epiphany instead of Firefox, it uses the same rendering engine as Fiefox (Gecko) but its alot lighter

You could also try Abiword and Gnumeric for wriing and spreadsheet tasks :)

Or seamonkey installed with the navigator only (I find this preferable to epiphany).

---

