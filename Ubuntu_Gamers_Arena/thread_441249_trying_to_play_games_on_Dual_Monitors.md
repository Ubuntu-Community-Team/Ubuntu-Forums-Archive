---
title: "trying to play games on Dual Monitors"
date: 2007-05-12
forum: Ubuntu Gamers Arena
---

### Post by Silent_Hunter on 2007-05-12
I have a Nvidia 7600 GT dual dvi graphics card and two monitors running at 1680x1050 resolution each.  I am using Ubuntu 7.04 32bit desktop edition.   With my dual monitors using TwinView, it tricks my monitors to thinking they are one and runs at 3360x1050 resolution for the both of them combined.  This is a great set up for doing everything but GAMES!  I would like to use just one screen 1680x1050 for full screen and not touch the second one.   I have not be able to figure out how to do that.   I am forced right now to disable my second monitor to be able to play a game.    Has anyone each been able to figure out how to make one monitor full screen but not have to shut off the second one?

---

### Post by autocrosser on 2007-05-12
Well-I shut one screen off. I have not found a way yet. I don't know if it can be done with the current version of Xorg--I'll post to xorg-request list later today & see what they think about it...If you want to inquire youself, the list is at:

[http://lists.freedesktop.org/mailman/listinfo/xorg](http://lists.freedesktop.org/mailman/listinfo/xorg)

I get the list in digest form--interesting reading......

---

### Post by jondecker76 on 2007-05-12
You have to set up meta modes..  The NVidia site has all the information you need to do this, but off the top of my head, set up meta modes for for all of your dual screen resolutions, then set up meta modes setting the resolution of one screen to null..

Oh - just found another post I remember seeing on this same topic. Please see:
[http://ubuntuforums.org/showthread.php?t=416249]("http://ubuntuforums.org/showthread.php?t=416249")

I followed this, and added meta modes for 1024x768,null , 800x600,Null, and 640x480,null and now for each game i can select whether it runs dual screen or single screen, and at which resolution. Once you get it set up, its quite slick

---

### Post by jondecker76 on 2007-05-12
Here is a copy and paste of my metamodes from my xorg.conf file

```
Option         "metamodes" "CRT-0: 1152x864 +0+0, CRT-1: 1152x864 +1152+0; CRT-0: 1152x864 +0+0, CRT-1: null +1152+0; CRT-0: 1024x768 +0+0, CRT-1: 1024x768 +1024+0; CRT-0: 1024x768 +0+0, CRT-1: null +1024+0; CRT-0: 800x600 +0+0, CRT-1: 800x600 +800+0; CRT-0: 800x600 +0+0, CRT-1: null +800+0; CRT-0: 640x480 +0+0, CRT-1: 640x480 +640+0; CRT-0: 640x480 +0+0, CRT-1: null +640+0"
```

---

### Post by autocrosser on 2007-05-12
Jon--I think that he is looking for a way to use one screen to play a game & use the other one for other uses (at least that is the way I read it). The metamode "null" shuts off one screen. I have posted to xorg-developers-list about the possibilty to have one screen for games (in full-screen mode) & the second screen with a webbrowser-etc open (my wish----)

---

### Post by jondecker76 on 2007-05-13
Aaah - i see. Thats not really possible at the moment

However, using the metamodes as indicated above is the best solution at this time. Besides, who really wants to surf the web while playing a game anyways??

---

### Post by autocrosser on 2007-05-13
Let's say you want a IM window open, or are keeping a eye open on something--I could think of several others-----It's possible that the new Xorg is going to help that along--

---

### Post by Clay_Banger on 2007-05-13
yeah, i would love a feature like that! enables you to use one screen as a fullscreen app, ie a game, and the other ur desktop.. sounds great. but will it happen? can windows do it?

---

### Post by autocrosser on 2007-05-14
Cross fingers--Xorg 7.3 is coming in Gutsy----

---

### Post by handy on 2007-05-25
I use 2 computers sometimes whilst playing Guild Wars; I can have the [***_Guild Wiki_***]("http://gw.gamewikis.org/wiki/Main_Page") open, & refer to a map, or character build information or whatever I would like to reference.

So, its not hard to imagine that being able to use a screen to refer to the web could be incredibly useful & far more cost effective & energy efficient than using 2 computers.

---

### Post by Soybean on 2007-05-25
I'm pretty sure this can be done with nested X servers. Not that I've done it, but I've seen a few different posts about people nesting X servers for various reasons, and this seems similar.

From my limited understanding, I believe what you want to do here is set it up so that when you start the game, it launches in a single-screen X server that's nested inside your regular X server. Then your other screen would still be usable, either by your regular X server, or a second single-screen nested server. I believe the synaptic package "xnest" is used for this. Somehow. ;) This trick can also be used to help Beryl coexist with full-screen 3d-accelerated programs, which is mainly where I've heard of people using it.

I realize I'm being really vague here, and my details might be slightly off, but my main point is that I'm pretty sure it IS possible, even though I don't personally really know how. :lol:

---

### Post by djRobbieF on 2007-06-08
How strange that I am experiencing the EXACT OPPOSITE problem:  My games ONLY display on one monitor in Twinview; but I *want* them to display on both, spanned out to make me feel like I've got that "extreme peripheral view"  :)

I'm no noob when it comes to linux or even xorg.conf; but this is my first time ever setting up a dual-monitor setup in Linux; so to this, I need assistance  ;)

Here's my xorg.conf.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050 +1680+0, DFP-1: nvidia-auto-select +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

So at the moment, when I run Enemy Territory, my one monitor turns off, and the second monitor has the game full-screen.  However, I want both monitors to REMAIN ON and have the game "widescreen" over both displays.

Any help anyone can provide would be hugely appreciated; and hopefully my xorg.conf might also give you ideas how to fix the first question in this thread, because it looks to me that what I have is what they want, and vice-versa.

Thanks!

---

### Post by burt_57 on 2007-07-05
In windows I can have my 2 monitors working , no problem.
But in Ubuntu Ultimate , no way man.
It wont't even recognise the second screen.
Any suggestion.
Using NVIDIA Express and 2 Phillips 170 S monitors.

---

### Post by jaygo on 2007-10-28
I believe I've found the problem affecting everyone here. While all the howto's tell you how to config xorg.conf, they generally don't mention that your desktop environment also maintains some screen settings that will override / limit all your hard work in xorg.conf. 

So instructions for the two camps:

[SIZE="6"]_To play fullscreen games on both monitors:_[/SIZE]
[LIST=1]
[*]open your xorg.conf as root
[*]under your screen, you have an Option "metamodes" line. Simply remove any single-monitor metamodes. These would look like "CRT: 1600x1200, NULL" or "DFP: 1600x1200" (notice no reference to a 2nd monitor). When you're done, your entire list of metamodes should be dual-monitor modes. Note: you can also just have one metamode, such as "CRT-1: 1600x1200, DFP-0: 1600x1200 +1600+0". This effectively disallows X from using any single monitor modes.
[*]save. (obviously)
[*]log out, RESTART X by hitting CTRL + ALT + BACKSPACE or by choosing "restart x" from the menu
[*]log in, and you're done.
[/LIST]

[SIZE="6"]_To Automatically switch to single-monitor for games[/SIZE] (but keep multiple monitors for everything else):_

Luckily, this seems to be the default behavior (at least for nvidia drivers) so we only need to keep the DE from interfering. In my experience, the desktop will only interfere if you've adjusted the display settings there. If left as default, xorg will rule the castle. In other words, You should only need the following steps if you're stuck playing games across all screens.

**_In KDE_**
[LIST=1]
[*]Find & open a file "displayconfigrc" in /home/(username)/.kde/share/config/
[*]remove the height & width lines
[*]save
[*]log out, RESTART X by hitting CTRL + ALT + BACKSPACE or by choosing "restart x" from the menu
[*]log in, and you're done.
[/LIST]

**_In Gnome:_**
I did this a while back so as best as I recall ...
[LIST=1]
[*]Open up the editor for your (desktop?) config. I forget exactly what Gnome calls this so please post if you find out. The easy way I used to get into it using Ubuntu 7.04 was to right-click on the gnome menu in the lower left & choose 1 of the 2 references to " ... config ...". Sorry I can't remember which one. You can also get to this editor from the main menu ... I think it's called "System Config".
[*]Find an entry called 'virtual desktop' or 'virtual screen' ... something like that.
[*]Remove that entry. If it's not in there, then it's not causing any problems and all your problems should be in your xorg.conf setup.
[*]log out, RESTART X by hitting CTRL + ALT + BACKSPACE or by choosing "restart x" from the menu
[*]log in, and you're done.[/LIST]

Note: as mentioned in some posts above, if you want to play fullscreen games on one monitor & have your desktop apps running on another, you'll want to setup multiple X screens. See [https://help.ubuntu.com/community/XineramaHowTo]("https://help.ubuntu.com/community/XineramaHowTo")

Also, if anyone can tell me how to make an official howto here or suggest where I should report bugs in launchpad, please let me know via PM.

---

### Post by lbelloq on 2007-10-29
> **Clay_Banger said:**
> yeah, i would love a feature like that! enables you to use one screen as a fullscreen app, ie a game, and the other ur desktop.. sounds great. but will it happen? can windows do it?
Yes it can. You can have a video playing fullscreen in one monitor and your regular Windows desktop in the other. Its' neat and useful, for example, for having your laptop displaying a PPT fullscreen in the projector output and having some guide notes in the built-in LCD screen or watching my favorite anime ep while I have a open eye in the other monitor for forums, IM and such.

---

