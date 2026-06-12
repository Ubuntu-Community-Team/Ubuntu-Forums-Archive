---
title: "LCD Monitor Calibration! Photo, gfx &amp; web designers."
date: 2008-08-05
forum: The Cafe
---

### Post by mips on 2008-08-05
Ever since I got my LG W2252TQ LCD I have not been happy happy with the image results. My old HP p1230 was and still is stunning when it comes to image reproduction after it was calibrated by eye as I'm not going to splash out $$$ on hardware.

I initially tried my same MO for calibrating my LCD but was not happy with the outcome. Getting the Gamma set on a LCD is an absolute biatch due to the difference in viewing angles (S-IPS panels handle this the best)

I set my monitor to the factory defaults and choose a colour temp (check for your defaults):
Brightness 100/100
Contrast 70/100
Colour Temperature sRGB
Sharpness 5/10

Next I turned the room lights off and worked in semi darkness. Also keep in mind that when you test you should look at the display from a distance and not always up close like you do for normal use.

I opened nvidia-settings to adjust Brightness, Contrast & Gamma as I did not want to fiddle with the monitor control panel. All setting were done with nvidia settings and then saved to xorg.conf.

I then followed the first link below to start the calibration. I played around for about an hour. As you progress through the steps you start noticing some of the previous steps have gone out of whack so it really is a fine balancing act to get a reasonable output. So I ended up skipping between the different sections to get the best result. I then followed the rest of the links just to suss things out and I have a pretty decent display at the moment although the gamma is still not perfect.

