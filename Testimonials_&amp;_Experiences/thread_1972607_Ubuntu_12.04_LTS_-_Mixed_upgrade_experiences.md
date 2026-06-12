---
title: "Ubuntu 12.04 LTS - Mixed upgrade experiences"
date: 2012-05-03
forum: Testimonials &amp; Experiences
---

### Post by Tanker Bob on 2012-05-03
I upgraded two machines to Precise - the desktop box described in my signature and a dated Dell Inspiron laptop.

The desktop box was running a fully updated 11.10 Oneiric setup. I used the Update Manager to run the upgrade. The upgrade seemed to be running smoothly until after the initial login. At that point, all I could get was the wallpaper - no Unity or compiz. The mouse pointer moved but that was it. I used Ctrl-Alt-Backspace (previously reenabled many version ago) to logout and login to the Unity 2D setup. Unity 2D loaded OK, but compiz crashed repeatedly. I even tried nouveau, but that was a joke as it would only run in an absurd 1024x768 resolution. 

After 6 hours of trying everything of which I could think, I learned that the proprietary nVidia 295.40 drivers in the 12.04 upgrade set broke support for a number of video cards, including mine. After manually uninstalling those drivers and loading the previous 295.33 version, I could finally get Unity and compiz to load in 3D. Even then, changing compiz settings would crash Unity. I finally had to uncheck Unity in ccsm, make my substantial setting changes to compiz to regain my 11.10 setup, then reenable Unity. The entire process took about 9 hours, but now I have a working 12.04 desktop that seems stable as long as I don't change too many compiz settings at one time with Unity running.

OTOH, the laptop started with 10.04 LTS. I used Update Manager to march through all the intermediate upgrades - 10.10, 11.04, and 11.10 - to get to 12.04 LTS. This took just over 3 hours, mostly running on its own, but worked perfectly. The laptop uses a very simple compiz configuration and seems very stable.

I'm not sure what's causing the instability between Unity and changing a number of compiz settings at one time, but that needs to be addressed. Other than that, 12.04 LTS seems to work pretty well.

---

