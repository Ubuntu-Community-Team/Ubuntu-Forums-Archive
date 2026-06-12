---
title: "Beryl keeps freezing."
date: 2007-01-08
forum: The Cafe
---

### Post by RussianVodka on 2007-01-08
It works just fine, and then boom, it freezes. As in, I can still move the mouse, but I can't click on anything, and CTRL+ALT+Backspace does nothing. This happens about every half an normaly, but if I have  "blur" on, it happens about 5 seconds after it's enabled.

Why is this happening? Is this a known bug? There seems to be nothing wrong with my drivers.

Here are the details:

OS: Edgy
Beryl Version: 0.1.4 (Installed manually using Beryl Wiki)
GPU: GeForce Go 7600
GPU Driver: 1.0-8776 (Installed using Automatix2)

And here is my xorg.conf file:
```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load	   "dri"
    Load 	   "dbe"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
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
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option 	   "AddARGBGLXVisuals" 		"true"
    Option	   "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Also, it should be noted that I first installed Beryl using Automatix2 Bleeder, but then since it gave me version 0.1.2 I removed it (used Automatix's uninstall function) and installed 0.1.4 manually. So maybe the old version wasn't removed properly.

---

### Post by arnieboy on 2007-01-08
Use envy to install the latest driver for your nvidia card. That will fix this issue.
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb)

---

### Post by RussianVodka on 2007-01-08
> **arnieboy said:**
> Use envy to install the latest driver for your nvidia card. That will fix this issue.
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb)

Thanks! 

But I have another problem now. I accidentally enabled blur again, so now my system freezes when ever beryl starts. The problem, is that "beryl-manager" is one of my startup scripts. So I can't start Gnome without starting Beryl. 

So I try Failsafe Gnome, and it also crashes. Failsafe terminal works just fine though. So I log into that, use vim to access the settings file in ~/.beryl, but there are only options to various effects of blur, no option to turn it on and off. Also, I can't find the place in which stores the startup scripts so I can remove the one that starts beryl.

---

### Post by arnieboy on 2007-01-08
try
```
rm -f ~/.config/autostart/beryl-manager.desktop
```

---

### Post by RussianVodka on 2007-01-08
Ok, I can now boot into Gnome.

But when I run envy, it asks me if I want to install or uninstall nvidia drivers. No matter which I click, it turns off the DE, and I'm stuck with a black screen with a blinking underscore in the top left.

Is this supposed to happen? Maybe I should first use automatix to uninstall the nVidia drivers? Or do I need to run the script in the failsafe terminal?

---

### Post by arnieboy on 2007-01-08
> **RussianVodka said:**
> Ok, I can now boot into Gnome.

But when I run envy, it asks me if I want to install or uninstall nvidia drivers. No matter which I click, it turns off the DE, and I'm stuck with a black screen with a blinking underscore in the top left.

Is this supposed to happen? Maybe I should first use automatix to uninstall the nVidia drivers? Or do I need to run the script in the failsafe terminal?
do the following:
```
sudo apt-get remove nvidia-glx
```
and change "**nvidia**" to "**nv**" under Section "Devices" in **/etc/X11/xorg.conf**
save the file and restart your computer and after logging into Gnome, run Envy.

---

### Post by RussianVodka on 2007-01-08
Never mind. It worked just fine. Turns out I had to wait a bit, then it told me that all background processes were shut off. Then I ran envy and it worked.

Now everything works as far as graphics. But for some reason my sound stopped working. Any idea on how to fix that?

---

### Post by arnieboy on 2007-01-08
> **RussianVodka said:**
> Never mind. It worked just fine. Turns out I had to wait a bit, then it told me that all background processes were shut off. Then I ran envy and it worked.

Now everything works as far as graphics. But for some reason my sound stopped working. Any idea on how to fix that?
first make sure your sound card is working (easy way to do that is to play any random music file) and check if a sound card error is reported or not. If thats not the case, and the file seems to be progressing just fine with no audio output, run alsamixer and make sure nothing is muted.

---

### Post by RussianVodka on 2007-01-08
> **arnieboy said:**
> first make sure your sound card is working (easy way to do that is to play any random music file) and check if a sound card error is reported or not. If thats not the case, and the file seems to be progressing just fine with no audio output, run alsamixer and make sure nothing is muted.

You sir, are god.

---

### Post by fiftynine on 2007-05-26
> **RussianVodka said:**
> It works just fine, and then boom, it freezes. As in, I can still move the mouse, but I can't click on anything, and CTRL+ALT+Backspace does nothing. This happens about every half an normaly, but if I have  "blur" on, it happens about 5 seconds after it's enabled.


Up. I'm getting same problem, except my graphic card is ati radeon x850xt. Beryl works fine for a hour or a day, but then it snaps: I can't do anything other than move my mouse pointer. Keyboard shortcuts dont work or anything.

```
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
EndSection

        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI RADEON X850XT"
        Driver          "ati"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "SAMSUNG SYNCMASTER 225BW"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI RADEON X850XT"
        Monitor         "SAMSUNG SYNCMASTER 225BW"
        DefaultDepth    24
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

Yep. Does anyone else have this problem? Or better yet, would someone know how to fix this?

edit: Hmm. Why this thread is in community cafe.. :-s

---

