---
title: "Virtualbox 4.2.14 - Linux guest - No mini toolbar in fullscreen mode"
date: 2013-06-30
forum: Virtualisation
---

### Post by TE7 on 2013-06-30
Windows 7 64 bit host
Linux guests Ubuntu 13.04 both 32 and 64 bit

I recently had to update my video driver for my AMD Radeon 6670 (driver version 13.4, release date 2013-5-29). After updating, my linux guests will not display the mini toolbar in fullscreen mode, nor does the host+home key work. I have no problem with the Windows guests. I have read on the net that this has been a long standing problem for ATI-AMD drivers. When I disable 3d acceleration for the guest, the problem is not present. But there'a a performance hit. Slow display and responsiveness. Any input from anybody would be greatly appreciated.

---

### Post by TE7 on 2013-06-30
I found a solution by following the steps here:

[http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

My host screen resolution is 1920x1080, so I just set the horizontal resolution to 1 less than 1080: 1079.

This is how my 10-monitor.conf looks:



Section "Monitor"
  
    Identifier "Monitor0"
  
    Modeline "1920x1079_60.00"  172.64  1920 2040 2248 2576  1079 1080 1083 1117  -HSync +Vsync

EndSection



Section "Screen"
  
    Identifier "Screen0"
  
    Device "VBOX0"
  
    Monitor "Monitor0"
  
    DefaultDepth 24
  
    SubSection "Display"
    
        Depth 24
    
        Modes "1920x1079_60.00"
  
    EndSubSection

EndSection

After that, go to your display settings and choose your new screen size.


Now in fullscreen mode I have the mini toolbar at the bottom of the screen.

---

