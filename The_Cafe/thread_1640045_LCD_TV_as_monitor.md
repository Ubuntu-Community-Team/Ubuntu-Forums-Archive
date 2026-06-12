---
title: "LCD TV as monitor"
date: 2010-12-07
forum: The Cafe
---

### Post by capink on 2010-12-07
I have an old PC that I want to transform into a media center mainly for watching and recording TV shows.

Can I just plug my VGA connection into the LCD TV (I plan on buying one with VGA input) and use it as the sole monitor.

I want to avoid the whole dual monitor, TV out thing and fiddling with xorg config.


Have anyone had experiences with doing this? and would it work with any LCD TV? (I am planning on buying a Samsung 42 inches).



Edit: My graphic card is ATI x300. Anyone have experiences with it?

---

### Post by Zzl1xndd on 2010-12-07
I presently do this with a Mac Mini and haven't had any issues.

---

### Post by capink on 2010-12-07
Do you use VGA? did it involve any editing of xorg.config

---

### Post by sydbat on 2010-12-07
> **capink said:**
> I have an old PC that I want to transform into a media center mainly for watching and recording TV shows.

Can I just plug my VGA connection into the LCD TV (I plan on buying one with VGA input) and use it as the sole monitor.Yes.

> I want to avoid the whole dual monitor, TV out thing and fiddling with xorg config.No need for "dual monitors" or "fiddling with xorg config".


> Have anyone had experiences with doing this? and would it work with any LCD TV? (I am planning on buying a Samsung 42 inches).I have one of my boxen (10.04 64bit w/XBMC) connected via HDMI to our 46" Sharp LCD. Only problem I have with that setup is 5.1 sound through the HDMI cable. Stereo (PCM) sound works fine. Still working on it.

---

### Post by Paqman on 2010-12-07
Yep, just plug it in. The only real difference between a TV and a monitor these days is the tuner.

---

### Post by Bölvaður on 2010-12-07
I dont see how you can have a problem with dual monitors if you only will have one.

At the moment there is a computer like this in my livingroom connected to a big lcd monitor... it's just the same as any other monitor so there shouldnt be any difference.

---

### Post by dozycat on 2010-12-07
I use a LG vga input with one asus 1000 HE, ubuntu desktop 10.04
It woks great.

---

### Post by Zzl1xndd on 2010-12-07
> **capink said:**
> Do you use VGA? did it involve any editing of xorg.config

Yes I used VGA, No I didn't have to configure at all.

---

### Post by andymorton on 2010-12-07
My girlfriend does the same thing with her desktop. It works without any issues at all. 

andy

---

### Post by Donalt2010 on 2010-12-07
I've also used my laptop on my tv in the living room for watching movies via hdmi, just have to change a few settings in the ATI Catalyst preferences and also on my sound card to hdmi output and works a treat:)

---

### Post by samalex on 2010-12-07
Yup, works great :)  We have an 42" LG 1080p TV that my Ubuntu 10.04 laptop works great with via VGA.  I've had some problems getting HDMI to work, and I don't think audio over HDMI is working just yet, but VGA works like a champ.

---

### Post by cariboo on 2010-12-07
I've got an early atom powered system with vga out only, and only 1 pci slot. I've got it connected to My Samsung 32" LCD, it runs runs at native resolution of 1360X768 with zero problems, no setup was needed. I'd love to find a good quality low profile nvidia based pci graphics card with HDMI out.

---

### Post by blueturtl on 2010-12-07
Word of warning about d-sub or vga connector you plan on using. In my case I found out that the LCD would not accept a signal it's native resolution through that connector. Why that is, I have no idea, but using HDMI solved that issue.

Could get 1280x768 tops from d-sub, 1368x768 from HDMI.

---

### Post by cariboo on 2010-12-07
I was talking about the native resolution of the TV, check what the manufacturers specs are for VGA. I have a 32" Samsung and a 40" Toshiba, their  native resolution on VGA is the same, 1368X768. On HDMI  it's 1920X1080, We tried it with my main system which has HDMI out.

---

### Post by Aquix on 2010-12-08
I have used a 42 lcd tv as a monitor for years now at it's brilliant.  Haven't bothered with hdmi so it's connected with vga and thats plug'n'play.

Two things is nice to use though. Darker ubuntu themes and darker scripts for stylish in firefox because the eyes can burn with all that white after a while. Another thing is that text becomes very large so I use Firegestures in firefox to zoom in and out on the page, there are many options but I use the mousewheel while holding down the right mousekey. Also use it to reset page zoom and close/next/previous  tabs. 

 :popcorn:  for every youtube video is also required  :D

---

### Post by Johnsie on 2010-12-08
I do it at home... I installed Boxee on it and it works great. 
[http://boxee.tv](http://boxee.tv)

My boxee repository is boxee.freebc.co.uk

---

### Post by grahammechanical on 2010-12-08
I am using a DTV/monitor with DVi imput. I have used it with VGA but not HDMI. The Operating system detects which method is being used to connect to the monitor and it just works. I do not have to change configuration files. I sure that if I plug in HDMI it would work from the next boot.

VGA was designed for CRT monitors. A digital to analogue conversion was needed to use CRT monitors. They are analogue devices. LCD monitors are digital devices so if you are using VGA to connect to a digital monitor then the signal is being converted from digital to analogue before it leaves the computer and converted from analogue to digital after it arrives in the monitor. 

This processing is not necessary with a digital monitor and so we have DVI and HMDI connectors. Some are of the opinion that signal quality is effected by the conversion processes when using VGA with a digital monitor. I researched this when I needed replace my old CRT monitor.

A big thank you to all the developers who are keeping Linux up with hardware developments.

Regards.

---

### Post by mcduck on 2010-12-08
> **cariboo907 said:**
> I was talking about the native resolution of the TV, check what the manufacturers specs are for VGA. I have a 32" Samsung and a 40" Toshiba, their  native resolution on VGA is the same, 1368X768. On HDMI  it's 1920X1080, We tried it with my main system which has HDMI out.

Usually when talking about "native resolution" people mean the actual, physical resolution of the display panel. So it doesn't depend on what connection you use.

Anyway, if your TV supports Full-HD, it's most likely a 1920x1080 panel, and if it's a "HD-Ready" then the panel is almost always 1366x768 (a resolution that requires a bit of tweaking on the computer's side, while using 1360x768 instead should work automatically and the 6-pixel wide black area really isn't noticeable)

The problem with relying on HDMI data for this purpose is that TV's tend to report the max resolution they can accept, not the best resolution (the one closest to the panel's native resolution). For example my TV accepts 1920x1080 through HDMI, but that wouldn't give a good picture on computer use as the TV would just have to scale it down to the panel's actual resolution. Fine for movies, perhaps, but definitely not for desktop graphics and text.

I pretty much have to use D-Sub connection as my TV doesn't accept anything else than standard HDTV resolutions through HDMI, while D-Sub allows me to use the native resolution. (on a full-HD display this of course wouldn't be a problem, as their native resolution usually really is the same 1920x1080 that 1080p HDTV uses)

---

### Post by capink on 2010-12-08
Thanks for everyone who contributed in this thread.

---

