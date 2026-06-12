---
title: "panp7 has worse video with proprietary ati driver in 10.04?"
date: 2010-05-06
forum: System76 Support
---

### Post by jcwilk on 2010-05-06
Hello,

When I enable the ATI driver my native terminal (not sure what the right term for this is, I'm referring to the bare-bones terminal you get by switching with ctrl-alt-F1/F2/F3..etc) is really low resolution, looks like maybe 800x600, but with the default ubuntu driver (presumably an open source driver for ati cards) it's the perfect resolution, it's faster than I've ever seen it to switch back to the X terminal (alt-F7), literally before my finger leaves the key.

I guess my question is if there is a way to get the bootup/native terminals in the correct resolution with the proprietary ATI driver or if we're better off just using the ubuntu drivers?

Also, I use an external monitor with a resolution that's much higher than my laptop screen and for the dual monitor setup it's really annoying because there's sort of "dead space" above my laptop screen... Below if you imagine the x's as my monitors with the one on the right much larger, above the little x is the dead space up to the pixel height of the big X...

xX

Hope that makes sense, it's really annoying because when I try to go to the top of the screen my cursor just goes past it out of sight for a bit. Anyone figure out how to address this?


Thanks,
John

---

### Post by jcwilk on 2010-05-11
Yep, I went back and gave the ATI driver a second chance and it's confirmed, it's terrible. I had to choose between Xinerama (unbearable) and two separate X screens where you couldn't drag windows between them (pitiful). Shame that the p7 doesn't have a nvidia card in it, nvidia twinview is flawless. I don't even really notice any visual performance hickups, though the only visually stressful thing I make the computer do is sidekick windows back and forth from being minimized... over... and over...

So I'm just using the nonproprietary driver and it works like a charm, no complaints at all. I strongly suggest anyone using a pangolin to try disabling the proprietary ATI driver in System -> Administration -> Hardware Drivers. -Especially- if you use a secondary external monitor, and why wouldn't you.

I got around the deadspace issue I described by just lining up the tops of my screens in System -> Preferences -> Monitors so that all of my top-screen menus are on the hard edge of the screen, and only my laptop's smaller screen has the annoying deadspace below it. But I -always- delete the bottom of the screen panels anyways, why would anyone want to have to move the cursor back and forth between the top and bottom of the screen when all of the window menus are on the top? I never understood why operating systems seem to obsess over putting some of the most important things at the bottom of the screen, the least convenient place possible.

Anyways, sorry for the rant, hope some people revert away from the proprietary driver and harass s76 to quit giving us ati junk :\ (though i still love the computer and love you guys! just not the video card >_<)

---

### Post by jcwilk on 2010-05-11
Oh yeah, I guess I should clarify that if you never picked to enable to ATI driver in the first place you're already good to go, but I guess I just assume everyone does that right away without thinking twice.

---

### Post by isantop on 2010-05-11
Actually, we get about the same issue on the Nvidia Machines in here. It is a simple fix for those, but it still happens by default. This seems to be an issue with either plymouth or the new Kernel's mode-setting. (Or both.) 

We recommend using the default gnome monitor configuration applet, since the setup is a lot simpler. With the exception of tty and splash-screen support, though, the proprietary driver is the way to go, as the open-source on has very poor 3D support.

---

### Post by satsujinka on 2010-05-11
I assume the open source ati driver works with xrandr so could you give the output of xrandr?Also if you know the names of your monitors you could try running: 
```
xrandr --screen monitor1 --auto --screen monitor2 --left-of monitor1 --auto
```
replace monitor1 and monitor2 with the names of your montiors (which should be something like LVDS1 and VGA1.)

---

