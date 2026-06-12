---
title: "xorg conf file ignored"
date: 2017-02-20
forum: Ubuntu/Debian BASED
---

### Post by bil-94 on 2017-02-20
Hello everyone, I'm going to go straight to the point. I've been  battling this annoyance for an entire weekend without results, sadly,  the distro I'm using isn't exactly an "Ubuntu" one, (well, It's  Tahrpup-6.0.5 which is based on ubuntu but whatever). And yet, I thin it  still applies by the fact that it's an issue with the freaking Xorg and  Nvidia drivers.
Here's my info:

Kernel:
3.14.54
Distro:
Tahrpup-6.0.5
Xorg Version:
1.15.1
Nvidia Drivers Version:
352.79
VGA controller:
 NVIDIA Corporation GF108 [GeForce GT 620] [10de:0f01] (rev a1) (2GB VRAM)
Screen:
SAMSUNG T24C550 via VGA cable.

Next, here's the lastest LOG from Xorg:
[http://pastebin.com/CjRkcHx3](http://pastebin.com/CjRkcHx3)
Here's my lastest conf file xorg:
[http://pastebin.com/1rGWJUDk](http://pastebin.com/1rGWJUDk)
Here's my ls of X11:
[HTML]app-defaults
FAKE.ck
ja_JP.eucJP
ja_JP.UTF-8
LORXCONFI.NVIDIA
xkb
xorg.conf
xorg.conf.
xorg.conf.NVIDIA
xorg.conf.nvidia-xconfig-original
xorg.safefile2
xsafeorg.co2
Xsession.d[/HTML]

Here's my xrandr output:
[HTML]Screen 0: minimum 8 x 8, current 1024 x 768, maximum 16384 x 16384
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   832x624        74.6  
   800x600        75.0     72.2     60.3  
   680x384        60.0     59.8  
   640x480        75.0     72.8     59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        72.8     60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)[/HTML]

So, with that said (and I hope I didn't forgot anything, please let me know), here's my issue.

[LIST]
[*]I'm using a monitor that **supports** 1080p screen resolution on **windows**,  via the same VGA cable. My HDD died a few days ago, so I'm using puppy  in a flash drive that loads on RAM, no cash for new drive **actually I live in a country that's slowing going to blow up, so economy wise I won't buy a HDD.** 
[*]1080p **works** with this distro, and screen,  I've tested that by manually changing to it via the nvidia-settings, so  the monitor can handle that resolution. 
[*]*Every time I reboot or even restart the graphic server*, the screen resolution **defaults to a totally distorted 1024x768** res. 
[*]My EDID for this monitor is **broken**, no idea why, even the HDMI is broken and no, can't replace it by the same reason stated before. 
[*]The Nvidia-settings can't read EDID, nor can do the "get-edid" software. 
[*]The xorg config tells the device to **ignore EDID**, but yet the log says otherwise. 
[*]If I erase the xorg.conf file and let the xorgwizard to create a default one, the nvidia-settings display much more modes than the ones that xrandr here displays. 
[*]There's no ~/config/.display* file 
[/LIST]

So, my main issue is that there's no way to create persistent changes on the xorg.conf, even if they are stated on the conf file, they seem to be ignored and xorg uses who knows what config file to parse into the driver, some of that can be seen on the log file, around line 177.

I don't know if I'm missing anything important to tell you, **please let me know**, I just want to use my 1080 screen :(
Thanks, I'm sure you guys can help me.

---

### Post by howefield on 2017-02-20
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by bil-94 on 2017-02-20
> **howefield said:**
> Thread moved to the "*Ubuntu/Debian BASED*" forum.

Ah, I see, sorry for the mistake.

---

