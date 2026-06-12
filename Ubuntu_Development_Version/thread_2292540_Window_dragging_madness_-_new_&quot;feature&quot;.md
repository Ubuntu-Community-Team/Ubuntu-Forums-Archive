---
title: "Window dragging madness - new &quot;feature&quot;?"
date: 2015-08-28
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-08-28
I really dunno what I've accidentally (?) changed in my LXDE, but it seems to be intentional. 

Since a few recent updates (to name Firefox 40 as the major application where this happens), I've been noticing a strange and different way of moving of windows.

The windows feel like "buttered" or something, or sliding on something like grease. (No I'm not drunk. :P) 

When my terminal window is in normal "working size", this is still bearable. But once I expand it to 80% of the screen size, it will become the same as in Firefox.
That MUST be something programmed in recently, as I've never witnessed that in either Trusty, Utopic or Vivid.
Gah, this is annoying the hell out of me. I want to turn this off again...provided that I can. :P

---

### Post by v3.xx on 2015-08-28
I do have FF40 installed and working, but I also have FF ESR just because its nice to have something that just works.

[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)

---

### Post by vasa1 on 2015-08-29
> **syntaxerror74 said:**
> I really dunno what I've accidentally (?) changed in my LXDE, but it seems to be intentional. 
...
I'm not on the dev version and so may be incorrect, but you should have *~/.config/openbox/lubuntu-rc.xml*. Have you made any modifications to that file? When was it last modified? I think that any changes to how windows appear are determined by this file's content.

Other avenues for help: 
[https://help.ubuntu.com/community/Lubuntu/Support](https://help.ubuntu.com/community/Lubuntu/Support)
[https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)
webchat.freenode.net/?channels=lubuntu
[https://www.facebook.com/Lubuntu.Official.Page](https://www.facebook.com/Lubuntu.Official.Page)

Edit: I posted on the facebook page pointing to this thread. BTW, you need to be approved by a mod to join up there.

---

### Post by syntaxerror74 on 2015-08-29
And on its part, that would require me to have a FB account.
Dismissed - Maybe in another life. :P

---

### Post by ventrical on 2015-08-29
I have an original upgraded install (meaning virgin install - not  manually configured in any way) on this machine:

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.1.0-3-generic x86_64 (64 bit gcc: 4.9.3)
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 15.10 wily
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12398
           clock speeds: max: 3100 MHz 1: 2097 MHz 2: 2263 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.2 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 10.6.3 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.1.0-3-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (6.8% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 54G used: 3.9G (8%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 141 Uptime: 13 min Memory: 422.0/3814.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.2.1
           Client: Shell (bash 4.3.391) inxi: 2.2.16 
ventrical@ventrical-MS-7850:~$ 

```

and do not see any of the behaviour you are describing. The windows do drag a lot smoother. There is less choppy  vertical refresh on a moving window which has always been a ambiance problem with lubuntu. I'll keep my eye on my installs.

What type video card are you using?

Regards..

edit:

I'll try with nVidia card and see whats up..

---

### Post by ventrical on 2015-08-29
Nope .. do not see it on nVida either.

---

### Post by syntaxerror74 on 2015-08-29
OK, thanks for bearing with me, ventrical - I'll try to explain it a little better.

Moving a window will now (I can't seem to remember that being like this in the old days) change the mouse cursor into a whole hand. If you move a window with the hand (RMB depressed) you will surely notice some kind of "momentum" applied on the windows.
If this was a video game, I would say that control is less direct. 

Old way would be that the mouse cursor *STAY* fixed on the title bar when the window is moved.
But now the "hand" will also appear OUTSIDE a window, for instance, when you move it in upward direction.
This confuses me entirely, and I'd like to turn this off again...Once I know what setting is causing this behavior, that is.

WAIT A SEC...
There must be some kind of animation mode set here. Because if the hand is 50 pixels ABOVE the window title bar, it will cause the window to be moved exactly to this position; however, not suddenly, but bit by bit, as if driven by a "motor."

---

### Post by ventrical on 2015-08-30
Ok.. I remember now. Grahammechanical had described this behaviour about three cycles ago (with saucy).. but it was with unity desktop and we called it the 'bungee effect". I do not recall it  happening on lubuntu and I think it was a ccsm problem. and/or could have been due to a nVidia proprietary driver prob.

Regards..

---

### Post by syntaxerror74 on 2015-08-30
> **ventrical said:**
> Ok.. I remember now. Grahammechanical had described this behaviour about three cycles ago (with saucy)..
That proves I'm NOT making this up...

> but it was with unity desktop and we called it the 'bungee effect". I do not recall it  happening on lubuntu and I think it was a ccsm problem. and/or could have been due to a nVidia proprietary driver prob.

Ah, that might be it. I had INDEED (test-)installed the NV prop driver (since nouveau worked so awfully) but had to remove it again because it has also shown in this forum that using the *latest *driver available from NVidia themselves with a 3.x kernel is an unwise thought (whilst the 4.x RC ones are *about *to work pretty well with it; yet I prefer to stick with the 3.x branch for the time being)

---

### Post by ventrical on 2015-08-30
Just seen now that >preferences>customize look and feel: does not work when I click on the dialog menu.

Major bug?

---

### Post by ventrical on 2015-08-30
Ok.. apport wanted to report a bug on 'lxappearance' after it crashed .. so I tried to follow through and the bug report just vanished.

Regards..

---

### Post by syntaxerror74 on 2015-09-01
WFM ... please do indeed go looking for bug reports regarding lxappearance for that (there was an utter plethora of reports, even if only looking in dev version forum alone). Note that  "Customize Look&Feel" is just a renamed *lxappearance* which is called under the hood.

---

