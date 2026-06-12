---
title: "HTPC Nvidia screen resolution."
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kimme on 2012-04-17
How can I get the correct screen resolution for my HTPC? There's no 16x9 (1440x900). Now my screen looks like an picture that's missing all the edges of the screen.

btw; I have installed The latest Precise beta with nvidia-current screen settings.

---

### Post by effenberg0x0 on 2012-04-17
> **kimme said:**
> How can I get the correct screen resolution for my HTPC? There's no 16x9 (1440x900). Now my screen looks like an picture that's missing all the edges of the screen.

btw; I have installed The latest Precise beta with nvidia-current screen settings.

You mean this resolution is not available in Dash / Settings / Display and also not available at dash/nvidia-settings/XServer Display Configuration? I find it odd, but you could probably write your own /etc/X11/xorg.conf to try the resolution you need.

Question: Was this monitor connected to this PC when it booted? It should be able to recognize a native resolution.

Also, if you're using XBMC, you can set the resolution in it's menus, on System / Video I think. (Display Mode). It uses xrandr at boot to detect usable resolutions and they are saved at ~/.xbmc/userdata/guisettings.xml
Regards,
Effenberg

---

### Post by fabricator4 on 2012-04-17
> **kimme said:**
> How can I get the correct screen resolution for my HTPC? There's no 16x9 (1440x900). Now my screen looks like an picture that's missing all the edges of the screen.

btw; I have installed The latest Precise beta with nvidia-current screen settings.

What resolutions are available?  The terminal command
```
xrandr
```
should list all of the available modes.

You could try install nvidia settings and see if that works better for you:

```
sudo apt-get install nvidia-settings
```

To run it open the dash and find "nvidia X server settings"

If this doesn't work it may mean there's a problem recognising the display.  What monitor and what type of hookup do you have?

Chris

---

### Post by kimme on 2012-04-17
I use my Sony Bravia 32" LCD screen and om my HTPC it only gives out these xrandr ressolutions..


```
kimme@HTPC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0     52.0  
   1360x768       53.0  
   1280x720       54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0  
   800x512        71.0  
   720x576        72.0     73.0  
   720x480        74.0     75.0  
   720x450        76.0  
   720x400        77.0  
   700x525        78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0     92.0  
   640x400        93.0  
   640x350        94.0  
   576x432        95.0     96.0     97.0     98.0     99.0    100.0    101.0  
   512x384       102.0    103.0    104.0    105.0    106.0  
   416x312       107.0  
   400x300       108.0    109.0    110.0    111.0    112.0  
   360x200       113.0  
   320x240       114.0    115.0    116.0    117.0  
   320x200       118.0  
   320x175       119.0  
kimme@HTPC:~$ 
```

And this TV is connected with an HDMI cable not directly at the TV, but through an box I purchased at dealextreme.com that gives me an additional 3 HDMI ports as my TV only has one.

How do I modify my xorg.config file so my TV can use all the same resolutions my desktop Ubuntu has, 'cause there it has all these resolutions...

```
kimme@ubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0     51.0* 
   1600x1024      52.0  
   1440x900       53.0  
   1400x1050      54.0     55.0  
   1360x768       56.0     57.0  
   1280x1024      58.0     59.0  
   1280x960       60.0  
   1152x864       61.0     62.0     63.0     64.0     65.0     66.0     67.0  
   1024x768       68.0     69.0     70.0     71.0     72.0     73.0  
   960x720        74.0  
   960x600        75.0  
   960x540        76.0  
   928x696        77.0     78.0  
   896x672        79.0     80.0  
   840x525        81.0     82.0     83.0     84.0     85.0  
   832x624        86.0  
   800x600        87.0     88.0     89.0     90.0     91.0     92.0     93.0     94.0     95.0     96.0  
   800x512        97.0  
   720x450        98.0  
   720x400        99.0  
   700x525       100.0    101.0    102.0    103.0  
   680x384       104.0    105.0  
   640x512       106.0    107.0    108.0  
   640x480       109.0    110.0    111.0    112.0    113.0    114.0    115.0    116.0  
   640x400       117.0  
   640x350       118.0  
   576x432       119.0    120.0    121.0    122.0    123.0    124.0    125.0  
   512x384       126.0    127.0    128.0    129.0    130.0  
   416x312       131.0  
   400x300       132.0    133.0    134.0    135.0    136.0  
   360x200       137.0  
   320x240       138.0    139.0    140.0    141.0  
   320x200       142.0  
   320x175       143.0  
kimme@ubuntu:~$ 


```

