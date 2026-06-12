---
title: "Dual Display on Wild Dog"
date: 2009-07-13
forum: System76 Support
---

### Post by katycorp on 2009-07-13
I just received a Wild Dog desktop and I'm having trouble getting the dual display to work. Originally it had the proprietary ATI driver installed, but every time I went to open System->Preferences -> Display the entire computer locked up. It seems there are some problems with ATI drivers and Jaunty. I switched to the open source ATI driver and the overall performance on the entire machine is much better and the display dialogue opens up. However, when I uncheck the "mirror" option I get a huge low res display that appears across both monitors, yet most of the panning area is outside the visible area of the screen. I can't access any of the menus or change the resolution in the display dialogue. Is there any way to set up a dual display on this machine? 
Thanks,
Kaitlin

---

### Post by thomasaaron on 2009-07-14
Good morning, Kaitlin.

You don't use System > Prefs > Display with the ATI card. You use Applications > Accessories > ATI Catalyst.

---

### Post by katycorp on 2009-07-17
Catalyst control center was not available when I had the original proprietary ATI driver installed. And the original driver was also causing significant performance issues. I was able to resolve the performance issues and access CCC by installing the latest ATI ubuntu driver from the ATI website (version 9-6 I think). However, the dual display was still not an option in CCC. I could only have a mirror display. All the options for dual display in CCC were greyed out. I solved it by running the aticonfig from bash with some different options. For anyone who's wondering, I've attached the /etc/X11/xorg.conf that was created by running the config. Now it works almost perfectly. I think the important lines to note in the config are:

Option        "EnableRandR12" "false"
Option        "DesktopSetup" "horizontal"

for enabling the horizontal dual display. 

When I come back from hibernate the display panning area is screwed up but I can live with that since I almost never hibernate. Hope this helps anyone who might have the same issue.

---

### Post by thomasaaron on 2009-07-20
There is a better way to do dual monitors/spanned desktops. You should not have to change ati drivers and download any software. Please contact System76 for support via email before doing any of that stuff, as it could result in drivers being broken during kernel updates.

---

