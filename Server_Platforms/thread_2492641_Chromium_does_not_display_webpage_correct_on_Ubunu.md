---
title: "Chromium does not display webpage correct on Ubunut Server with X-Server(X11)"
date: 2023-11-18
forum: Server Platforms
---

### Post by gegyman on 2023-11-18
Hey ubuntu forum! :)

[FONT=Helvetica]I am running Ubuntu Server 22.04 with minimal X-Server to display a webpage in chromium on an external display connected by HDMI. As hardware i am using an MacMini from 2010. The webpage to display i am hosting myself on this device.[/FONT] [FONT=Helvetica]But chromium does not display the webpage correctly. It seems text, formatted as header is displayed wrong. They have spaces between chars and wrong color. (Should be white). When i access the webpage from any other computer, everything looks ok, regardless what browser i am using.[/FONT]
[FONT=Helvetica]I worked on this for a couple of hours but could not find what cause this issue. Hope someone can help me out. :)
[/FONT]
[FONT=Helvetica]I am doing an autologin for a user which calls a bashscript to launch chromium.[/FONT]
[FONT=Helvetica]This is the script:[/FONT]
[FONT=Helvetica]
[/FONT]

```
[FONT=Helvetica]#!/bin/sh[/FONT]
[FONT=Helvetica]xset -dpms     # disable DPMS (Energy Star) features.[/FONT]
[FONT=Helvetica]xset s off     # disable screen saver[/FONT]
[FONT=Helvetica]xset s noblank # don't blank the video device[/FONT]
[FONT=Helvetica]matchbox-window-manager -use_titlebar no &[/FONT]
[FONT=Helvetica]unclutter &    # hide X mouse cursor unless mouse activated[/FONT]
[FONT=Helvetica]chromium-browser --enable-gpu --start-maximized --noerrdialogs --disable-restore-session-state [http://192.168.1.50/internal](http://192.168.1.50/internal)[/FONT]

[FONT=Helvetica]
[/FONT]
```
[FONT=Helvetica]Here are photos, showing the issue:[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Should be like this:[/FONT]
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293079&stc=1[/IMG]

Current display style
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293080&stc=1[/IMG]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]
[/FONT]

---

### Post by MAFoElffen on 2023-11-19
> **gegyman said:**
> Hey ubuntu forum! :)

[FONT=Helvetica]I am running Ubuntu Server 22.04 with minimal X-Server to display a webpage in chromium on an external display connected by HDMI. As hardware i am using an Mac Mini from 2010. The webpage to display i am hosting myself on this device.[/FONT] [FONT=Helvetica]But chromium does not display the webpage correctly. It seems text, formatted as header is displayed wrong. They have spaces between chars and wrong color. (Should be white). When i access the webpage from any other computer, everything looks ok, regardless what browser i am using.[/FONT]
[FONT=Helvetica]I worked on this for a couple of hours but could not find what cause this issue. Hope someone can help me out. :)
[/FONT]
[FONT=Helvetica]I am doing an autologin for a user which calls a bashscript to launch chromium.[/FONT]
[FONT=Helvetica]
This is the script:[/FONT]
```
[FONT=Helvetica]#!/bin/sh[/FONT]
[FONT=Helvetica]xset -dpms     # disable DPMS (Energy Star) features.[/FONT]
[FONT=Helvetica]xset s off     # disable screen saver[/FONT]
[FONT=Helvetica]xset s noblank # don't blank the video device[/FONT]
[FONT=Helvetica]matchbox-window-manager -use_titlebar no &[/FONT]
[FONT=Helvetica]unclutter &    # hide X mouse cursor unless mouse activated[/FONT]
[FONT=Helvetica]chromium-browser --enable-gpu --start-maximized --noerrdialogs --disable-restore-session-state [http://192.168.1.50/internal](http://192.168.1.50/internal)[/FONT]

```
[FONT=Helvetica]Here are photos, showing the issue:[/FONT]
[FONT=Helvetica][/FONT]...

My first question would be what packages did you install as your "interpretation" of Minimal X? And what additional packages did Chromium pull in ass dependencies? Because, well, I've been doing XServer on Unix since 21988, so my interpretation of Minimal X may varies from yours. Back in 2012, I started DEV on a Rescue LiveCD that was mainly console base, wiht on on-demand minimal X desktop (OpenBox).

Next, why Matchbox Windows Manager? That was meant for embedded systems with very low resolutions.

I, as a preliminary best guess, before getting any answers from you yet, my guesstimate would be  a combination of the limited capabilities of MatchBox Windows Manager, and very few fonts resources installed from a minimal X install.

---

### Post by gegyman on 2023-11-19
Hey. Thank you for your answer. I followed this instructions:
[https://reelyactive.github.io/diy/pi-kiosk/](https://reelyactive.github.io/diy/pi-kiosk/)
It's for raspberry pi but in most case it should work for my situation too. 
So i guess i should use another window manager. What would you suggest?
Many thanks.

---

### Post by MAFoElffen on 2023-11-19
For Minimal X, I still use OpenBox. Still well supported and very lightweight. I have a friend who prefers FWM for his. 

There is also LXQT, which is the same as Lubuntu... But if you are trying to stay minimal, I would do via
```

sudo apt -no-install-recommends install lxqt-core

```
That way, it doesn't pull in the applications, and you can pick and choose what you want to add to it.

---

### Post by gegyman on 2023-11-23
I switched now to openbox but the result is the same. Chromium does not display the page correct on the display. 
I got this worked half a year ago on the same hardware but i don't now the "trick" i did for getting this right.


On any other devices i am accessing the webbage i am getting the correct restult... even if i use chromium.

---

### Post by MAFoElffen on 2023-11-23
Please post the results of
```

xrandr -q
sudo lshw -C video

```

---

### Post by gegyman on 2023-11-23
xranr is not found as command. I guess you mean xrandr.

Ouput of xrandr
```
Can't open display
```

Output of [COLOR=#000000][FONT=&amp]sudo lshw -C video

[/FONT][/COLOR]```
*-display
       description: VGA compatible controller
       product: MCP89 [GeForce 320M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: /dev/fb0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1920,1080
       resources: irq:28 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:1000(size=128) memory:d3000000-d301ffff

```

---

### Post by gegyman on 2023-11-23
I have new informations for this topic:

I now switched to google chrome and it works. The page is displayed as it should be.  So it looks like, chromium needs a special flag to display correctly or has a bug in version 119.0.6045.159 snap

---

### Post by MAFoElffen on 2023-11-23
I think you might be using Wayland. Confirm by this.
```

printenv XDG_SESSION_TYPE

```
Try using X11 when you log in. That way you will be using "xserver-xorg-video-nouveau" as the graphics driver.

Since it is a minimal X install, ensure that driver is installed.

---

### Post by gegyman on 2023-11-23
Output is:
```
tty
```

Hmm... maybe google-chrome installation did install the driver now?
As it now works i will stay at chrome now.

---

### Post by MAFoElffen on 2023-11-23
I see that now... LOL. I'm happy that that is working for you now.

Please use the 'Thread Tools' link in the upper right of the page to mark your thread as 'Solved', so that others may find what worked for you.

---

### Post by gegyman on 2023-11-24
Thank you very much for your help! :)

---

