---
title: "HOWTO:Nvidia AGP FastWrites and Side Band Addressing"
date: 2006-03-07
forum: Tutorials
---

### Post by tseliot on 2006-03-07
**Introduction**

This guide is largely inspired to a wonderful guide of the Gentoo Forums (and wiki) ( and I would really thank the user elboricua who wrote the original guide. Unfortunately Gentoo and Ubuntu do not share the same configuration files therefore I couldn't port the entire guide to Ubuntu.

You can find the original guide for Gentoo here:
[Nvidia Driver AGP FastWrites and Side Band Addressing]("http://gentoo-wiki.com/HARDWARE_Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing")

The purpose of this guide is to give you a performance boost which could help you in 3d applications such as videogames.


**Requirements**

By default the nvidia drivers do not enable AGP FastWrites or Side Band Addressing. This tip is a quick and easy way to turn it on. To enable fastwrite you must have a motherboard that supports it, and have it turned on in the BIOS. Most AMD boards have fastwrite capability. I am not sure about Pentium based boards. 

You need a kernel compiled with support for agpgart (you can find it under the section Character Devices). The kernels that come with Ubuntu by default support agpgart.

You need to have the Nvidia Drivers enabled and working. If you haven't installed the driver yet you can follow my guide on:

[HOWTO: Latest NVIDIA drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")


*NOTE: This tip requires a reboot.*


**NOTE: Fast Writes and SBA might make your computer freeze if they are not supported therefore you should use them at your own risk.**


**Check to see if the FastWrites and SBA is enabled or disabled **

```
cat /proc/driver/nvidia/agp/status
```


```
Status:          Enabled
Driver:          AGPGART 
AGP Rate:        4x 
Fast Writes:     Disabled 
SBA:             Disabled
```

Test the fps you can get with your current setup

Open Terminal or Konsole and type:

```
glxgears -printfps
```

You will get something like this:

```
~$ glxgears -printfps
6073 frames in 5.0 seconds = 1214.530 FPS
6723 frames in 5.0 seconds = 1344.542 FPS
6724 frames in 5.0 seconds = 1344.704 FPS
6725 frames in 5.0 seconds = 1344.805 FPS
6724 frames in 5.0 seconds = 1344.699 FPS
6724 frames in 5.0 seconds = 1344.657 FPS
6727 frames in 5.0 seconds = 1345.201 FPS
6724 frames in 5.0 seconds = 1344.708 FPS
6724 frames in 5.0 seconds = 1344.774 FPS
6719 frames in 5.0 seconds = 1343.688 FPS
6627 frames in 5.0 seconds = 1317.529 FPS
```

*NOTE: you can press CTRL+C in the command line to stop the process*

Save the output somewhere so that you can see if you get an fps boost after enabling Fast Writes and SBA.


**Enable Fast Writes and SBA**


Open Terminal or Konsole and type:

```
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```

OR (if you use KDE)
```
kdesu kedit /etc/modprobe.d/nvidia-kernel-nkc
```

OR
```
sudo nano /etc/modprobe.d/nvidia-kernel-nkc
```

You should see a line like the following:

```
alias char-major-195* nvidia
```

**If so**, add the following line at the end of the file

```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

so that it will look like this:

```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

Save the file and exit.

[B]NOTE: Otherwise if the file is blank:
exit from the text editor and make a new file in the following way:
```
sudo nano /etc/modprobe.d/nvidia
```
make the content look like this
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```[/B]

Restart your computer.

**Check that it works**

Type:

```
cat /proc/driver/nvidia/agp/status
```

If you get something like this then it works

```
Status:          Enabled
Driver:          AGPGART 
AGP Rate:        4x 
Fast Writes:     Enabled 
SBA:             Enabled
```


Test the fps you can get with your current setup

Open Terminal or Konsole and type:

```
glxgears -printfps
```

It is likely that the number of fps has increased. Nonetheless you shouldn't rely only on glxgears and you should see if you have a performance boost while using games (or other 3d applications)


**If you want to disable Fast Writes and SBA**

Open Terminal or Konsole and type:

```
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```

OR (if you use KDE)
```
kdesu kedit /etc/modprobe.d/nvidia-kernel-nkc
```

OR
```
sudo nano /etc/modprobe.d/nvidia-kernel-nkc
```

Remove the following line:

```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```


Save the file and exit.

Restart your computer.

---

### Post by donar73 on 2006-03-08
Thx for the HowTo, works flawless. 
But (there's always a "but", isn't it? ;)): it doesn't seem to give a performance-boost to enable "FastWrites" (SBA was already enabled by default) on my system (AthlonXP 2800, Gforce 6600GT) - glxgears gave me nearly the same results as before.

---

### Post by tseliot on 2006-03-08
[QUOTE=donar73]Thx for the HowTo, works flawless. 
But (there's always a "but", isn't it? ;)): it doesn't seem to give a performance-boost to enable "FastWrites" (SBA was already enabled by default) on my system (AthlonXP 2800, Gforce 6600GT) - glxgears gave me nearly the same results as before.[/QUOTE]
Sometimes it helps, sometimes not (it can depend on your card and mobo). Nonetheless you should try a 3d game and see how it goes.

---

### Post by Rizado on 2006-03-08
It's a bit odd but I don't have any nvidia-kernel-nkc. But I solved it by adding "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" in /etc/modules instead. In case someone else are in the same situation.

---

### Post by arikato on 2006-03-08
heh got ~300fps more after that
thansk for how to

---

### Post by tseliot on 2006-03-08
[QUOTE=Rizado]It's a bit odd but I don't have any nvidia-kernel-nkc. But I solved it by adding "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" in /etc/modules instead. In case someone else are in the same situation.[/QUOTE]
Which Method did you use to install the Nvidia driver?

---

### Post by i3dmaster on 2006-03-08
```

cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

dmesg |grep -i agp
[4294695.587000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.589000] agpgart: Detected ALi M1671 chipset
[4294695.600000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294734.179000] NVRM: not using NVAGP, an AGPGART backend is loaded!
[4294734.969000] NVRM: not using NVAGP, an AGPGART backend is loaded!

```
That's all the info from dmesg regarding AGP stuff. What is the problem?

---

### Post by tseliot on 2006-03-09
[QUOTE=i3dmaster]```

cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

dmesg |grep -i agp
[4294695.587000] Linux agpgart interface v0.101 (c) Dave Jones
[4294695.589000] agpgart: Detected ALi M1671 chipset
[4294695.600000] agpgart: AGP aperture is 128M @ 0xf0000000
[4294734.179000] NVRM: not using NVAGP, an AGPGART backend is loaded!
[4294734.969000] NVRM: not using NVAGP, an AGPGART backend is loaded!

```
That's all the info from dmesg regarding AGP stuff. What is the problem?[/QUOTE]
Can you post the content of your /etc/X11/xorg.conf ?

---

### Post by i3dmaster on 2006-03-09
Here we go...
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option         "HorizScrollDelta"      "0"
#EndSection

Section "ServerLayout"

#       InputDevice     "Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

#       FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        # paths to defoma fonts
    FontPath        "/usr/X11R6/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/cyrillic"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/Type1"
    FontPath        "/usr/lib/X11/fonts/CID"
    FontPath        "/usr/lib/X11/fonts/100dpi"
    FontPath        "/usr/lib/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
#   Load           "ddc"
    Load           "extmod"
    Load           "v4l"
#   Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
    Load           "xtt"
    Load           "dri"
    Load        "i2c"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 107.0
    VertRefresh     50.0 - 185.0
    ModeLine       "1280x854" 85.3 1280 1296 1552 1792 854 854 861 892
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Driver         "nvidia"
    Option          "NvAGP" "1"
    Option          "NoLogo" "true"
    Option          "RenderAccel" "true"
    Option          "AllowGLXWithComposite" "true"
    Option          "CursorShadow" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x854"
    EndSubSection
EndSection

#Section "Extensions"
#        Option  "Composite" "Enable"
#EndSection

```

---

### Post by tseliot on 2006-03-09
[QUOTE=i3dmaster]Here we go...
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option         "HorizScrollDelta"      "0"
#EndSection

Section "ServerLayout"

#       InputDevice     "Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

#       FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        # paths to defoma fonts
    FontPath        "/usr/X11R6/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/cyrillic"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/Type1"
    FontPath        "/usr/lib/X11/fonts/CID"
    FontPath        "/usr/lib/X11/fonts/100dpi"
    FontPath        "/usr/lib/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
#   Load           "ddc"
    Load           "extmod"
    Load           "v4l"
#   Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
    Load           "xtt"
    Load           "dri"
    Load        "i2c"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 107.0
    VertRefresh     50.0 - 185.0
    ModeLine       "1280x854" 85.3 1280 1296 1552 1792 854 854 861 892
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Driver         "nvidia"
    Option          "NvAGP" "1"
    Option          "NoLogo" "true"
    Option          "RenderAccel" "true"
    Option          "AllowGLXWithComposite" "true"
    Option          "CursorShadow" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go 32M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x854"
    EndSubSection
EndSection

#Section "Extensions"
#        Option  "Composite" "Enable"
#EndSection

```[/QUOTE]
Here's your problem:
Option          "NvAGP" "1"

Can you comment it out (i.e. put a # before it)?

NvAGP is not loaded but agpgart will work fine.

Then restart your computer.

Let me know if it works

---

### Post by Rizado on 2006-03-09
[QUOTE=tseliot]Which Method did you use to install the Nvidia driver?[/QUOTE]Nvidia installer. But I have a vanilla kernel too so it may be because of that.

---

### Post by tseliot on 2006-03-09
[QUOTE=Rizado]Nvidia installer. But I have a vanilla kernel too so it may be because of that.[/QUOTE]
I haven't tried it with a vanilla kernel yet. :-k 

Can anyone with a vanilla kernel confirm this problem?

---

### Post by Neo40 on 2006-03-09
Hi,

I tried it but I don't get much more fps. Before I had around 1275 fps. With fast writes enabled I get 1282 fps.

---

### Post by mcwtlg on 2006-03-09
I used the Nvidia installer with my GForce 5600 FX
I have the 2.6.12-10-686 kernel
I did not have nvidia-kernel-nkc so I took the advice of Rizado and added "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" to /etc/modules
I gained 200 fps according to glxgears

Thanx to you all.

I hope that helps someone...

Edit -- I just checked and I still have Fast Writes disabled ... hmmm

mark@HB-Linux:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

Any ideas?  Abit IS-7 mobo / Nvidia GeForce 5600FX vid card

---

### Post by tseliot on 2006-03-10
[QUOTE=mcwtlg]I used the Nvidia installer with my GForce 5600 FX
I have the 2.6.12-10-686 kernel
I did not have nvidia-kernel-nkc so I took the advice of Rizado and added "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" to /etc/modules
I gained 200 fps according to glxgears

Thanx to you all.

I hope that helps someone...[/QUOTE]
Ok I'll add it to the guide.

Thanks Rizado and mcwtlg

EDIT: DONE!

---

### Post by z-vet on 2006-03-11
It did not worked for me with /etc/modules, so after reading an article in Gentoo Wiki i just created /etc/modprobe.d/nvidia file and added there:
```

alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

```
which gives me this:
```
 
cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled
```

---

### Post by tseliot on 2006-03-11
[QUOTE=z-vet]It did not worked for me with /etc/modules, so after reading an article in Gentoo Wiki i just created /etc/modprobe.d/nvidia file and added there: ```
 alias char-major-195 nvidia options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 
``` which gives me this: ```
 cat /proc/driver/nvidia/agp/status Status: Enabled Driver: AGPGART AGP Rate: 4x Fast Writes: Enabled SBA: Enabled
```[/QUOTE] Very interesting! Thanks for reporting, I'll add it to the guide.

EDIT: You mean the "/etc/modprobe.d/nvidia-kernel-nkc" file, don't you?

---

### Post by z-vet on 2006-03-11
[QUOTE=tseliot]You mean the "/etc/modprobe.d/nvidia-kernel-nkc" file, don't you?[/QUOTE]
No, i mean /etc/modprobe.d/**nvidia** :)

---

### Post by Rizado on 2006-03-11
It's weird adding the line to modules doesn't work, maybe agpgart has to be loaded first.

Creating /etc/modprobe.d/nvidia is probably better because that will enable fastwrites everytime nvidia is loaded, adding the line in modules will only enable it when loaded at boot time. Also I have noticed that adding nvidia to modules make x start faster. Or atleast there's no corrupted screen just before kdm/gdm starts (The ugly grey and black screen)

---

### Post by mcwtlg on 2006-03-11
That worked...thanx z-vet

I did not have nvidia-kernel-nkc.  First I took the advice of Rizado and added "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" to /etc/modules, but that did not work (fast writes were still disabled).

I then took z-vet's advice and created /etc/modprobe.d/nvidia and put: 
alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

into that file, saved it and rebooted.

Now I get:

mark@HB-Linux:~$ cat /proc/driver/nvidia/agp/status
Status: Enabled
Driver: AGPGART
AGP Rate: 8x
Fast Writes: Enabled
SBA: Enabled

12039 frames in 5.0 seconds = 2406.168 FPS
11974 frames in 5.0 seconds = 2394.695 FPS
11786 frames in 5.0 seconds = 2350.184 FPS
11951 frames in 5.0 seconds = 2390.186 FPS
11822 frames in 5.0 seconds = 2364.329 FPS
11781 frames in 5.0 seconds = 2353.736 FPS
11794 frames in 5.0 seconds = 2358.772 FPS

Which is a total of about 250 fps faster in glxgears.  Overall I am happy!  Thanx to EVERYONE for their imput!

---

### Post by Eazy© on 2006-03-11
[QUOTE=mcwtlg]That worked...thanx z-vet

I did not have nvidia-kernel-nkc.  First I took the advice of Rizado and added "nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" to /etc/modules, but that did not work (fast writes were still disabled).

I then took z-vet's advice and created /etc/modprobe.d/nvidia and put: 
alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

into that file, saved it and rebooted.
[/QUOTE]

I did not have nvidia-kernel-nkc either, and this is the only solution that works for me. If I get better fps I can't tell becaus I get differnt results every time I run glxgears. Sometimes I get better fps than before enable fastwrites, and sometimes worse.

---

### Post by rjwood on 2006-03-11
Thanks tseliot it works great on dapper too:-D got about 250fps increase. I notice it in overall performance.

---

### Post by tseliot on 2006-03-11
[QUOTE=z-vet]No, i mean /etc/modprobe.d/**nvidia** :)[/QUOTE]
Ok, I'll fix the guide.

Thanks everybody

---

### Post by mcwtlg on 2006-03-12
[QUOTE=Eazy©]I did not have nvidia-kernel-nkc either, and this is the only solution that works for me. If I get better fps I can't tell becaus I get differnt results every time I run glxgears. Sometimes I get better fps than before enable fastwrites, and sometimes worse.[/QUOTE]

I found that the only way to tell was to NOT move the mouse.  Moving the mouse can skew the results.

---

### Post by tseliot on 2006-03-13
[QUOTE=mcwtlg]I found that the only way to tell was to NOT move the mouse.  Moving the mouse can skew the results.[/QUOTE]
You shouldn't rely upon glxgears too much. Try it in games,etc.

---

### Post by PowerRanger on 2006-04-12
Does the nvidia_agp module offer anything over the generic linux agpgart from a performance perspective?  What I want to know is whether it is worth recompiling my kernel explicitly without agpgart( I can't get it to stop loading)  so that I can use the nvidia_agp.  I have an nvidia chipset based mobo.  The performance of my 5500 based card just seems sluggish compared to my old geforce 4 mx, and I've tried just about everything else I've read about to get it to perform.

---

### Post by tseliot on 2006-04-13
[QUOTE=PowerRanger]Does the nvidia_agp module offer anything over the generic linux agpgart from a performance perspective?  What I want to know is whether it is worth recompiling my kernel explicitly without agpgart( I can't get it to stop loading)  so that I can use the nvidia_agp.  I have an nvidia chipset based mobo.  The performance of my 5500 based card just seems sluggish compared to my old geforce 4 mx, and I've tried just about everything else I've read about to get it to perform.[/QUOTE]
It's a matter of compatibility. Agpgart supports more graphic cards than nv_agp.
I have a Geforce FX 5500 (128MB) and nv_agp doesn't work for me.

---

### Post by PowerRanger on 2006-04-13
Do you know whether your particular incompatibility issue is related to the card, or the chipset?  I actually have 2 5500's in my machine, a 256 agp and a 128 pci .    Anyway, compatibility issues aside, can anyone definitively say the performance of nvidia_agp is better than agpgart? 


Thanks

---

### Post by tseliot on 2006-04-13
[QUOTE=PowerRanger]Do you know whether your particular incompatibility issue is related to the card, or the chipset?  I actually have 2 5500's in my machine, a 256 agp and a 128 pci .    Anyway, compatibility issues aside, can anyone definitively say the performance of nvidia_agp is better than agpgart? 


Thanks[/QUOTE]
Have a look at this page, please:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/appendix-f.html]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/appendix-f.html")

---

### Post by PowerRanger on 2006-04-13
Yeah, I' actually read the readme when I installed the driver. 

My issue lies in the statement "You should use the AGP module that works best with your AGP chip set. "

I've never been able to use the nvidia_agp because agpgart is compiled into my kernel, I can't blacklist it,  so I don't know if it would be 'best' or not.  

That's why I'm asking whether it's worth it for me to try re-compiling the kernel without the agpgart.  Do you know of A good guide for re-compiling the kernel without agpgart?

I was asking, because if somebody can say definitively that it won't help with performance, I won't waste my time and risk my current setup.  On the other hand, if that is where I might be able to improve performance, I would like to give it a try.

---

### Post by tseliot on 2006-04-13
[QUOTE=PowerRanger]That's why I'm asking whether it's worth it for me to try re-compiling the kernel without the agpgart.  Do you know of A good guide for re-compiling the kernel without agpgart?[/QUOTE]
I recompiled my kernel without agpgart but then I couldn't get the nvidia driver to work.

If you want a guide about how to compile a kernel:
[http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")
but it doesn't explain how to disable agpgart (and I don't remember how I did it). Google might be your best friend in this case.

---

### Post by PowerRanger on 2006-04-13
Yeah, I tried renaming the agpgart.ko (not sure of the name, /lib/modules/kerner version/char/agp or something like that) and then had lotsa 'unresolved symbol' errors in the system log ( and x log) when the nvidia_agp module tried to load.  I went back and checked the nvidia driver installer log  and it seemed like it knew the agpgart was loaded so didn't do anything to the nvidia_agp  module. I'm not in front of that machine now so I can't check it.

What I was gonna do was recompile the kernel( without agpgart) then try to reinstall the nvidia drivers.

---

### Post by PowerRanger on 2006-04-13
Arghh- Frustration is setting in....](*,) 

I _can't_ seem to disable agpgart in the kernel configuration.  I've googled all over the place, the only thing I can find is that if iommu is enabled, agpgart must be loaded as a module.  (iommu is for AMD64 >4GB RAM) Unfortunately, I can't find iommu in my kernel configuration.  I've looked over the .config file, it's not there.  It's supposed to be in the kernel configuration, under  'Processor Type and Features'.


I did stumble across something else though, I think you can set a 'no iommu' parameter at boot in GRUB! I wonder if this will have any affect on not being able to blacklist the agpgart.

---

### Post by domino on 2006-04-19
Thanks for this how-to. The default nv drivers already had sb enabled so all I had to do was edit and add the fast write option and restart. Pre-gear diag was ~5500 and post-gear diag is ~6500. Now if only I had any interests in gaming :S

---

### Post by russ_armst on 2006-05-14
Thanks for the HowTo. I can confirm this works on Dapper with a PCI-Express 7300GS on a DFI NF4 DR-SLi Expert board without changing any BIOS settings. Its nearly doubled my FPS in glxgears!:-D

EDIT: Ok maybe not double, I guess not running Seti Enhanced at the same time helped a good bit. Still seems to be alot faster.

---

### Post by tseliot on 2006-05-14
[QUOTE=russ_armst]Thanks for the HowTo. I can confirm this works on Dapper with a PCI-Express 7300GS on a DFI NF4 DR-SLi Expert board without changing any BIOS settings. Its nearly doubled my FPS in glxgears!:-D

EDIT: Ok maybe not double, I guess not running Seti Enhanced at the same time helped a good bit. Still seems to be alot faster.[/QUOTE]
Thanks for reporting

---

### Post by beeldings on 2006-05-19
Running Dapper on AMD Athlon 64 3000+ installed on an Asus K8V-MX with 2 GB DDR 400 and a PNY Verto GeForce 6200 AGP video card. I installed the nvidia-glx drivers with apt-get and followed this how-to step-by-step. SBA was enabled by default, however I cannot enable FW even though I have it enabled in my BIOS. This problem also existed when I ran Breezy Badger. If it matters, I have XGL and compiz installed and running.

---

### Post by tseliot on 2006-05-20
[QUOTE=beeldings]Running Dapper on AMD Athlon 64 3000+ installed on an Asus K8V-MX with 2 GB DDR 400 and a PNY Verto GeForce 6200 AGP video card. I installed the nvidia-glx drivers with apt-get and followed this how-to step-by-step. SBA was enabled by default, however I cannot enable FW even though I have it enabled in my BIOS. This problem also existed when I ran Breezy Badger. If it matters, I have XGL and compiz installed and running.[/QUOTE]
can you post the content of your "/etc/modprobe.d/nvidia" ?

---

### Post by beeldings on 2006-05-20
[quote=tseliot]
can you post the content of your "/etc/modprobe.d/nvidia" ?
[/quote]

I just checked it with nano and it's empty.

---

### Post by tseliot on 2006-05-20
[QUOTE=beeldings]I just checked it with nano and it's empty.[/QUOTE]
Make it look like this (as it's written in the guide):
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

---

### Post by beeldings on 2006-05-20
[QUOTE=tseliot]Make it look like this (as it's written in the guide):
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```[/QUOTE]

Ok, the file has been edited per your instructions. However, Fast Writes is still disabled. If it helps, here's the entry for my video card in my xorg.conf file:
```

Section "Device"
        Identifier      "NVIDIA Corporation GeForce 6200 AGP"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

and here is the modules section:
```

Section "Module"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "GLcore"
EndSection


```

According to glxinfo, my drivers are:
```

OpenGL version string: 2.0.2 NVIDIA 87.56

```

---

### Post by tseliot on 2006-05-21
1) Can you post the content of this?
sudo nano /etc/modprobe.d/nvidia-kernel-nkc

2) Did you enable Fast Writes in your BIOS?

---

### Post by beeldings on 2006-05-21
[QUOTE=tseliot]1) Can you post the content of this?
sudo nano /etc/modprobe.d/nvidia-kernel-nkc

2) Did you enable Fast Writes in your BIOS?[/QUOTE]

1) alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

2) Yes.

---

### Post by beeldings on 2006-05-22
I reviewed the original Gentoo Wiki entry and noticed this:
```

cat /proc/driver/nvidia/agp/host-bridge

```
which output the following:
```

Host Bridge:     PCI device 1106:0204
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000a0b:0x00000b02

```
So, it's not a problem with tseliot's guide, Ubuntu, the NVIDIA drivers or the card itself, but it appears to be a problem with the motherboard's AGP interface. Even though I cannot enable Fast Writes, I found a working alternative with nvclock. I will attempt to upgrade the BIOS to see if this will correct the problem or not.

---

### Post by zenwhen on 2006-07-13
Worked for me with an Nvidia 6800nu and an Abit IS7.

---

### Post by fiuman on 2006-07-15
```
cat /proc/driver/nvidia/agp/status

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Disabled

```

```
 cat /proc/driver/nvidia/agp/host-bridge

Host Bridge:     PCI device 1039:0745
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x00000114

```

```
 cat /proc/driver/nvidia/agp/card

Fast Writes:     Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000017:0x1f000114

```

why in host-bridge output sba is supported and in card output is not supported???

i have a 3d prophet 2 mx gforce2 (nvidia-based)

---

### Post by panurge77 on 2006-07-15
Theres no agp in my /proc/driver/nvidia
lsmod shows me agpgart is loaded
whats my problem?

---

### Post by tseliot on 2006-07-15
> **panurge77 said:**
> Theres no agp in my /proc/driver/nvidia
lsmod shows me agpgart is loaded
whats my problem?

can you post:

1) the model of your card

2) the output of this command:
```
lspci -n | grep 0300
```

---

### Post by panurge77 on 2006-07-15
floyd@tchs:~$ lspci -n | grep 0300
01:00.0 0300: 10de:0141 (rev a2)

it's a geforce 6600 pci-e
duh
I just rembered agp are the cards that are not pci-e, right?

---

### Post by tseliot on 2006-07-15
> **panurge77 said:**
> I just rembered agp are the cards that are not pci-e, right?
Right ;)

---

### Post by fiuman on 2006-07-15
my sba is disabled cause isn't supported???

---

### Post by tseliot on 2006-07-16
> **fiuman said:**
> ```
 cat /proc/driver/nvidia/agp/card

Fast Writes:     Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000017:0x1f000114

```

why in host-bridge output sba is supported and in card output is not supported???
I wouldn't know. But it looks like it's not supported.

---

### Post by fiuman on 2006-07-16
kk tnx

---

### Post by gborzi on 2006-07-20
Nice howto, now I have *Fast Writes* enabled. Only one note, you don't need to restart your computer. Instead of rebooting switch to a console (Ctrl+Alt+F1), login, stop gdm (or kdm )
> sudo /etc/init.d/gdm stop
unload the nvidia module
> sudo modprobe -r nvidia
reload it
> sudo modprobe nvidia
start gdm (or kdm )
> sudo /etc/init.d/gdm start

---

### Post by tseliot on 2006-07-21
> **gborzi said:**
> Nice howto, now I have *Fast Writes* enabled. Only one note, you don't need to restart your computer. Instead of rebooting switch to a console (Ctrl+Alt+F1), login, stop gdm (or kdm )

unload the nvidia module

reload it

start gdm (or kdm )

I know that but sometimes things just go wrong until you reboot.

Ah... the mysteries of IT :mrgreen:

---

### Post by anti-trend on 2006-08-22
Hi Ubuntu forums!

Mainstream Debian user here, but I have some info which you may find helpful. It seems that with most configurations, many of the steps listed here are not necessary. If you already have working 3D with AGP, simply do the following:

```

*#get root*
[SIZE="2"]**sudo bash**[/SIZE]
*#if /etc/modprobe.d/nvidia doesn't exist, create it:*
[SIZE="2"]**touch /etc/modprobe.d/nvidia**[/SIZE]
*#Now add the option to enable Side-banding and FastWrites:*
[SIZE="2"]**echo "options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1" > /etc/modprobe.d/nvidia**[/SIZE]

```

Basically just make a file called */etc/modprobe.d/nvidia* and add the preceding line which forces fastwrites, reboot and you're done. If you want to turn it off again later, either comment out the entire line with a **#** to return to your system's defaults, or change the value of a specific setting from "1" to "0" to disable that feature.

On that note, it may be worth mentioning that on my system side-band addressing was already enabled but fastwrite was disabled on my FX5900XT. In q3a timedemo four, I consistently scored exactly **1 FPS** more than I did without it. So, you can see why this is disabled by default. Not exactly a mind-blowing gain in performance ;) In fact, though this setting normally causes no stability problems, artifacts or otherwise, it did cause X not to start correctly in at least one instance. 

_The bottom line:_ side-band addressing should give a noticable boost in FPS, but fastwrites won't necessarily help at all. Run some tests on your own rig to see if this tweak helps or hurts! 

All the best,
-AT

---

### Post by Omnios on 2006-10-04
Hi hi I moded my nvidia and it only gave me about a 20 frame increase.
 ANyways you might want to look into this benchmark how to.

[http://ubuntuforums.org/showthread.php?t=157429&highlight=benchmark](http://ubuntuforums.org/showthread.php?t=157429&highlight=benchmark)

---

### Post by hype on 2006-10-05
Thx Tseliot.
I noticed better fps on Xgl. Tho its not a "huge" gain. :)

---

### Post by big z on 2006-10-05
i did it and and now my  agp is 2x not 4x like it was how do i fix it?

---

### Post by m1215 on 2007-01-29
i found when trying this guide, i was unable to get fastwrite working. i discovered a setting in the mother board  bios that was disabled for fastwrite. after enabling it i had fastwrite. if anyone is having that problem check your bios settings.
nice guide tseliot, thanks for the info.
tested on asus a7v133 with an nvidia fx5600 ultra card. i gained about 75 fps.

---

### Post by gribelu on 2007-05-07
I'm trying to DISABLE SBA but this guide won't work for me..
So, the system is an AMD64 on VIA KT800 chipset, GF 6600GT AGP and Kubuntu Feisty and nvidia 1.0-9755

```

cat /proc/driver/nvidia/agp/*

Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f000302
Host Bridge:     PCI device 1106:0204
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0x1f000a1b:0x00000b02
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

```

So SBA/FW are supported, FW is Disabled and SBA enabled. I should mention that i also tried this with the NVIDIA AGP driver instead of the default one.

```

cat /proc/driver/nvidia/registry | grep AGP

EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0

```

Judging by the nvidia registry values, SBA should also be disabled. Also, setting these values to 1 doesn't enable FW.. It's pretty clear that they are ignored.

Help? :)

**Edit: **
I found out why the options defined in nvidia-kernel-nkc didn't stick.
I had to comment out the lines in this file

```

cat /etc/modprobe.d/lrm-video
# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

```

Still, the options have no effect on the AGP driver

---

### Post by KEVIN06 on 2007-05-13
I followed the tutorial and fast Write remains desactive. :( 

its did my PC function under edgy. 

supports it [http://paste.ubuntu-nl.org/20586/]("http://paste.ubuntu-nl.org/20586/") ? 

I am feisty with the last drivers of nvidia 

thank you

---

### Post by gribelu on 2007-05-15
I tried everything. It appears that with the latest kernels (?) this trick doesn't work anymore.
Anyone have a workaround? I need to disable SBA as i have stability problems with it on

---

### Post by tseliot on 2007-05-15
Add the following line to your /etc/modprobe.d/nvidia-kernel-nkc :
```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

---

### Post by gribelu on 2007-05-15
you didn't understand my problem :) 

**options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1**

```

$ cat /proc/driver/nvidia/agp/status

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

$ cat /proc/driver/nvidia/registry | grep AGP

EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 1
EnableAGPFW: 1

```

**options nvidia NVreg_EnableAGPSBA=0 NVreg_EnableAGPFW=0**

```

$ cat /proc/driver/nvidia/agp/status

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

$ cat /proc/driver/nvidia/registry | grep AGP

EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0

```

Whatever the EnableAGPSBA and EnableAGPFW values are, FW and SBA stay at the default values.
I think there's a problem in Feisty or the 2.6.20 kernel that makes these options obsolete

As i mentioned earlier, this is also the case with the NVIDIA agp driver. I guess the problem is with the AGPGART from the kernel...

---

### Post by benoitc on 2007-05-20
> **tseliot said:**
> Add the following line to your /etc/modprobe.d/nvidia-kernel-nkc :
```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

It doesn't work with nvidia-glx-new. However it works with nvidia-glx but linux-lowatency require last version of nvidia driver.

---

### Post by thom_raindog on 2007-06-03
So, there is NO way to make SBA and FW work with nvidia-glx-new? That would suck...

---

### Post by edmondt on 2007-06-06
I added the following to my nvidia-kernel-nkc and got much better performance after rebooting, my card is a FX5700 128MB

gksudo gedit /etc/modprobe.d/nvidia-kernel-nkc


options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_EnableBrightnessControl=1 NVreg_DevicesConnected=1 NVreg_VbiosFromROM=1 NVreg_SaveVBios=1 NVreg_SoftEDIDs=0 NVreg_VideoMemoryTypeOverride=0 NVreg_NvAGP=3 NVreg_ReqAGPRate=8 #(8=for 8X AGP, 4=for 4X AGP)

---

### Post by thom_raindog on 2007-06-07
Aha.. and where did you find these things?
Other people posted that EnableAGPSBA=1 and EnableAGPFW=1 did nothing for them.

What does 
```
cat /proc/driver/nvidia/registry
```
show for you?

Edit: 
I did the same thing and none of that seems to have and kind of effect, at least according to /proc/driver/nvidia/registry.
For instance, Enable brightnesscontroll still says "0", just like SaveBios does...

---

### Post by chris_504 on 2007-06-09
> **thom_raindog said:**
> So, there is NO way to make SBA and FW work with nvidia-glx-new? That would suck...

Checked it out myself..dosen't work with the new 'nvidia-glx-new' drivers.

Solution..Anyone?

---

### Post by running4 on 2007-07-04
I followed this guide and was successful under 6.10.

As an unintended side effect, I can now rip a DVD movie 30% faster than before.:)

---

### Post by hardyn on 2007-07-04
does this improve PCI-E at all?

---

### Post by scontin on 2007-08-13
> **chris_504 said:**
> Checked it out myself..dosen't work with the new 'nvidia-glx-new' drivers.

Solution..Anyone?

YES!!!!!!
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc

options nvidia_new NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

IT WORKS!!! Yeah............:popcorn:

---

### Post by Aya Dream on 2007-08-25
Thanks to tseliot for this tip. I can confirm It does work under feisty with nvidia-glx-new as long as you follow scontin's advice:

sudo gedit /etc/modprobe.d/nvidia-kernel-nkc      #and add the line

options nvidia_new NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

The magic bit being _new in the second line after nvidia!

I'm not sure of the impact on fps as it seems to differ according to how much of glxgears is showing on screen. If the graphic is running but hidden by my terminal window then fps goes up to 2828fps; but if I maximize glxgears to full screen then the underlying terminal records 192fps. As has been suggested elsewhere in this thread the real test will be when you actually play the games

But hey, the tip works and I now have Fast Write and Side Band Addressing both fully operational

Thanks

---

### Post by Bart_D on 2007-08-25
Would this improve the performance of Compiz Fusion?  i.e. make it smoother?

---

### Post by jaybombalous on 2007-10-01
In game, fastwrite alone jumped my 6800 GT up 200 - 250 fps. :cool:

---

### Post by sad_iq on 2007-10-02
Works for me(feisty)...more or less with these instructions...I first put [COLOR="Blue"]options nvidia_new NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1[/COLOR] in /etc/modprobe.d/nvidia-kernel-nkc and that didn't work...so I added [COLOR="Blue"]options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1[/COLOR] after the first line and that worked :) However I don't know what driver I'm using (don't remember) and I'm using a custom kernel. Still testing to see if any improvements have been made! Also...glxgears gives me fewer points with agpfast write enabled :(

---

### Post by grndrush on 2008-02-13
Hi! Hoping this thread is still open.

I run Arch Linux. This distro doesn't have an /etc/modprobe.d directory, much less anything in it. Were would I place the options that ubuntu users place in nvidia-kernel-nkc?

Arch does have an /etc/modprobe.conf file; that would be my guess, but that's a bit if a shot-in-the-dark.

Would simply placing:
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
there be adequate?

I haven't been able to find any reference in my installation that looks anything like:
alias char-major-195* nvidia

FWIW: Asus A8V-MX, Athlon64 XP 3500+, GeForce2 MX/400
The latter item, of course, being the main reason I'm trying to squeeze every ounce out!  :)
 
TIA.

---

### Post by itchanddino on 2008-10-31
This file doesn't exist in 8.10 :(

---

### Post by phobos_anomaly on 2009-03-23
Thank you for the howto. after enabling this stuff, my fps went from 

301 frames in 5.0 seconds = 60.170 FPS
301 frames in 5.0 seconds = 60.020 FPS
299 frames in 5.0 seconds = 59.622 FPS

to 

12332 frames in 5.0 seconds = 2466.249 FPS
13163 frames in 5.0 seconds = 2632.540 FPS
13087 frames in 5.0 seconds = 2617.359 FPS


Much appreciated :D

---

### Post by fillintheblanks on 2009-04-07
thanks. I can confirm this worked for me

> **z-vet said:**
> It did not worked for me with /etc/modules, so after reading an article in Gentoo Wiki i just created /etc/modprobe.d/nvidia file and added there:
```

alias char-major-195 nvidia 
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

```
which gives me this:
```
 
cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Enabled
```

---

### Post by fillintheblanks on 2010-10-23
> options **nvidia-current** NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1

finally this worked for me.. I just had to put in **nvidia-current**

Ubuntu 10.10 Nvidia 260.19.06

---

### Post by IPEX-731BA5DD06 on 2011-01-30
None of the solutions worked for me.

AGP is enabled in BIOS :oops:, Initially I had PCI. (doh!!!!)
AGP is supported.
Fastwrite is supported. but NOT enabled
SBA is supported and enabled.

Hyperthreading is enabled in BIOS (this doubles the frame rate)

No option in BIOS for fast write.?? 

nivdia-current/_current or nvidia-new/_new both don't work. NOTE dash - and Underscore _ don't work.

Geforce FX5600 XT 128 MB's 

Direct x 9.0 supported.

Any suggestions appreciated.

---

### Post by cascade9 on 2011-01-30
> **IPEX-731BA5DD06 said:**
> None of the solutions worked for me.

AGP is enabled in BIOS :oops:, Initially I had PCI. (doh!!!!)
AGP is supported.
Fastwrite is supported. but NOT enabled
SBA is supported and enabled.

Hyperthreading is enabled in BIOS (this doubles the frame rate)

No option in BIOS for fast write.?? 

nivdia-current/_current or nvidia-new/_new both don't work. NOTE dash - and Underscore _ don't work.

Geforce FX5600 XT 128 MB's 

Direct x 9.0 supported.

Any suggestions appreciated.

Hyperthreading will NOT double your framerate. 

Not all BIOSes have the option for fast write. 

FX cards dont use nvidia-current, you've got to use nvidia 173.xx drivers.

---

### Post by IPEX-731BA5DD06 on 2011-01-30
nvidia_173.14.22 didn't break anything, or fix.

I guess, fastwrite just isn't an option, even though its supported.

Leave well enough alone, I broke the graphics driver twice, once trying to install a beta driver, 2nd time to make sure I knew what I did.

Thanks for quick reply.

On Hyperthreading, disabling reduced frame rate by 1/2 so sematics. Looks like its just disabled by default for my Video card. Card is only supported by legacy updates.

Guide might be for lower setting Video cards??? (4 yr's old)

No big problem, still a great guide regardless.

---

### Post by cascade9 on 2011-01-31
> **IPEX-731BA5DD06 said:**
> nvidia_173.14.22 didn't break anything, or fix.

I guess, fastwrite just isn't an option, even though its supported.

Leave well enough alone, I broke the graphics driver twice, once trying to install a beta driver, 2nd time to make sure I knew what I did.

If you've borked your nvidia drivers twice already (and I'd assume have tried to install nvidia-current) I'dpurge all the nvidia dirvers and start again.

> **IPEX-731BA5DD06 said:**
> On Hyperthreading, disabling reduced frame rate by 1/2 so sematics. 

What?!?! You actually found something where  turning on hyperthreading will double your framerate? 

That to me says that you've got no 3D driver installed (or it wasnt a 3D program), whatever you were using was light, and very CPU bound.

---

### Post by coolbrook on 2011-07-20
> **fillintheblanks said:**
> finally this worked for me.. I just had to put in **nvidia-current**

Ubuntu 10.10 Nvidia 260.19.06

Excellent.  It not only accepted the FW and SBA, but it also acknowledges 4x capability instead of just 2x.

Lucid 10.04.3, Nvidia 275.19

---

### Post by cosimo321 on 2013-09-02
Hello,
 Ok, none of these options worked here. I am on ubuntu 13.04 nvidia driver 308.
I have several clients that still have agp nvidia cards. On previous versions of Ubuntu, these instructions worked.
Any help would be appreciated

coz

---

