---
title: "VGA and 1920x1080 resolution"
date: 2011-12-17
forum: The Cafe
---

### Post by donniezazen on 2011-12-17
I have been unable to get a full resolution on my new Westinhouse 42" TV (1920x1080) through vga. I have tried two different laptops and both windows and Ubuntu. Do you run a similar setup? Is it possible to get 1920x1080 resolution on a TV through VGA?

This should have been asked multiple times and belongs more to hardware section. I just want to know if other people are running a similar setup and i need to configure it properly. Their are several threads on different forums but i can't seem to find decisive answer. 

Thanks.

---

### Post by Lucradia on 2011-12-17
It's dependent on the specific publisher (PNY, XFX, etc.) to support 1080i via VGA by default. In linux, however, you can force your display to try and set it to 1920x1080 via the xorg override.

In windows, you can't do this. If it doesn't support it hardware-wise, it won't even show up in the "Manual Resolution" part of your graphics card's CP.

You can try to see if this still works in ubuntu: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

VGA also has a nasty habit of overscanning / underscanning on certain Televisions that are low in inches but can support up to 1080i full. If this happens, it's unlikely you'll be able to keep the resolution long.

---

### Post by donniezazen on 2011-12-17
> **Lucradia said:**
> It's dependent on the specific publisher (PNY, XFX, etc.) to support 1080i via VGA by default. In linux, however, you can force your display to try and set it to 1920x1080 via the xorg override.

In windows, you can't do this. If it doesn't support it hardware-wise, it won't even show up in the "Manual Resolution" part of your graphics card's CP.

You can try to see if this still works in ubuntu: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

VGA also has a nasty habit of overscanning / underscanning on certain Televisions that are low in inches but can support up to 1080i full. If this happens, it's unlikely you'll be able to keep the resolution long.

What do you mean by publishers? the graphic card or the TV. My 42" TV's native resolution is 1920x1080. I have one Nvidia GeForce Go 7300, Intel HD3000 and Nvidia NVS4200.

I contacted Westinghouse and they said TV will support whatever the source transmit. I had a 23" monitor and used Nvidia GeForce Go 7300 to project at 2048x1152. I don't know why would it not project 1920x1080 on the TV. On another laptop with HDMI works fine but i don't have HDMI on my laptop. And analog to digital conversion is a bitch.

Thanks.

---

### Post by blueturtl on 2011-12-17
There is always the possibility that the TV doesn't support that resolution thru VGA. Our panel has a native resolution of 1368x768, but only allows for 1280x768 thru VGA. For full resolution we have to use HDMI. Before wasting a lot of time and banging your head on the wall I suggest you see the manual for supported resolutions...

---

### Post by LowSky on 2011-12-17
Through VGA my 37" HDTV only supports 1366x768, if I use HDMI I can get 1920x1080 but the type is way too small Its only 1080i not 1080P too so that could be a issue as well), so I have to go down to 1360x720 (I think thats it).

You might be seeing the same problem.

---

### Post by cariboo on 2011-12-17
> **LowSky said:**
> Through VGA my 37" HDTV only supports 1366x768, if I use HDMI I can get 1920x1080 but the type is way too small Its only 1080i not 1080P too so that could be a issue as well), so I have to go down to 1360x720 (I think thats it).

You might be seeing the same problem.

I agree with what LowSky said, I have a Samsung 32" and a Toshiba 40" native VGA resolution on both tvs is 1368X768. The Samsung being older old does 1080i, but the Toshiba does 1080p with no problem. I get 1920X1080 resolution on both sets using HDMI.

The system I have connected is an early Intel Atom motherboard, with one PCI, not PCI-e slot, I have an EVGA 6250le graphics card installed, and I use a DVI to HDMI conversion cable.

---

### Post by szymon_g on 2011-12-17
i had no problem running 1920x1200 connected via old analog vga-cable with nvidia 9800 card
are you sure you card/chipset supports your resolution?

---

