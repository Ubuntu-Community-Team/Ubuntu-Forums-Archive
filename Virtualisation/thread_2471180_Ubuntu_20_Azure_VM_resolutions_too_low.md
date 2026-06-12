---
title: "Ubuntu 20 Azure VM resolutions too low"
date: 2022-01-22
forum: Virtualisation
---

### Post by hassan42 on 2022-01-22
Hi, 

I installed ubuntu 20.0 on a Azure VM. after installation i installed GUI on it but now the resolutions are too low. 
I did add custom resolutions to via xrandr but no joy. 

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode rdp0 "1920x1080_60.00"

Is it possbile to provide a solution? Note that the VM is in Azure. 

Thanks

---

### Post by wildmanne39 on 2022-01-22
Thread moved to the virtualisation sub-forum.

---

### Post by guiverc on 2022-01-22
It might also help if you're precise & clear with product release details.

Ubuntu has two sets of products, 
- *year.month* format being used by the main products, eg. Ubuntu 20.04 LTS Server
- *year* format being used by *specialist* products intended for devices/appliances or use in the Cloud, eg. Ubuntu Core 20

In the title you mention 20; closest being Ubuntu Core 20, but in your main question you state 20.0; which makes little sense given 0 is not a valid month (the main LTS release comes out in April thus it's .04; ie. Ubuntu 20.04 LTS is the 2020-April release).

Both 20 & 20.04 are different products; with 20.04 being the more powerful.  Ubuntu Core 20 is also designed for *headless* operation and not for use with GUIs.  (*FYI: there is also no `apt` command in 20 as the year releases are snap package only, with desktops being packaged as deb packages*)

---

