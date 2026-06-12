---
title: "VMware running Ubuntu and fbdev"
date: 2008-03-27
forum: Virtualisation
---

### Post by swoopy on 2008-03-27
Hi all,

I'm new to the Ubuntu forums so I hope I'm posting to the right section! 

I'm running Ubuntu in VMware and have a video application that renders using /dev/fb0. I run the executable from a terminal window and the video renders all the way across the top of the desktop and even then only when the terminal window is dragged around the desktop across that general region.  

I suspect it's a combination of a couple of things: a screen refresh problem and the fbdev drivers aren't set up properly for the X environment. I did run the same app in console mode only and it played smoothly.

In my long running attempts to get this going smoothly in the desktop environment I have done the following: 

edited and updated /boot/grub/menu.lst to include video = vesafb vga= 0x305

also edited /etc/grub.conf for  video = vesafb vga= 0x305

and generally pulled my hair out trying a number of other combinations of things with no improvement :)

I also tried to look at the system/preferences/screen resolution to change the refresh rate but that seems to be left a 0Hz and unchangeable.

I have posted Xorg.0.log  and a copy of xorg.conf here. Any help on this will be much appreciated. 

Thanks in advance!!

---