### Post by doorknob60 on 2011-12-17
On my 32" Sony TV (720p native, but displays 1080p sources fine), I can get 1080p if I use HDMI, but with VGA the maximum is 1360x768 (probably for the better, it's hard to read the text when I set it to 1080p anyways). I think it's dependant on how the TV identifies itself through the VGA input, which is not always the same as with HDMI. Depends on the TV I guess, but you might be able to try to force it into 1080 with editing the xorg.conf file or using some advanced xrandr options, but that may or may not work.

---

### Post by inobe on 2011-12-17
you need a vga to hdmi scaler unit to get full 1080 res.


edit: [http://www.amazon.com/LinkStyle-1080P-Converter-Adapter-3-5mm/dp/B005Z7Y46E](http://www.amazon.com/LinkStyle-1080P-Converter-Adapter-3-5mm/dp/B005Z7Y46E)

---

### Post by donniezazen on 2011-12-17
TV manual does not specifically mention PC VGA resolution. It does mention that component support up to 1080i and HDMI supports up to  1080p.

Their is no HDMI or DVI, so, i am stuck with analog.

Converter might work but reviews are not so appealing.

Does PC graphic card restricts the resolution?

---

### Post by doorknob60 on 2011-12-17
> **donniezazen said:**
> TV manual does not specifically mention PC VGA resolution. It does mention that component support up to 1080i and HDMI supports up to  1080p.

Their is no HDMI or DVI, so, i am stuck with analog.

Converter might work but reviews are not so appealing.

Does PC graphic card restricts the resolution?

Graphics cards do have maximum resolutions, but it's usually very high (for example, my GT 430's max res is 2560 x 1600). The graphics card probably isn't the issue here, it's the [EDID]("https://en.wikipedia.org/wiki/Extended_display_identification_data") data provided by the TV when plugged into the VGA port. Basically, you have to tell the graphics card to ignore the EDID to force a new resolution. This may or may not work, but it's worth a shot: [https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions)

---

### Post by blueturtl on 2011-12-18
I think there were a few instances in the recent past with Intel drivers where the drivers were what created the problem, essentially they couldn't adjust to atypical resolutions (ie. 1360x768 vs. 1366x768 vs. 1368x768 ). No modern ATi or nVidia card would have that problem though, even with the OSS drivers.

Based on how you're getting a lower resolution through component than HDMI (1080i vs 1080p) I'd say there's a good chance your TV has a resolution cap on the VGA input as well.

edit:

I was for example (playing with xrandr) able to finally force 1360x768 thru the VGA, but the picture was misaligned and fuzzy compared to the lower working resolution, so eventually I just gave up on it.

---

### Post by donniezazen on 2011-12-21
> **blueturtl said:**
> I think there were a few instances in the recent past with Intel drivers where the drivers were what created the problem, essentially they couldn't adjust to atypical resolutions (ie. 1360x768 vs. 1366x768 vs. 1368x768 ). No modern ATi or nVidia card would have that problem though, even with the OSS drivers.

Based on how you're getting a lower resolution through component than HDMI (1080i vs 1080p) I'd say there's a good chance your TV has a resolution cap on the VGA input as well.

edit:

I was for example (playing with xrandr) able to finally force 1360x768 thru the VGA, but the picture was misaligned and fuzzy compared to the lower working resolution, so eventually I just gave up on it.

I just want to get a decent resolution something like 1280x800 which is my laptop's native resolution will do. I am not sure if converter will help, ultimately it is converting vga signal which is capped at lower resolution.

---

### Post by cariboo on 2011-12-21
> **donniezazen said:**
> I just want to get a decent resolution something like 1280x800 which is my laptop's native resolution will do. I am not sure if converter will help, ultimately it is converting vga signal which is capped at lower resolution.

You should be able to get at least 1360X768 resolution. You may have to change the picture setting in the TV menu to just scan. This should fix any under or over scanning you are experiencing.

---

### Post by mips on 2011-12-22
> **donniezazen said:**
> I have been unable to get a full resolution on my new **Westinhouse 42" TV**...

What is the EXACT model of the tv?

---