Thanks in advance..

UPDATE: I can  rule out that the HDMI box is the culprit as it soesn't show all the avalable resolutions still without the dealextreme HDMI switcher. It still doesn't give me all the resolutions I had before the Oneiric update ****** it all up. :(

---

### Post by Erlander on 2012-04-17
If you updated as the last post indicates then I would try a clean install.  I've had similar problems with a GT8600 card connected to a Samsung TV via a dvi to hdmi cable.

A clean install fixed mine on 11.10

---

### Post by kimme on 2012-04-18
I first updated, and that didn't work I did an clean install with the /home directory on an another partition. But it still eludes the screen resolutions. :(

---

### Post by kimme on 2012-04-18
Does anybody know why my Sony Bravia TV doesn't get the correct 16x9 resolutions at all? I'm getting desperate here to get my HTPC working again before the damn nvidia bug crept up in my HTPC and it was working perfect...

---

### Post by fabricator4 on 2012-04-18
> **kimme said:**
> I use my Sony Bravia 32" LCD screen and om my HTPC it only gives out these xrandr ressolutions..


UPDATE: I can  rule out that the HDMI box is the culprit as it soesn't show all the avalable resolutions still without the dealextreme HDMI switcher. It still doesn't give me all the resolutions I had before the Oneiric update ****** it all up. :(

I would still try installing and using nvidia-settings.  When you make changes in nvidia x server settings and save, it writes the xorg.conf

Chris

---

### Post by kimme on 2012-04-18
I have done that and  it still doesn't pick up the correct resolutions at all. if it only would display 1440x900 then I'll be happy, but it doesn't do that.

---

### Post by cariboo on 2012-04-18
Have you tried connecting directly to the TV without going through the device? I have a problem with monitors not being detected properly when running through a KVM, this could be a similar problem.

---

### Post by kimme on 2012-04-18
When I boot up my install disk on my USB stick, I tried to test the Ubuntu desktop from my stick, and there the Ubuntu desktop only recognized my TV as an 7" Sony monitor.... That's where the problem lies..

I shall try to install the Ubuntu with my TV connected directly first, and will give my result ASAP.

Edit: Nope, it still detects my Sony Bravia 32" TV as an 7" Sony monitor/TV with the resolution 1280x720 (16x9) with the edges outside the display.... :(

---

### Post by cariboo on 2012-04-18
Have you tried:

```
sudo nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf, that may solve your problem.

---

### Post by kimme on 2012-04-18
I've tried your solution, but it still won't make my preffered 1440x900 screenmode available for me to select, it still gives out this xrandr output.

This was done with the HTPC plugged directly to the Sony Bravia 32" TV, without the KVM box as suggested.

```
kimme@HTPC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0     52.0  
   1360x768       53.0  
   1280x720       54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0  
   800x512        71.0  
   720x576        72.0     73.0  
   720x480        74.0     75.0  
   720x450        76.0  
   720x400        77.0  
   700x525        78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0     92.0  
   640x400        93.0  
   640x350        94.0  
   576x432        95.0     96.0     97.0     98.0     99.0    100.0    101.0  
   512x384       102.0    103.0    104.0    105.0    106.0  
   416x312       107.0  
   400x300       108.0    109.0    110.0    111.0    112.0  
   360x200       113.0  
   320x240       114.0    115.0    116.0    117.0  
   320x200       118.0  
   320x175       119.0  
kimme@HTPC:~$
```

---

### Post by kimme on 2012-04-18
The brand on my TV is...

Sony Bravia KLV-S32A10E if that's any help and as I purchased it some years ago, it's not listed on Sony's homepage.

---

### Post by fabricator4 on 2012-04-18
> **kimme said:**
> I have done that and  it still doesn't pick up the correct resolutions at all. if it only would display 1440x900 then I'll be happy, but it doesn't do that.

OK, run nvidia settings and save the results (so it generates xorg.conf)

Next, in a terminal run
```
cvt 1140 900

#and it will give a result something like:
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

open up /etc/X11/xorg.conf as superuser and add the modeline and mode to it.  Log out and back in again, then run nvidia-settings again and see if the mode has been added.

Chris

---

### Post by Erlander on 2012-04-18
In the code don't you mean "cvt **[COLOR="Red"]1440[/COLOR]** 900"

---

### Post by kimme on 2012-04-19
I did run "sudo nvidia-xconfig" as you stated, and later the command "cvt 1440 900" (You didn't mean cvt 1140 900, right) and where in '/etc/X11/xorg.conf' shall I put the new mode it gave me?

```
kimme@HTPC:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

In '/etc/X11/xorg.conf'? And where in '/etc/X11/xorg.conf'?


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Thu Apr  5 22:33:07 PDT 2012

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@zirconium)  Fri Mar 30 13:43:34 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       14.0 - 46.0
    VertRefresh     47.0 - 61.0
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kimme on 2012-04-19
I added the modeline as suggested, but the resolution isn't there yet after an reboot.... :(


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Thu Apr  5 22:33:07 PDT 2012

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@zirconium)  Fri Mar 30 13:43:34 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       14.0 - 46.0
    VertRefresh     47.0 - 61.0
    # 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
    Modeline       "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by fabricator4 on 2012-04-19
> **Erlander said:**
> In the code don't you mean "cvt **[COLOR="Red"]1440[/COLOR]** 900"

Indeed I did.  I wrote that quickly during my lunch break today and didn't have time to proof read.

Thanks

Chris

---

### Post by fabricator4 on 2012-04-19
> **kimme said:**
> I added the modeline as suggested, but the resolution isn't there yet after an reboot.... :( 

Try this:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Thu Apr  5 22:33:07 PDT 2012

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@zirconium)  Fri Mar 30 13:43:34 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       14.0 - 46.0
    VertRefresh     47.0 - 61.0
    Modeline       "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
#   Option         "metamodes" "nvidia-auto-select +0+0"
    Option	   "metamodes" "1140x900_60.00"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

The difference between this and the original you posted is I added the Modeline to the "Monitor" (edited) section, and in the "Screen" section I commented out the "metamodes" auto select mode and added the select mode for the 1440x900 modeline instead.

I did it this way because that is what nvidia-settings does when I select the correct resolution and save it.

The HorizSync and VertRefresh values look quite low.  You might want to check them against the manual for your screen and set them appropriately if necessary.

Chris

---

### Post by kimme on 2012-04-19
> **fabricator4 said:**
> 
    Modeline       "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
    
#   Option         "metamodes" "nvidia-auto-select +0+0"
    Option	   "metamodes" "1140x900_65.00"
    [/CODE]

The difference between this and the original you posted is I added the Modeline to the "Monitor" (edited) section, and in the "Screen" section I commented out the "metamodes" auto select mode and added the select mode for the 1440x900 modeline instead.

I did it this way because that is what nvidia-settings does when I select the correct resolution and save it.

The HorizSync and VertRefresh values look quite low.  You might want to check them against the manual for your screen and set them appropriately if necessary.

Chris

Shouldn't the line "Option	   "metamodes" "1140x900_65.00" actually say 60.00 at the end, and I have misplaced the manual for the TV sometime ago already, so I have to search the web for an online manual, but thanks to Sony it's removed from their site...

---

### Post by fabricator4 on 2012-04-19
> **kimme said:**
> Shouldn't the line "Option	   "metamodes" "1140x900_65.00" actually say 60.00 at the end, and I have misplaced the manual for the TV sometime ago already, so I have to search the web for an online manual, but thanks to Sony it's removed from their site...

Yes it should, I've fixed it.  Sorry it's been a looong day.

I know on some monitors when you enter the setup menu from the front panel there's often an information screen which can have important stuff like ideal resolution, sync ranges and Horizontal refresh timings.  Worth a look?

Chris

---

### Post by kimme on 2012-04-19
New update. I have tried with both the 65.00 ending and the 60.00 ending to the modeset twith no luck. The resolution 1440x900 doesn't show it in nvidia-config or the Display settings... :(

---

### Post by fabricator4 on 2012-04-19
> **kimme said:**
> New update. I have tried with both the 65.00 ending and the 60.00 ending to the modeset twith no luck. The resolution 1440x900 doesn't show it in nvidia-config or the Display settings... :(

65.00 is definitely wrong: it won't mean anything in that context.

Definitely investigate the correct HorizSync settings as I think it needs to be at least 55kHz to give the resolution you want at 60Hz Refresh rate.

(Maybe just change it to 57 or something if you can't find the manual to verify it.  Check the setup menus on the monitor as well, remember.

Chris

---

### Post by kimme on 2012-04-20
It's funny that this actually worked with the 11.04 version, until nvidia released the driver that ****** it up, and now when I install 11.04 again, it gets the updated nvidia driver that ***** it up..... :(

---

