---
title: "Direct Draw And Video card fun - Please Help"
date: 2008-01-23
forum: Windows
---

### Post by jordank on 2008-01-23
Alright, I've searched all over the net, and I can't figure out what the problem is.

I'm trying to play warcraft 3 (recently I dual booted vista wtih ubuntu).  However, when I doubleclick my icon to play, it tells me that the directx is wrong, and that it cant initialize, etc etc.

Looking around the net, there were a lot of people with the same problem.  I've tried running as an administrator, using xp service pack 2, etc.  I think it's a video card driver problem.  When i go to my device manager, the only thing i can see that is related to video cards is:
Standard VGA graphics adapter.  I don't know what this is exactly, but the video card in my laptop is an nvidia 8600m gt 256. So this definitely should be able to run warcraft 3.  When i type dxdiag in the run line, and go to the display tab, it tells me that
directdraw: not available
direct3d: not available

how can I get these working properly, I do believe that this is my problem.

I've tried going to control panel - display -advanced settings - troubleshoot - hardware acceleration and turning it all the way to full, but that doesn't seem to do anything.  I really have no idea what I should do from here. 
How do I tell my computer that I'm using this video card, and get the latest drivers for it, AND get my directdraw/direct3d working properly.

Thanks in advance.

---

### Post by redcrayon on 2008-03-17
It sounds like your graphics card drivers are not installed.

Luckily you have an Nvidia card... possibly the easiest drivers to install :)

Go to Nvidia.com and download the latest drivers.
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
this is the link to the download drivers page - choose the cllosest match to you video card. These drivers are usually fairly generic.

peace.

---

### Post by sayakb on 2008-03-17
> **redcrayon said:**
> It sounds like your graphics card drivers are not installed.

Luckily you have an Nvidia card... possibly the easiest drivers to install :)

Go to Nvidia.com and download the latest drivers.
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
this is the link to the download drivers page - choose the cllosest match to you video card. These drivers are usually fairly generic.

peace.

+1

Standard VGA Graphics Adapter @ Device Manager means that you do not have the driver installed.

---

