---
title: "xubuntu + esxi + xorg problems"
date: 2016-02-17
forum: Virtualisation
---

### Post by JORGE_FERNANDEZ on 2016-02-17
Hi community, after I can´t remember the number of attemps to get this working, looking at google at posts in this forum, in another forums finally I need some help.

My problem: 

Im trying to setting into an esxi box a xubuntu and a pair of windows 8.1.

I like a lot an open source desktop to personalize and for my day to day web programming so windowses are one for gaming (with a 390x passtrough) and the oder for autocad working (firepro passtrough). 

First I'm trying with an old NVIDIA 6200 LE before buying a EVGA GT 740 SC and I'm not able to configure xorg to get video from the physical screen.

 After reading a lot about xorg and its folder priorities I've made a 10-monitor.conf file into /usr/share/X11/xorg.conf.d/. I've got some neccesary values following a guide (HorizSync and VertRefresh values). I've got the modeline parameters with another guide. But I can get only a fantastic "out of range" on my screen even my parameters (I hope so) are good. 

I don't know what I'm doing bad. A little help would be appreciated. Thanks in advance.

---

### Post by MAFoElffen on 2016-02-17
Does this help? (ESXI 5.5)
[https://www.pugetsystems.com/labs/articles/Multi-headed-VMWare-Gaming-Setup-564/](https://www.pugetsystems.com/labs/articles/Multi-headed-VMWare-Gaming-Setup-564/)

Look about the middle of the blog at the screen shots...

On your xorg.conf file, with modesty, I'm told I'm the person to talk to about the Linux Graphics Layer, XServer, and proprietary High Resolution Graphics GPU's. If you need reference, go to the Graphics Resolution Sticky in my Sig line...

But... ESXi and Nvidia Geforce do not play well together: (at least not without[ nVidia Grid]("http://www.nvidia.com/object/vmware-trygrid.html"))
> 
The setup worked great and the article was very popular, but one limitation we found was that NVIDIA GeForce cards cannot be used as passthough devices in VMWare ESXI.


---

### Post by JORGE_FERNANDEZ on 2016-02-17
Yes I've read that thread but they are working with windows only and i am able to setup my windows machines.

 I'm using esxi because another solutions like kvm qemu and xen didn't worked for me (my video card and os).

I am able to passtrough the ancient 6200 (esxi lets me with no problem) and when i start the linux instalation i see the xubuntu's splash screen on my physical screen but no more apart from "out of range". Also i can install nvidia drivers on linux and the card is recognised. I supose video is working but with wrong parameters on xorg. I had problems in linux with a hd 6570 and esxi didnt start with a hd 6870 so thats te reason about using the 6200 le. Im very stuck with this.

---

### Post by MAFoElffen on 2016-02-18
Post your xorg conf file that you are working on and I'll take a look at it. And what is the model of the monitor it is connected to? (for modes of and syncs).

---

### Post by JORGE_FERNANDEZ on 2016-02-18
This is my testing environment:

First i'm trying with an LG 24EA53VQ here are their specs with its official frequency (not working) values on VGA port. (6200 LE has tv out dvi d and vga). Then i'am going to try with two monitor setup (benq fp937s) but is better to test with one to avoid more problems.

[http://www.lg.com/hk_en/monitors/lg-24EA53VQ/technical-specifications](http://www.lg.com/hk_en/monitors/lg-24EA53VQ/technical-specifications)

this is my testing xorg config

> 
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      1  "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "LG"
    ModelName    "24EA53"
    HorizSync    30.0 - 83.0
    VertRefresh  43.0 - 72.0
    Modeline     "1920x1080" 148.500 1920 2016 2056 2200 1080 1084 1089 1125 +hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
        #Option     "AccelMethod"            # <str>
    Identifier  "Card1"
    Driver      "nouveau"
    BusID       "PCI:11:0:0"
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


this file is copied following the next method

CTRL + ALT + F1 to go to console then stop lightdm service and then startx but no success, only out of range. Values horizsync vertrefresh in xorg conf file obtained with xubuntu booted on the physical machine without esxi following this guide

[http://www.blackmoreops.com/2014/08/29/fix-linux-display-issue-find-horizsync-vertrefresh-rates/](http://www.blackmoreops.com/2014/08/29/fix-linux-display-issue-find-horizsync-vertrefresh-rates/)

Modeline got with this in windows

[http://webcache.googleusercontent.com/search?q=cache:http://www.x.org/wiki/FAQVideoModes/&gws_rd=cr&ei=ggHFVpqbL4T4aq2woJAI](http://webcache.googleusercontent.com/search?q=cache:http://www.x.org/wiki/FAQVideoModes/&gws_rd=cr&ei=ggHFVpqbL4T4aq2woJAI)

If you need more info about my setup please tell me.

---

### Post by MAFoElffen on 2016-02-18
So the passthrough  for the guest, the pci address of the GPU for the guest is blacklisted. So that the host does not use it while booting the system. On the start of the guest, the map of the guest is given the address of the GPU to use that device address as a resource. So to the host is the passthorugh is considered as discrete and is only used by that VM guest (as if it was connected to a physical machine). So that your host system sees it, by does not reserve it as a resource...

I think what you are implying would be logically be like connecting a video card and monitor to two machines.  I have a widescreen that would that two inputs and display them side-by-side, but this is not this... You understand this when you said you have a successful passthrough graphics device right?

What GPU are you using for the hosted system as the non-discrete GPU and display? You can't use a passthrough GPU as both discreet and non-discrete. Your guest is Windows, so would be physically connecting to the passthrough GPU as the sole owner of that device... right? (so would not use an xorg.conf for that device). Now if your guest was Ubuntu, then you would define it with an xorg.conf...

---

### Post by JORGE_FERNANDEZ on 2016-02-18
My host os is a vmware esxi 6.0. My guests are a xubuntu, a windows 8.1 with a 390x for gaming and I have plans to add a future w series firepro to another windows 8.1 machine for cad & video. I have connected only (for testing purposes ) the 6200 le. The other machines are not configured yet.

The passtrough NVIDIA 6200 LE card is used first for booting the esxi. When linux boots/starts, it claims it and the esxi box screen turns off (obviously) but no video with xorg configured. Linux has another card svga vmware (virtual esxi card) but if you dont specify anything into xorg its not used by the system (I supose that). My future goal is trying first with this card after buying a new one that can handle more monitors and higher resolutions.

I don't uderstand the part of discrete and non-discrete.

---

### Post by MAFoElffen on 2016-02-19
Okay. I was confused by your first post. On your xubuntu "guest", if nvidia drivers are installed and it see's a montior...
```

sudo nvidia-xconfig

```
Would re-gen an xorg.conf file on what it sees.

It puts that file into the directory /etc/X11/

If you look at the docs, there is a search precedence order that it uses to look for that file:
```

    /etc/X11/<cmdline>
    /usr/etc/X11/<cmdline>
    /etc/X11/$XORGCONFIG
    /usr/etc/X11/$XORGCONFIG
    /etc/X11/xorg.conf
    /etc/xorg.conf
    /usr/etc/X11/xorg.conf.<hostname>
    /usr/etc/X11/xorg.conf
    /usr/lib/X11/xorg.conf.<hostname>
    /usr/lib/X11/xorg.conf

```
So, historically, in various distros of Linux, the first place you look for that file is in that first directory.

My suggestion is to move what you had to your home directory as a backup, then let nvidia-xconfig do the work for you, then tweak it from there.

What XServer does when it boots id it looks for an xorg.conf file for settings. Then does probes on hardware. First probe is for the Video card, If an xorg.conf file exists, it only proabes what is defined in the device section, slot address. Then maps a driver to it. When it probes that card, then it probed the ports on that card, looking for attached devices. If a port does not see a monitor attached, it runes those unused ports off. If it does see a montor, it then probes for an EDID from the monitor, then probes a refresh rates and modes. If you define something, then it only uses those settings. Then there are overrides that you can use...

I gave this explanation, because you have a lot of things that you didn't need to define for just a basic install. Lots of things you can tweak with nvidia-settings, that will automate what setting to write out to that file, that beyond the basic. For instance, a modeline is not needed unless XServer does not find an EDID file from your monitor. If that happens then you would need to define that with a modeline, along with telling XServer to ignore EDID and not probe for one... If you do not tell it to ignore EDID, it will have problems. Most of the time it will just ignore the modeline... but sometimes...

Refresh rates look okay there.

You can say preferred mode to what it said, which was all 1080p // 1920x1080 resolution It said a range, but I would assume at 60. You could confirm the preferred mode with xrandr.

---