[http://www.lagom.nl/lcd-test/](http://www.lagom.nl/lcd-test/)
[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)
[http://epaperpress.com/monitorcal/](http://epaperpress.com/monitorcal/)
[http://www.colorwizzard.com/lcdtest/index.html#_top](http://www.colorwizzard.com/lcdtest/index.html#_top)
[http://www.pcbypaul.com/software/monica.html](http://www.pcbypaul.com/software/monica.html)

The last link above is for a Linux gamma utility called Monica which I have not tried on my LCD yet but I recall it working nicely with my CRT.

I would advise anybody with a monitor to calibrate to ensure your display is optimally set. This way the photo you see from your camera or a website  you know would be an accurate representation.

I would also encourage web designers & gfx artists to definately do this so you know what your stuff actually really looks like.

The above steps can also be use to calibrate a CRT which is generally easier.

**EDIT:**
I have noticed that the changes I made are not persistant even though I ran nvidia-setting with sudo in order to save the changes to the xorg.conf

To make the changes persistant:
**nano  ~/.nvidia-settings-rc**
```
0/RedBrightness=-0.17
0/GreenBrightness=-0.17
0/BlueBrightness=-0.17
0/RedContrast=-0.14
0/GreenContrast=-0.14
0/BlueContrast=-0.14
0/RedGamma=1.013
0/GreenGamma=1.013
0/BlueGamma=1.013
```**sudo nano /etc/X11/xorg.conf**
```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2252"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Gamma           1.013 1.013 1.013
    Option         "DPMS"
EndSection
```

---

### Post by Bachstelze on 2008-08-05
*thanked and bookmarked*

I'm going to start photography seriously soon-ish, so that will surely be of great help.

---

### Post by mips on 2008-08-05
I wish I could somehow provide before and after images of the improvement but that is not possible (for the reasons listed above) unless I took a photos which would not be that great.

---

### Post by shallpion on 2008-11-10
Oh MY~@!!! That is just I was looking for !!!! You really help!! Thank you!!

By the way, do you know if ATI's driver supports such tiny configuration, such as redcontrast or bluebrightness? These parameters are significant for color configuration.

Thank you!

---

### Post by mips on 2008-11-11
> **shallpion said:**
> 
By the way, do you know if ATI's driver supports such tiny configuration, such as redcontrast or bluebrightness? These parameters are significant for color configuration.


I honestly do not know when it comes to ATI. What I do however know is that the ATI control panel or whatever it is called does have some calibration options for Linux. Best you have a look for yourself or hopefully someone else comments.

---

### Post by handy on 2008-11-11
The ATi Catalyst Control Center gives you Gamma correction on Red, Green & Blue.

Apart from that, the other controls look to be specifically for 3D & dual monitor setups, at least that's how it looks to the uninitiated.

---

### Post by HanZo on 2008-11-11
wow great! Thank you so much for this! just one question... you don't happen to know how to get ubuntu to load an existing profile, do you? Because I have a hardware calibration tool that creates an icc profile for the monitor (with an app that runs on win)... I have the profile now, but of course it only works on windows...

---

### Post by jespdj on 2008-11-11
If you really want to calibrate and set up your monitor accurately, then there's nothing that beats a hardware monitor calibration device.

I'm using an old Spyder to profile my monitor (Dell 2405FPW) on Windows, and load the generated ICC profile in Ubuntu using xcalib (a very small utility to load the monitor profile).

---

### Post by mips on 2008-11-11
> **HanZo said:**
> wow great! Thank you so much for this! just one question... you don't happen to know how to get ubuntu to load an existing profile, do you? Because I have a hardware calibration tool that creates an icc profile for the monitor (with an app that runs on win)... I have the profile now, but of course it only works on windows...

I might be wrong but from what I recall it 'might' be possible to use windows icc profiles from windows in Linux. I came across it a long time ago though so I'm not to sure though. I recall this because people could not get their calibration hardware to work in Linux but they could transfer the profile to Linux although it was not global.

I will have a look at some stage when I have time.

EDIT: I think jespdj just answered your question above this post.

---

### Post by JohnFH on 2008-11-11
> **HanZo said:**
> wow great! Thank you so much for this! just one question... you don't happen to know how to get ubuntu to load an existing profile, do you? Because I have a hardware calibration tool that creates an icc profile for the monitor (with an app that runs on win)... I have the profile now, but of course it only works on windows...

I've calibrated my (LCD) monitor in Linux using the Sypder2 express spider tool USB thingy.  It creates and applies the icc profile and doesn't need to rely on one being built in Windows.

Two links I use:

[http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/]("http://jcornuz.wordpress.com/2007/11/16/spyder-the-good-and-the-ugly/")
[http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux]("http://jcornuz.wordpress.com/2007/11/18/use-colorvision-spyder-to-produce-an-icc-monitor-profile-under-argyllcms-linux")

If you don't want the bother of creating another .icc profile (it does take a while), just jump to the relevant part in the guide and run the dispwin command to apply the profile.  You will need to apply the profile every time you boot, so best to add it to your list of startup scripts.  (You could also use xcalib to apply the profile but I've never done it that way).

Hope that helps.

---

### Post by shallpion on 2008-11-11
Thank you all for your kindly answers~~ sorry I am little confused... I checked the price of spyder2 and it is acceptable---I thought it was an astronomical numbers...

Ok, so what I need to do, simply, is forgetting the difference between drivers of ati/nvidia, buying any card I like and a spyder, then deriving an icc file in windows and using xcalib to load it. Or following the instructions to make spyder running in Linux? Is that correct? 

Thank you all~~

---

### Post by JohnFH on 2008-11-11
You don't seem confused at all, so yes, what you say is exactly right.

---

### Post by mips on 2008-11-12
> **JohnFH said:**
> I've calibrated my (LCD) monitor in Linux using the Sypder2 express spider tool USB thingy.

How much did you pay for your Spyder 2?

I see Amazon/17 Street Photo is selling the Spider 2 Suite for $70

[http://www.amazon.com/ColorVision-Spyder2-Suite-Win-Mac/dp/B000ES6K34](http://www.amazon.com/ColorVision-Spyder2-Suite-Win-Mac/dp/B000ES6K34)

Does not help me though as Amazon does not ship electronics internationally.

---

### Post by JohnFH on 2008-11-12
> **mips said:**
> How much did you pay for your Spyder 2?

I see Amazon/17 Street Photo is selling the Spider 2 Suite for $70

[http://www.amazon.com/ColorVision-Spyder2-Suite-Win-Mac/dp/B000ES6K34](http://www.amazon.com/ColorVision-Spyder2-Suite-Win-Mac/dp/B000ES6K34)

Does not help me though as Amazon does not ship electronics internationally.

I'm pretty sure I didn't get it as cheap as that.  I think I paid something like £50 for it.  

It can be bought locally (click [here]("http://www.colorvision.co.za/prod_spyder2express.htm")) and maybe you won't get a better price when you take shipping charges into account.

---

### Post by mips on 2008-11-12
> **JohnFH said:**
> I'm pretty sure I didn't get it as cheap as that.  I think I paid something like £50 for it.  

It can be bought locally (click [here]("http://www.colorvision.co.za/prod_spyder2express.htm")) and maybe you won't get a better price when you take shipping charges into account.

At that price I would rather just go with my initial post calibration technique.

---

### Post by LeeHamo on 2008-11-27
I wish I could understand your tutorial cause I have a w2252TQ exactly the same and I cant even begin to set it up properly,

:(

I need help...

---

### Post by mips on 2008-11-27
> **LeeHamo said:**
> I wish I could understand your tutorial cause I have a w2252TQ exactly the same and I cant even begin to set it up properly,

:(

I need help...

If you tell me exactly what problems you are encountering then I will try to help you.

---

### Post by LeeHamo on 2008-11-27
Your a saviour for even reading my post mips.

Basically I can manage to get into nvidia-settings and change my monitor to the optimum resolution (i think, i hope anyway).

[ATTACH]94409[/ATTACH]

Then I try to save and it says it has, I log off and back in and it is back to old setup.

Ive tried many things and im a total noob so I expect ive harmed the xorg.conf file in some way possibly.

Id love to be able to use your tutorial but as yet I cant get off the first part of it.

Lee.

Also just to add, considering we both have exactly the same monitor can I just copy your settings exactly and I will have a monitor set up at its best probably by someone who seems to know exactly what looks best?

My monitor is w2252TQ 22" LG Flatron 2ms.

Cheers.

---

### Post by mips on 2008-11-27
I use Arch Linux so things might me slightly different. Try running nvidia settings as root or with sudo to save stuff.

---

### Post by LeeHamo on 2008-11-27
ive typed many things and none save, whats root?

---

### Post by mips on 2008-11-28
> **LeeHamo said:**
> ive typed many things and none save, whats root?

Try running nvidia setting from the terminal with **sudo nvidia-settings**

[COLOR=Red]I'm not going to answer the root question as it seems on these forums you can get an **infraction** for doing so[/COLOR]. Sudo will do exactly what root does though so do not worry about root if you do not know what it is.

---

### Post by LeeHamo on 2008-11-28
Tried it mate the settings never save.

---

### Post by Graeme1949 on 2012-09-21
> **mips said:**
> 
[http://www.colorwizzard.com/lcdtest/index.html#_top](http://www.colorwizzard.com/lcdtest/index.html#_top)
[http://www.pcbypaul.com/software/monica.html](http://www.pcbypaul.com/software/monica.html)

The last link above is for a Linux gamma utility called Monica which I have not tried on my LCD yet but I recall it working nicely with my CRT.


Outstanding post and a big help for one who is new to the mysteries of color. 

Two of the links posted (see quote above) appear to be dead. They go to "not found" or "this domain is for sale" pages. What alternative sites are there?

---

### Post by Artemis3 on 2012-09-21
I got a huey and dispcalgui for this. It improved gamut in my cheap panel, the hard thing was making the device stick the half hour or so it takes to calibrate :S But its better than spending hours in those "by eye" pages and always second guessing, and never quite getting it right.

---

### Post by mips on 2012-09-21
Something else people can try is downloading ICC profiles for their specific display models, it's not 100% but it's a pretty good starting point.

---

