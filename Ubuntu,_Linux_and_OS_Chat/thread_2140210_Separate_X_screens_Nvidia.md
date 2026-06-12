---
title: "Separate X screens Nvidia"
date: 2013-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by VietCanada on 2013-04-29
Ubuntu 10 had this feature. I have a PC monitor with 1280x1024 and a TV with 1920x1080. Being able to use each in its own resolution was great. Ever since version 11 however this option does not work. My PC monitor is my primary display. With separate X screens enabled it works but my TV is just white. If I move the mouse onto it it becomes a black X and will not move back to the primary monitor forcing me to hit the physical restart button on my PC.

Why does this still not function? I have searched for a solution or explanation for years. I can't find one. Except for one common response- 'just use twinview'. Twinview is not the same as separate X screens. That's why I use it, that's why I installed Linux Mint Mate 13.

Ubuntu version 13 started off okay. It was defaulted to Twinview and I found the option to set each monitor to its native display. I thought that was it but noooooooo. When I ran a game in full screen on the TV, the PC monitor greyed out and stopped functioning. The clock didn't even work. My TV is on the left of my monitor. If I use that setting in NVIDIA X Server Settings, the windows I open span both screens. Whatever screen I open a window in seems to become the default screen for that window until I physically grab it and move it to my primary monitor. This is a problem. Each program opens its window on the monitor that it had been last used on.

It's been three years now? Why hasn't this issue been fixed? I notice someone asking that question about three times on the bug page for this issue. 

13 is so buggy that I can't see using it in its present form for anything important. For now I'll leave it as a dual boot option and keep checking from time to time to see if this option on my NVIDIA X Server Settings screen has been enabled. If the decision has been made to ignore this issue and never restore it then please remove the option.

---

### Post by cariboo on 2013-04-29
This isn't a Saucy support or any other type of support question. Moved.

---

### Post by muktupavels on 2013-04-29
> **VietCanada said:**
> With separate X screens enabled it works but my TV is just white.
White screen is nautilus bug. You simply see white color instead your background image.

> **VietCanada said:**
>  If I move the mouse  onto it it becomes a black X and will not move back to the primary  monitor forcing me to hit the physical restart button on my PC.
In 13.04 this bug (not moving back to primary monitor) has been fixed.

I am using gnome fallback session (**sudo apt-get install gnome-session-fallback**). You see black cursor because compiz is started only on primary monitor. I have added two extra entries in startup applications:
1) **compiz --replace --display :0.1** (second screen)
2) **compiz --replace --display :0.2** (third screen)

I use 3 screens set up in separate x screen mode on main seat and one screen on second seat. One video card for each seat, both are nvida cards. Everything is working quite good.

---

### Post by VietCanada on 2013-04-29
I owe you a beer big time if this works for me. I thought I read something about this which caused me to be excited about installing U13.

I can Do the command in the terminal I am not sure about addin the two entries in startup applications. I just don't know what that means. Can I click on startup applications and then tick a couple of boxes or do I need to gksudo (?) to open a file and these lines then save the file?

WOW it'll be great to get that function back on Ubuntu. TY

---

### Post by VietCanada on 2013-04-29
First I ran the command in terminal. I set up separate x-screens with the nvidia app. Restarted and ended up with a white screen on my TV. The mouse would not leave the PC monitor. Progress of some sort I suppose if change is progress. I choose the gnome fallback session as an option on the log in screen.

Second- I opened startup applications and selected add. I copied the nvidia-xconfig into the name and compiz --replace --display :01 into commands. I set up separate x-screens with the nvidia app. Restarted and ended up with only a desktop picture, nothing else. No dash, no panels, no options. I alos tried rebooting with theout changing the options. Same thing.

Seems I bricked the thing. Fortunately I dual boot with Mate 13 so I've lost nothing really.

I tried the failsafe mode at the grub but then I got something totally messed up on both screens,

I'm going to reinstall and mess around with this some more. You got it working so it is possible. I have a command for restoring panels from a time I accidently killed mine. Perhaps that will be useful. :cheers:

---

### Post by muktupavels on 2013-04-29
When you logged in gnome fallback, did you get top and bottom panels on both screens?

Adding startup entries is easy. Just open startup applications. Click on Add button. Choose name of startup application, you can write whatever you want. In command add line - **compiz --replace cpp --display :0.1** . Between zero and one must be dot.

I am using nvidia driver 313.30 from nvidia.com and kernel 3.9rc8.

Here is my xorg.conf for seat with seperate x screens:```
Section "ServerLayout"
    Identifier      "Seat1"
    Screen      0   "Screen0" 0 0
    Screen      1   "Screen1" LeftOf "Screen0"
    Screen      2   "Screen2" RightOf "Screen0"
EndSection

Section "ServerFlags"
    Option          "Xinerama" "0"
EndSection

Section "InputClass"
    Identifier "ignore other seats"
    Option "Ignore" "yes"
EndSection

Section "InputClass"
    Identifier "input seat1"
    MatchTag "input-seat1"
    Option "Ignore" "no"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    ModelName      "Philips 19S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    ModelName      "COMPAQ 1825"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    ModelName      "Philips 19S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    BusID          "PCI:1:0:0"
    Screen          0
    Option           "NoLogo" "True"
    Option            "ProbeAllGpus" "false"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    BusID          "PCI:1:0:0"
    Screen         1
    Option           "NoLogo" "True"
    Option            "ProbeAllGpus" "false"
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
    BusID          "PCI:1:0:0"
    Screen          2
    Option           "NoLogo" "True"
    Option            "ProbeAllGpus" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-3: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
``` Ignore section inputclass, you don't need that.

---

### Post by VietCanada on 2013-04-29
There were no panels. Just my desktop wallpaper. Nothing else. I may not have put in the dot. I just finished re-installing and configuring things. I'll try this and reboot. Thanx.

---

### Post by mips on 2013-04-29
Just use nvidia-settings to set up dual screens with different resolutions.

---

