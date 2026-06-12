---
title: "Howto: Using Compton for tear-free compositing on XFCE or LXDE"
date: 2013-05-12
forum: Tutorials
---

### Post by screaminj3sus on 2013-05-12
I've always grappled with one major issues when using lightweight DE's like XFCE or LXDE: Video tearing. For me there is nothing more annoying then seeing tearing when watching video in my local video player or in flash player, and seeing ugly tearing when scrolling in firefox. XFCE's built-in xrender based compositor does nothing but exacerbate the issue, and the intel driver's "TearFree" option performs rather poorly.

The obvious solution to this is using an opengl compositor. In the past I had been using compiz in XFCE, which worked but left a lot to be desired when it came to integrating with XFCE and general bugginess; and the last straw is that in 13.04 it seems rather unusable when used outside of unity (severe bugs such as unclickable window decorations), so I searched for another solution. I then found compton: [https://github.com/chjj/compton](https://github.com/chjj/compton). Compton is a very lightweight compositor that is based on xcompmgr (its a fork of xcompmgr-dana). Compton features a stable opengl backend and working vsync (It also has an xrender backend, but for the purpose of getting tear-free output the opengl backend is recommended). Compton is an excellent fit for XFCE or LXDE because it is very lightweight and it does not need to replace your window manager like compiz does, it purely provides compositing.

The first thing you will want to do is install compton. The compton maintainer has a ppa for compton here: [https://launchpad.net/~richardgv/+archive/compton](https://launchpad.net/~richardgv/+archive/compton). To add the ppa to your system and install compton, open the terminal and enter the following commands: **sudo apt-add-repository ppa:richardgv/compton** and **sudo apt-get update && sudo apt-get install compton**

Next you will want to create your compton config file. Save the file as "~/.compton.conf". Here is the config file I use, I've added a few detailed comments explaining the most important things:

```

backend = "glx";
paint-on-overlay = true;
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
vsync = "opengl-swc"; 

[B]# These are important. The first one enables the opengl backend. The last one is the vsync method. Depending on the driver you might need to use a different method.
# The other options are smaller performance tweaks that work well in most cases. 
# You can find the rest of the options here: https://github.com/chjj/compton/wiki/perf-guide, and here: https://github.com/chjj/compton/wiki/vsync-guide
[/B]

# Shadow
shadow = true;			# Enabled client-side shadows on windows.
no-dock-shadow = true;		# Avoid drawing shadows on dock/panel windows.
no-dnd-shadow = true;		# Don't draw shadows on DND windows.
clear-shadow = true;		# Zero the part of the shadow's mask behind the window (experimental).
shadow-radius = 7;		# The blur radius for shadows. (default 12)
shadow-offset-x = -7;		# The left offset for shadows. (default -15)
shadow-offset-y = -7;		# The top offset for shadows. (default -15)
shadow-exclude = [
 "! name~=''",
 "n:e:Notification",
 "n:e:Plank",
 "n:e:Docky",
 "g:e:Synapse",
 "g:e:Kupfer",
 "g:e:Conky",
 "n:w:*Firefox*",
 "n:w:*Chrome*",
 "n:w:*Chromium*",
 "class_g ?= 'Notify-osd'",
 "class_g ?= 'Cairo-dock'",
 "class_g ?= 'Xfce4-notifyd'",
 "class_g ?= 'Xfce4-power-manager'"
];

[B]# The shadow exclude options are helpful if you have shadows enabled. Due to the way compton draws its shadows, certain applications will have visual glitches 
# (most applications are fine, only apps that do weird things with xshapes or argb are affected). 
# This list includes all the affected apps I found in my testing. The "! name~=''" part excludes shadows on any "Unknown" windows, this prevents a visual glitch with the XFWM alt tab switcher.
[/B]
# Fading
fading = true; # Fade windows during opacity changes.
fade-delta = 4; # The time between steps in a fade in milliseconds. (default 10).
fade-in-step = 0.03; # Opacity change between steps while fading in. (default 0.028).
fade-out-step = 0.03; # Opacity change between steps while fading out. (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

detect-client-opacity = true; [B]# This prevents opacity being ignored for some apps. For example without this enabled my xfce4-notifyd is 100% opacity no matter what.
[/B]
# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};

```

Now you are ready to set compton to start automatically upon login.

**For XFCE/xubuntu:**

Open the XFCE settings manager: settings manager > session and startup > application autostart > add and add **compton -b**. Now compton will start automatically when you login.

**For LXDE/lubuntu: **

edit this file: **~/.config/lxsession/Lubuntu/autostart**. You can just create the file if it does not exist: ```
mkdir -p ~/.config/lxsession/Lubuntu/
touch ~/.config/lxsession/Lubuntu/autostart
``` If you want to enable compton globally (for every user on the system), you can edit: /etc/xdg/lxsession/Lubuntu/autostart. Once the file is open in your text editor just add your startup command to it with an @ symbol in front of it, for example: **@compton -b &**

(I don't use lubuntu/lxde so I haven't tested this myself, I've put this together from these sources: [http://lubuntublog.blogspot.com/p/compton.html](http://lubuntublog.blogspot.com/p/compton.html), [https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_I_can_autostart_a_program_when_logging_into_Desktop](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_I_can_autostart_a_program_when_logging_into_Desktop))

**EDIT: Based on feedback I have moved all switches into the config file and simplified the guide.**

---

### Post by vociferous666 on 2013-05-16
works great on Ubuntu 12.04 with Lubuntu-Desktop installed!

even makes the scrolling in firefox a little faster.

---

### Post by hg088 on 2013-06-08
Works perfectly with amd radeon 6870 running xubuntu 13.04

Thank you so much i really didn't wanted to use compiz to address the tearing issue, this is so much better.

---

### Post by Baneblade on 2013-06-09
Worked perfectly on Xubuntu 13.04. with Nvidia 310 drivers. I used your Intel command and it seems to be just fine.

Many thanks! The tearing was slowly driving me mad :p

---

### Post by ushpiy on 2013-06-10
Worked for me on Ubuntu 12.04 too, thanks a lot!

---

### Post by Emblem Parade on 2013-06-11
If you're using DockbarX, including the DockbarX plugin for Xfce, then you might also want to add this to "shadow-exclude" in your config:

```
"n:w:*dockbarx*"
```

Also, you really don't need all those arguments in the compton command line, you can include all them in your config except for "-b". You don't even need to specify the config file location, because it's already in the default location. In summary, you just need this command line to start Compton:

```
compton -b
```

And this config (saved as "~/.compton.conf"):

```
backend = "glx";
paint-on-overlay = true;
glx-no-stencil = true;
vsync = "opengl-swc";

# Shadow
shadow = true; # Enabled client-side shadows on windows.
no-dock-shadow = true; # Avoid drawing shadows on dock/panel windows.
no-dnd-shadow = true; # Don't draw shadows on DND windows.
clear-shadow = true; # Zero the part of the shadow's mask behind the window (experimental).
shadow-radius = 7; # The blur radius for shadows. (default 12)
shadow-offset-x = -7; # The left offset for shadows. (default -15)
shadow-offset-y = -7; # The top offset for shadows. (default -15)
shadow-exclude = [
  "n:e:Notification",
  "n:e:Docky",
  "g:e:Synapse",
  "g:e:Conky",
  "n:w:*Firefox*",
  "n:w:*Chromium*",
  "n:w:*dockbarx*",
  "class_g ?= 'Cairo-dock'",
  "class_g ?= 'Xfce4-notifyd'",
  "class_g ?= 'Xfce4-power-manager'"
];

# Opacity
detect-client-opacity = true;

# Fading
fading = true; # Fade windows during opacity changes.
fade-delta = 4; # The time between steps in a fade in milliseconds. (default 10).
fade-in-step = 0.03; # Opacity change between steps while fading in. (default 0.028).
fade-out-step = 0.03; # Opacity change between steps while fading out. (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};

```

---

### Post by jigsaw! on 2013-10-30
Compton is of course is better than compiz.

But with ```
backend = "glx";
``` I have pretty bad performance on my Nvidia Geforce GT 630. So I use ```
backend = "xrender";
``` Unfortunately I cant fix tearing in video with xrender backend. Do you know how to fix that?

Thanks a lot.

---

### Post by CFWhitman on 2013-11-18
> **jigsaw! said:**
> Compton is of course is better than compiz.

But with ```
backend = "glx";
``` I have pretty bad performance on my Nvidia Geforce GT 630. So I use ```
backend = "xrender";
``` Unfortunately I cant fix tearing in video with xrender backend. Do you know how to fix that?

Thanks a lot.

You shouldn't have a problem with performance with that card unless you are using the nouveau drivers rather than the Nvidia ones.  Are you using the Nvidia supplied proprietary drivers?  There are several glx / opengl related options in compton that could make a difference, especially if you are using nouveau drivers.

---

### Post by jschroed on 2013-12-31
This might no longer be an issue but I found that compton worked great to fix video tearning when I was running [Netflix in XBMC]("http://forum.xbmc.org/showthread.php?tid=154888&pid=1586557#pid1586557"). Here's what I did:

Install netflix-desktop
```

sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update && sudo apt-get install netflix-desktop

```

Install compton
```

sudo apt-add-repository ppa:richardgv/compton
sudo apt-get update && sudo apt-get install compton

```

Download the addon [here]("http://www.qfpost.com/file/d?g=nk0617Cr6").

From XBMC, choose install addon from zip file and open the netflix addon downloaded in the previous step.

Change the scripts to be executable. (May no longer be necessary.)
```

chmod +x ~/.xbmc/addons/script.netflix_install/run*.sh

```

Change run.sh to use compton instead.
```

gedit ~/.xbmc/addons/script.netflix_install/run.sh

```

Change the contents from:
```

#!/bin/bash
openbox & netflix-desktop "$1"
kill %1

```

To:
```

#!/bin/bash
openbox &
compton -b 
netflix-desktop "$1"
kill %1

```

Note: you can also change run2.sh to use compton.

---

### Post by Niccola on 2014-02-11
How much heavy lxde turns after installing Compton?

---

### Post by donjoe0 on 2014-03-05
Brilliant! Finally no more video tearing!

I'm on a Xubuntu 12.04 with Nvidia driver v311. Tested with VLC, MPlayer and YouTube (old Flash v11.2.202) - only minor glitches left in YouTube playback, possibly because of streaming jitter rather than vsync problems.

---

### Post by dannyboy79 on 2014-05-31
this did not resolve my screen tearing I am getting in minecraft. I am running Xubuntu 14.04 with Nvidia driver 337.25 with an EVGA GTX 760 SC. I think i've now tried every possible solution i came across on the web. Anyone else have any other ideas to solve this tearing i'm getting?

UPDATE: i hadn't disabled Xubuntu's built in compositing in order to get Compton to work, also the -b switch results in an error so to run compton within Xubuntu 14.04 64bit I just issue compton and that's it. This resolved my tearing I was getting in Minecraft. THANKS

---

### Post by Razema on 2014-06-10
[FONT=arial]Using compton with your configuration did fix all of my tearing problems, but it also caused a LOT of lag when dragging windows. I have an Nvidia GTX 570 with 2.5G of vram, so moving 2D windows around the screen should not have any noticable performance issues. This led me to believe that it was a problem with the settings. So, I messed with the compton config a bit and found a different set of options that worked much better for me:

```

[FONT=courier new]#--------------------------------
#-------Backend Settings:--------
#--------------------------------
backend = "glx";                 # Use GLX backend for rendering
vsync = "opengl";                # Use OpenGL to implement vsync
glx-swap-method = 3;             # Use a triple-buffer
paint-on-overlay = true;         # Improves performance (usually) and reduces flickering
glx-no-stencil = true;           # Improves performance
glx-no-rebind-pixmap = true;     # Improves performance with rapid window changes, might not work with some drivers


#--------------------------------
#--------Shadow Settings:--------
#--------------------------------
shadow = true;                   # Enable drawing shadows on windows
shadow-radius = 8;               # The blur radius for shadows
shadow-offset-x = -8;            # The horizontal offset for shadows
shadow-offset-y = -8;            # The vertical offset for shadows
clear-shadow = true;             # Zero the part of the shadow's mask behind the window, may break some applications
no-dock-shadow = true;           # Do not draw shadows on docks/panels
no-dnd-shadow = true;            # Do not draw shadows on DND windows
shadow-exclude = [               # Do not draw shadows on these specific applications:
   #"! name~=''",
    "n:e:Notification",
    "n:e:Plank",
    "n:e:Docky",
    "g:e:Synapse",
    "g:e:Kupfer",
    "g:e:Conky",
    "n:w:*dockbarx*",
   #"n:w:*Firefox*",
   #"n:w:*Chrome*",
   #"n:w:*Chromium*",
    "class_g ?= 'Notify-osd'",
    "class_g ?= 'Cairo-dock'",
    "class_g ?= 'Xfce4-notifyd'",
    "class_g ?= 'Xfce4-power-manager'"
];


#--------------------------------
#--------Fading Settings:--------
#--------------------------------
fading = true;                   # Enable fading windows during opacity changes
fade-delta = 4;                  # The time between steps in a fade in milliseconds
fade-in-step = 0.03;             # The opacity change between steps while fading in
fade-out-step = 0.03;            # The opacity change between steps while fading out
detect-client-opacity = true;    # Prevent opacity from being ignored for some applications


#--------------------------------
#--------Window Settings:--------
#--------------------------------
wintypes:                        # Change behavior for these specific types of windows:
{
    tooltip = { fade = true; shadow = false; };
};
[/FONT]

```[/FONT]
Although this configuration works very well for me, it might not work well for everyone. Some of the options, such as triple buffering, can dramatically decrease performance on graphics cards without enough vram. Also, I am using the proprietary nvidia driver v331.79. These options might not work well (or at all) with nouveau drivers.

---

### Post by stkeg on 2014-08-04
i've notced that when i leave my computer on for a couple of days (maybe 2-3) xorg stays at a high cpu and then UI interaction gets sluggish (slow to move windows, etc)


i kill and then restart compton then everything is ok again.


anyone else have this issue and/or know what's happening?

---

### Post by Pablo_San_Martn on 2015-01-02
Is there a way of putting exceptions to the "inactive-dim" function? I really like that feature but I don't like the fact that it also affects conky.

---

### Post by pseudosynaptic on 2015-08-11
I don't mean to resurrect an old thread, but this is still one of the top Google results for using compton with Ubuntu.

I've packaged the latest version of compton, along with an unmerged pull request of mine that fixes a resource leak, for 15.04, 14.04LTS, and 12.04LTS.  My fork of compton is at [https://github.com/kelleyk/compton](https://github.com/kelleyk/compton) and the PPA is at [https://launchpad.net/~kelleyk/+archive/ubuntu/compton](https://launchpad.net/~kelleyk/+archive/ubuntu/compton).

Hope this helps someone!

---

### Post by pseudosynaptic on 2015-08-11
> **stkeg said:**
> i've notced that when i leave my computer on for a couple of days (maybe 2-3) xorg stays at a high cpu and then UI interaction gets sluggish (slow to move windows, etc)


i kill and then restart compton then everything is ok again.


anyone else have this issue and/or know what's happening?

This is the resource leak that I mentioned in my previous post.  The relevant pull request ([https://github.com/chjj/compton/pull/285](https://github.com/chjj/compton/pull/285)) describes exactly what the problem was and how I tracked it down.  It's fixed in my fork of the repository and in my PPA.

---

### Post by vasa1 on 2015-08-11
> **pseudosynaptic said:**
> I don't mean to resurrect an old thread, ...
Not an issue, IMO, because the last post was from Jan 15 this year :)

And this is certainly a thread worth keeping open!

---

### Post by vasa1 on 2015-08-11
> **Pablo_San_Martn said:**
> Is there a way of putting exceptions to the "inactive-dim" function? I really like that feature but I don't like the fact that it also affects conky.
It may also be worth asking this as a separate conky question because conky experts could look at your conky code and show you how to get what you want without fiddling with your compton settings. 

I'm not aware of compton affecting my conky which is a brief text-only one-liner.

Edit:
Have you looked at [https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions?](https://github.com/chjj/compton/blob/master/man/compton.1.asciidoc#format-of-conditions?) That's quite informative (or just type compton -h in your terminal for information specific to your version of compton).

---

### Post by fkervin on 2015-11-24
Hi all,

I've been using compton with xubuntu 14.04 for long time with a great result, but now I've a new install with a freshly installed Xubuntu 15.10 and have notice some problems.

Some applications (some games such as torcs) gets blocked when run in fullscreen. I've solve this problem using an script that makes "**killall compton**" before opening the application and "**compton -b**" when closing the app.

The bigger problem comes with Google Chrome, it plays videos correctly in "normal" (windowed) mode, but when I go fullscreen video gets frozen althought audio continues. this problem comes with youtube and other webs that plays videos. I've research a bit and youtube uses by default HTML5, so I've move it to flash using a Chrome addon, result? problem is exacty the same. I suppose it's the same problem that comes with those other applications and has nothing to do with html5 or flash. 

Of course, if I disable compton then videos works great in fullscreen mode and... here comes the most insteresting thing, I've no tearing!. I mean:

If I disable compton there is tearing on videos played in "non-full-screen" but when go to fullscreen tearing dissapears. It makes me think that Chrome includes now some method to remove tearing in full screen. This should be something good, but it seems to interfere with Compton, so it makes video unplayable in fullscreen.

I've also try to disable hardware acceleration in chrome, for doing this go to the settings and [do this. ]("http://i.stack.imgur.com/Faj5M.png")If I do this then video gets no frozen when go to fullscreen, but then I've a huge tearing even with compton enabled. So, this solution is not ok :(

I guess the solution of this problem could be having some way to disable compton when Chrome plays video in fullscreen. How can I do this? I could disable compton when opening chrome and enable again when closing, but it's not desirable since I had no compton in any app (remember, we only wants compton to be disabled when playing a video in full-screen).

Is there any way to disable compton only with chrome and only when play fullscreen? I wonder if I could configure this in "~/.compton.conf".

Many thanks to everyone who reads this, I hope someone can help.

Regards

---

### Post by fkervin on 2015-12-01
Anybody has experience this problem?

Regards

---

### Post by fkervin on 2015-12-03
Hi All,

I'm unhappy to see there are no answer at all :(, I can't believe I'm the only one with this problem.

If it helps anyone, I've notice Chrome have problem playing some 1080p 60hz youtuve videos, even with compton disabled, so there could be some problem related to the latest stable version (47.0.2526.73 64 bits). The problem I'm talking about is not complete freeze of image but stops of 0,5 - 1 sec every certain time. This is one of the videos that shows this behaviour:

[https://www.youtube.com/watch?v=JBM_gqOeUXY](https://www.youtube.com/watch?v=JBM_gqOeUXY)

In the same machine (Intel N3150 with 4GB RAM) using firefox everything works great.

If I disable compton I still have tearing, so it's not an option.

Regards

---

### Post by Vertux on 2016-03-17
Hi there,

I've been playing aroud a little with compton some time ago.

Here is my .compton.conf:

```
##-----------------------------------------------------##
##      Fichier de configuration compton by Vertux     ##
##  Édité le samedi 12 mars 2016, 17:46:26 (UTC+0400)  ##
##-----------------------------------------------------##

# You can find the rest of the options here: https://github.com/chjj/compton/wiki/perf-guide, and here: https://github.com/chjj/compton/wiki/vsync-guide

# Backend to use: "xrender" or "glx".
# GLX backend is typically much faster but depends on a sane driver.
backend = "glx";

vsync = "opengl-swc";
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
paint-on-overlay = true;
glx-swap-method = "undefined";
detect-client-opacity = true;
mark-wmwin-focused = true;
mark-ovredir-focused = true;
use-ewmh-active-win = true;

# Enabled client-side shadows on windows.
shadow = true;
# Don't draw shadows on DND windows.
no-dnd-shadow = true;
# Avoid drawing shadows on dock/panel windows.
no-dock-shadow = true;
# Zero the part of the shadow's mask behind the window. Fix some weirdness with ARGB windows.
clear-shadow = true;
# The blur radius for shadows. (default 12)
shadow-radius = 8;
# The left offset for shadows. (default -15)
shadow-offset-x = -8;
# The top offset for shadows. (default -15)
shadow-offset-y = -8;
# The translucency for shadows. (default .75)
shadow-opacity = 0.5;

# The shadow exclude options are helpful if you have shadows enabled. Due to the way compton draws its shadows, certain applications will have visual glitches
# (most applications are fine, only apps that do weird things with xshapes or argb are affected).
# This list includes all the affected apps I found in my testing. The "! name~=''" part excludes shadows on any "Unknown" windows, this prevents a visual glitch with the XFWM alt tab switcher.
shadow-exclude = [
    "name = 'Notification'",
    "name = 'xfce4-notifyd'",
    "name = 'medit'",
    "name *= 'VLC'",
    "name *= 'compton'",
    "class_g ?= 'gksudo'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g ?= 'Xfce4-notifyd'"
];

# Fade windows during opacity changes.
fading = true;
# The time between steps in a fade in milliseconds. (default 10).
fade-delta = 5;
# Opacity change between steps while fading in. (default 0.028).
fade-in-step = 0.11;
# Opacity change between steps while fading out. (default 0.03).
fade-out-step = 0.19;
fade-exclude = [
   "name = 'Notification'",
   "name = 'xfce4-notifyd'",
   "name *= 'compton'",
   "class_g = 'Conky'",
   "class_g ?= 'Notify-osd'",
   "class_g ?= 'Xfce4-notifyd'"
];

# Fade windows in/out when opening/closing
# no-fading-openclose = true;

# Window type settings
wintypes:
{
  tooltip = { fade = false; shadow = false; };
};
```

It worked nice, no tearing at all, with no high CPU consumption, and RAM usage from 20 to 70 Mo.
Some (very rare) apps were behaving weird (especially medit that I use a lot), but nothing severe.

Then came XFCE 4.12 with the possibility to enable Vsync.
95% of videos, Full-screen games are now tearless.

I then left Compton.

Cheers.

---

