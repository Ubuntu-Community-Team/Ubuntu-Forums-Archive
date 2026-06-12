---
title: "Dual monitor login"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-12
Until just a couple of days ago, I was running the nvidia proprietary drivers on my dual-monitor Quadro.  In trying to isolate a hard crash on the -22-generic kernel, I switched over to the nouveau driver set.

When jockey backed out nvidia-current, it blew away /etc/X11/xorg.conf -- that's mostly a good thing -- but it did *not* replace it with a new xorg.conf.

So the X server just reverts to default behavior -- it mirrors the output on both monitors and uses the lowest common monitor resolution on both monitors.  You can check out what the X server is doing on startup by looking at /var/log/Xorg.0.log -- here's what it looks like when X is making up stuff up as it goes along ;)
```
[     8.567] Markers: (--) probed, (**) from config file, (==) default setting,
 (++) from command line, (!!) notice, (II) informational,
 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.567] (==) Log file: "/var/log/Xorg.0.
log", Time: Thu Oct 13 14:22:37 2011
[     8.579] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.579] (==) No Layout section.  Using the first Screen section.
[     8.579] (==) No screen section available. Using defaults.
[     8.579] (**) |-->Screen "Default Screen Section" (0)
[     8.579] (**) |   |-->Monitor "<default monitor>"
[     8.579] (==) No monitor specified for screen "Default Screen Section".
 Using a default monitor configuration.
```There is a bug for this unwanted behavior wrt an "external" monitor -- like a TV -- here [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874241](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/874241) but not for this similar situation.  I commented on that bug but I thought it relevant to repeat here for others that might be searching for a solution.

A valid xorg.conf is required for lightdm + greeter to behave properly in a multi-monitor configuration. (Note: gnome-control-center does not edit the xorg.conf -- its configuration is saved in ~/.config/monitors.xml)

[B]I do not recommend editing your xorg.conf unless you know what you're doing and can recover if the X server won't start.
[/B] 
 The key requirements in a dual-monitor configuration for xorg.conf are:
1) a "ServerLayout" section that identifies the "Screen" section
2) the desired virtual size in Section "Screen"/Subsection "Display"
3) indicating which monitors are connected to which outputs


Here's my xorg.conf *which is specific to my setup*. Do NOT copy it to your setup! This is an aid to understanding, in conjunction with the xorg.conf man page.
 ```
Section "Device"
    Identifier     "Device0"
    Driver         "nouveau"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 570"
    Option         "Monitor-DVI-I-1" "Monitor0"
    Option           "Monitor-DVI-I-2" "Monitor1"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "DELL"
    ModelName      "DELL 2208WFP"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "DELL"
    ModelName      "DELL 1905FP"
    Option         "LeftOf" "Monitor0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Virtual 2960 1050
    EndSubSection
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    # generated from default
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
```

For those of you that reallly do know what you're doing, nouveau does not support the "Position" option in xorg.conf. This means that if you're getting that irritating background shift between greeter and session you have to edit the session side (via either gnome-control-center or editing your ~/.config/monitors.xml).

---

### Post by Nick Payne on 2012-04-12
I'm also using the Nouveau driver, and creating an xorg.conf enables me to get a login screen with the correct resolution on both monitors and the login dialog on only one monitor. However, I have the secondary monitor in portrait orientation, and the driver doesn't seem to recognise the commands I've put in xorg.conf to indicate this:

```
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "DELL"
    ModelName      "DELL U2311H"
    Option         "RightOf" "Monitor0"
    Option         "RandRRotation" "on"
    Option         "Rotate" "CCW"
EndSection

```

The display on this monitor doesn't get rotated - if I move the mouse to that monitor, it comes in from the top rather than the side, and the login dialog is sideways. Once I'm logged in, I do get the correct orientation on the 2nd monitor, but that was setup using the Displays dialog in System Settings.

---

### Post by NHclimber on 2012-04-12
The nouveau driver doesn't use "CCW" for a "ROTATE" value. That should read:
```
    Option         "Rotate" "Left" 
```

Also, I don't think you need "RandRRotation".  Check /var/log/Xorg.0.log;  it will report unused values near the end of the nouveau initialization [Note: there will be two initialization timelines -- 1 for the greeter and again for the session].

---