### Post by donniezazen on 2011-12-22
> **cariboo907 said:**
> You should be able to get at least 1360X768 resolution. You may have to change the picture setting in the TV menu to just scan. This should fix any under or over scanning you are experiencing.

What do you mean by scanning?

> **mips said:**
> What is the EXACT model of the tv?

Westinghouse 42" Class LED-LCD 1080p 120Hz HDTV LD-4258.

---

### Post by inobe on 2011-12-22
> **donniezazen said:**
> 
Westinghouse 42" Class LED-LCD 1080p 120Hz HDTV LD-4258.

very nice set:)

---

### Post by mips on 2011-12-22
> **donniezazen said:**
> 
Westinghouse 42" Class LED-LCD 1080p 120Hz HDTV LD-4258.

According to their website [http://westinghousedigital.com/products/led/42-55/ld4258/](http://westinghousedigital.com/products/led/42-55/ld4258/)

> **Compatible Modes**
TV Tuner*: NTSC/ATSC
Component: 480i, 480p, 720p, 1080i
HDMI: 480i, 480p, 720p, 1080i, 1080p
**[COLOR="Red"]PC: SVGA, XGA, WXGA[/COLOR]**
Optimum Resolution: 1920 x 1080

Thus SVGA-800x600 XGA-1024x768 WXGA-1280x720 so try setting your laptops external display size to one of those resolutions and see how far you get. Your laptops native resolution is 1280x800 which is for a 16:10 aspect ratio display while your tv is 16:9.

Secondly from the manual on page 33,

> VIEW MODE (VGA)
Select VGA as your input source and use the View Mode sub-menu to adjust the display in VGA mode.
Press [image/icon] on the remote control or MENU on the control panel to display the setup menu screen then select View Mode to display the View Mode sub-menu.
The following options are available: Aspect Ratio, H. Position, V. Position, Fine Tune, and **Auto Sync**.

So maybe try Auto Sync.

But here is the weird thing, in the specifications section of the manual (page 54) it says:

> **PC Timing**
640 x 400 @ 85Hz,
640 x 480 @ 60Hz/75Hz,
800 x 600 @ 56Hz/60Hz/75Hz,
1024 x 768 @ 60Hz/70Hz/75Hz/85Hz,
1280 x 1024 @ 60Hz,
**1920 x 1080 @ 60Hz**

So maybe try 1920x1080@60Hz and make sure you set your laptops external display output to those exact resolution & sync rate (60Hz). If this does not work then I think you are stuck with WXGA-1280x720

So maybe try all the of the above things and see how far you get.

---

### Post by donniezazen on 2011-12-22
> **inobe said:**
> very nice set:)

Got it for $330 from Walmart during pre-thankgiving sale. :popcorn:

---

### Post by inobe on 2011-12-22
a friend payed over 700$ for that same model :)

got mine a 130 bucks cheaper at walmart, 830$ is the manufactures price.

vizio M420SV, pretty much has everything in the tv, web apps, wireless and ethernet connections, usb..

---

