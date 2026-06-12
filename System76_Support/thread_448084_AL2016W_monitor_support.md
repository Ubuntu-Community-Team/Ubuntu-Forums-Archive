---
title: "AL2016W monitor support?"
date: 2007-05-18
forum: System76 Support
---

### Post by greg_g on 2007-05-18
Hello, I am very close to ordering a Ratel but I have one question.

The monitor I have now and would like to use is an Acer AL2016W (the w is for widescreen).  When trying to install ubuntu 6.10 before I had problems with the liveCD in that the output of the video card was not supported by the monitor.  I had to use the text installer on the alternate install cd to get it installed and then to get the correct resolution I had to mess with the drivers for the ATI 9250 I used to have.

Basically, just asking if you know of any other issues people with widescreen LCD displays have had.

By the way, monitor native resolution is 1680x1050.


Thanks in advance,

greg

---

### Post by thomasaaron on 2007-05-21
It looks like that particular monitor has been challenging to others as well.
However, it should not be a problem to get it configured for the Ratel.

See:
[http://ubuntuforums.org/showthread.php?t=447510](http://ubuntuforums.org/showthread.php?t=447510)

The Ratel's lowest-end nVidia card option is the GeForce 6200LE, which is capable of a maximum
resolution of 2048 x 1536.

---

### Post by DsH on 2007-08-10
I recently installed Feisty on my desktop computer. It has an ATI 9200 video card. For some reason the resolution that X picked was not the correct native resolution for this display, which is 1680x1050. I could select this resolution in the system - preferences - screen resolution menu, but when I did, there were some problems with the desktop. There was a ghost on the very edges of the screen. If I clicked on the Applications menu, it would show up on the top right hand corner of the screen AS WELL as the top left hand corner. I finally figured out how to correct this problem in case anyone is having the same problem.
At a terminal prompt type:

sudo gedit /etc/X11/xorg.conf

scroll down untill you find the section about your monitor
find Depth 24 (the default color depth)
add "1680x1050" to the list of resolutions
save xorg.conf
exit
restart X by ctrl-alt-backspace

and its fixed!8)

---

