---
title: "Gazelle Professional Screen Resolution"
date: 2013-02-26
forum: System76 Support
---

### Post by 3Miro on 2013-02-26
I currently have panp8 and I have been unable to use the HDMI port to get full resolution 2560x1440 on my external monitor (I can get up to 1920x1200). I read somewhere that Intel HD 3000 doesn't support 2560x1440 resolution in general.

Does the Gazelle Professional support 2560x1440 resolution through the HDMI port?

Answer: YES, both Panp7 and Panp8 support the resolution. On Panp7 I had to use xrandr and create a new mode with refresh rate of 40
```

cvt 2560 1440 40

```
See the tutorial below for all of the commands that would be needed.

Thanks to isantop for the help. every time I talk to him I discover a new power hidden in my laptop.

---

### Post by isantop on 2013-02-27
What monitor are you using? Your PanP8 should be capable of outputing at 2650x1600 over HDMI.

EDIT: Also check that the cable you're using supports HDMI v1.4, as earlier 1.3 cables will only support lower resolutions.

---

### Post by 3Miro on 2013-02-27
This is the monitor that I am using.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16824236294](http://www.newegg.com/Product/Product.aspx?Item=N82E16824236294)

When using the laptop with HDMI on monitors with 1920x1200 or lower, everything is detected via the Display setting (using 12.04 LTS).

When I use HDMI with the 2560x1440, the highest resolution is detected as 1600xSomething.

The same monitor works fine with my desktop using DVI, Display Port, or DVI to HDMI adapter (i.e. the DVI, DP and HDMI ports on the monitor work fine). 

I searched for a solution, but all that I found were forum people with similar issues and others claiming Intel HD doesn't support 2560x1440 at all.

Do I need to edit Xorg manually? Is there another setting tool that I am not using?

---

### Post by isantop on 2013-02-28
> **3Miro said:**
> This is the monitor that I am using.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16824236294](http://www.newegg.com/Product/Product.aspx?Item=N82E16824236294)

When using the laptop with HDMI on monitors with 1920x1200 or lower, everything is detected via the Display setting (using 12.04 LTS).

When I use HDMI with the 2560x1440, the highest resolution is detected as 1600xSomething.

The same monitor works fine with my desktop using DVI, Display Port, or DVI to HDMI adapter (i.e. the DVI, DP and HDMI ports on the monitor work fine). 

I searched for a solution, but all that I found were forum people with similar issues and others claiming Intel HD doesn't support 2560x1440 at all.

Do I need to edit Xorg manually? Is there another setting tool that I am not using?

The HD 3000 on your Pangolin definitely does support it though (At least, it supports 2650x1600. It may not support x1440 for some weird reason). 

Do you have the display mirrored at all? Are there any other monitors plugged into the system apart from the built-in?

---

### Post by 3Miro on 2013-02-28
I have only the in-build monitor and the external monitor.

I plug the monitor in the HDMI port using the cable that comes with the monitor (the laptop has nothing else plugged other than the power cord). The display settings show that there is an external monitor, but allow only resolution up to 1600xSomething. I switch to the external monitor and disable the in-build one. The picture is horrible and the highest possible resolution is till listed as 1600xSomething.

Monitors with 1920x1080 and 1920x1200 resolution work just fine.

2560x1440 is 16:9 aspect, 2560x1600 is 16:10. The in-build monitor is 16:9 (1366x738).

Would you know what is the correct syntax of the Xorg file to force the monitor to 2560x1440 manually. Maybe this is just a Gnome bug for not reading the correct info from the monitor.

---

### Post by isantop on 2013-02-28
Ubuntu no longer uses an xorg.conf file for graphics configuration, so I'd advise against that approach. This article would be a much better idea: [http://myit-solutions.blogspot.com/2010/09/how-to-add-and-set-custom-display.html](http://myit-solutions.blogspot.com/2010/09/how-to-add-and-set-custom-display.html)

---

### Post by 3Miro on 2013-02-28
xrandr is also good. I didn't think to try it before. I am out of town now, but I will try it out and probably let you know on Saturday.

---

### Post by 3Miro on 2013-03-02
I did try the tutorial, it is a good tutorial.

I was able to use xrandr to create a 1920x1080 mode and I was able to switch to that mode. The laptop and monitor are now happy with that resolution. Here is something interesting that I found on Intel's web-site, apparently there is a known bug in the monitor/laptop communications. 

[http://www.intel.com/support/graphics/sb/CS-030193.htm](http://www.intel.com/support/graphics/sb/CS-030193.htm)

However, I was unable to use 2560x1440 mode. I did add the mode just like the 1080 resolution, however, when I switch to that mode, the monitor goes blank and says that there is no HDMI signal. After 30 seconds the Laptop reverts back to the old resolution.

I tried to lower the refresh rate from 60 to 30. At 2560x1440_30, the external monitor doesn't lose signal, however, the image keeps moving along the screen at refresh rate of about 2 frames per second. It is difficult to describe what happened, it looks a lot like a heavily lagging game, but it is not lag in the ordinary sense since I was able to also use the inbuild laptop monitor.

Tried this couple of times with no luck. I made sure to try everything with power plugged and without laptop monitor (i.e. enable only the external monitor).

Any ideas?

---

### Post by 3Miro on 2013-03-02
Solved it, I had to lower the refresh rate to 40. See the first post.

---