### Post by donniezazen on 2011-12-22
> **mips said:**
> According to their website [http://westinghousedigital.com/products/led/42-55/ld4258/](http://westinghousedigital.com/products/led/42-55/ld4258/)



Thus SVGA-800x600 XGA-1024x768 WXGA-1280x720 so try setting your laptops external display size to one of those resolutions and see how far you get. Your laptops native resolution is 1280x800 which is for a 16:10 aspect ratio display while your tv is 16:9.

Secondly from the manual on page 33,



So maybe try Auto Sync.

But here is the weird thing, in the specifications section of the manual (page 54) it says:



So maybe try 1920x1080@60Hz and make sure you set your laptops external display output to those exact resolution & sync rate (60Hz). If this does not work then I think you are stuck with WXGA-1280x720

So maybe try all the of the above things and see how far you get.

Thank you so much for your time.

I have XBMC Live installed on it now and I have tried Ubuntu-Desktop before. Their are only two resolutions available 640x480 and 320x240. Auto sync only helps when you have the resolution but it is displaced from the actual screen. I get 1920x1080@60Hz through HDMI from PS3 or a laptop with HDMI. I don't know why it works on 60Hz instead of 120Hz. 1280x720 is smooth and clear on windows and i could crank it up to 1600xXXXX but it is not clear.

Thanks.

---

### Post by mips on 2011-12-23
> **donniezazen said:**
> I don't know why it works on 60Hz instead of 120Hz.

It's two different things as far as I remember. The 60Hz refers to the sync rate for the incoming signal on the input ports. The 120Hz refers to how often the the actual display/screen you see is refreshed (or turned on and off) which is 120 times a second to provide a better viewing experience.

---

### Post by mips on 2011-12-23
> **donniezazen said:**
> I have XBMC Live installed on it now and I have tried Ubuntu-Desktop before. Their are only two resolutions available 640x480 and 320x240.

Something is not right there I reckon, I would look into it a bit more if I was you.

---

### Post by donniezazen on 2011-12-23
> **mips said:**
> Something is not right there I reckon, I would look into it a bit more if I was you.

I am going to do another clean Ubuntu desktop install and then try more things. Would you suggest Nouveau or Nvidia drivers?

---

### Post by mips on 2011-12-23
> **donniezazen said:**
> I am going to do another clean Ubuntu desktop install and then try more things. Would you suggest Nouveau or Nvidia drivers?

I would suggest the nVidia drivers, especialy the Beta ones just in case.

[http://www.nvidia.com/Download/Find.aspx](http://www.nvidia.com/Download/Find.aspx)

Under "Recommended/Beta:" select "Beta"

---

### Post by donniezazen on 2011-12-24
> **cariboo907 said:**
> You should be able to get at least 1360X768 resolution. You may have to change the picture setting in the TV menu to just scan. This should fix any under or over scanning you are experiencing.

> **mips said:**
> I would suggest the nVidia drivers, especialy the Beta ones just in case.

[http://www.nvidia.com/Download/Find.aspx](http://www.nvidia.com/Download/Find.aspx)

Under "Recommended/Beta:" select "Beta"

On one instance i got 1360x768 but in order to get 1280x720 or better 1920x1080, i messed up everything. Now i am again stuck at 640x480. I have tried to install manually, through ppa and using additional drivers.

I get white blocks instead of text when i start the machine and then it would stuck their for ever. The only way i am able to get to my system is through recovery console and then resuming normal boot.

---

### Post by inobe on 2011-12-24
i found something.

[http://ubuntuforums.org/showthread.php?t=1897588](http://ubuntuforums.org/showthread.php?t=1897588)

---

### Post by donniezazen on 2011-12-24
> **inobe said:**
> i found something.

[http://ubuntuforums.org/showthread.php?t=1897588](http://ubuntuforums.org/showthread.php?t=1897588)

Thanks I will try that.

I have a couple of options when it comes to Nvidia Driver.

1.Manually(Beta).
2.Nvidia-current from additional drivers.
3.Nvidia-current from ppa.
4.Nvidia-current-updates from ppa.

I am a little confused about which to use. Also, what is the difference between nvidia-glx-xxx and nvidia-current.

Thanks for all your help.

---

### Post by inobe on 2011-12-24
i just add the x-swat, this gives me the newest stable driver, it's the 290.10

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

i don't do the manual deal, i can see the benefits, just not on a stable system.

from hardware drivers, too old, even the current there is older than the newest stable release. 

> 4.Nvidia-current-updates from ppa.

i assumed with the repo i would stay current and get stable updates.

---

### Post by donniezazen on 2011-12-25
> **inobe said:**
> i just add the x-swat, this gives me the newest stable driver, it's the 290.10

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

i don't do the manual deal, i can see the benefits, just not on a stable system.

from hardware drivers, too old, even the current there is older than the newest stable release. 



i assumed with the repo i would stay current and get stable updates.

I did a clean install and installed nvidia-current from ppa which is 290.10. I have plenty of graphic modes from 320x240 to 1360x768 but no 1280x720 or 1920x1080 and anything beyond 1024x768 is invalid format. xrandr gives me error xrandr: Failed to get size of gamma for output default which have myriad of posts i am investigating.

Thanks.

---

