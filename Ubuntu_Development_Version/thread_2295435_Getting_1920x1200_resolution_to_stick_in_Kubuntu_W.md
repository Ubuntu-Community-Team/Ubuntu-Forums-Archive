---
title: "Getting 1920x1200 resolution to stick in Kubuntu Wily, Intel 82Q35 chipset..."
date: 2015-09-18
forum: Ubuntu Development Version
---

### Post by jrogers-f on 2015-09-18
It's VGA compatible controller, Product: 82Q35 Express Integrated Graphics Controller, Vendor: Intel Corp, physical id: 2, bus info: pci@0000:00:02:0, version: 02, width: 32bits, clock: 33MHz, capabilities: msi pm vga_controller bus_master cap_list rom, configuration: driver=i915 latency=0

I've tried all various tricks, hacks, suggestions, and nothing seems to work. When I installed Kubuntu Wily other week with the ISO build from then, it installed fine, resolution was fine, now after installing new ISO from Sept 17th 2015, I'm stuck with crappy 1024x768 resolution... I have 24" NEC AccuSync LCD 24WMCX monitor and the 1024x768 is killer on the eyes and puts me to sleep. 

HOW do I do a xorg.conf file setup? There's two to three places with x11 files or folders, can't make new files there in any of them, no right click to open as root option, can't create the file else where and move it there, I can't do "X -configure" I get lock errors. Please don't link to ubuntu screen/resolution manuals, and temporarily turn off lightdm, it don't work, get lock errors... Nothing seems to work! I thought Intel drivers were handled in the operating system????  I can temporarily change it though with xrandr, add mode, output it, etc.. just once reboot or logout and back in, oops, it's gone. 

Can someone show proper steps to create xorg.conf, or edit which files etc? This should be out of the box stuff though, should automatically detect and handle your resolutions, not make normal users do system file edits (possibly damaging their system more). Average users, computer illiterate users shouldn't have to learn all this stuff to use Kubuntu or Ubuntu or whatever.. should just hook up your hardware, it detects it, and off you go, all happy and using the software.

P.S. Am I supposed to download intel graphic drivers from some site and if so, which ones for my chipset / i915 drivers?

---

### Post by jrogers-f on 2015-09-18
I managed to get the xorg.conf created and displaying 1920x1200, but the password screen for cryptsetup and splash/login screen is still 1024x768 resolution. How do I fix this? I tried other various things, for grub but don't work. [http://ubuntuforums.org/showthread.php?t=1469223&p=9215732#post9215732](http://ubuntuforums.org/showthread.php?t=1469223&p=9215732#post9215732)
[http://www.binarytides.com/ubuntu-fix-nvidia-graphics/](http://www.binarytides.com/ubuntu-fix-nvidia-graphics/) [http://askubuntu.com/posts/362998/revisions](http://askubuntu.com/posts/362998/revisions)

trying to do xorg.conf changes, and restarting the x server or whatever don't work either, nothing seemed to work. ctrl alt backspace don't work, all these don't work... so.. not sure how to do much. 

                        [FONT=monospace]matteo@matteo-OptiPlex-755:~$ sudo service lightdm restart 
[sudo] password for matteo:  
Failed to restart lightdm.service: Unit lightdm.service failed to load: No such file or 
directory. 
matteo@matteo-OptiPlex-755:~$ killall X 
X: no process found 
matteo@matteo-OptiPlex-755:~$ sudo restart gdm 
sudo: restart: command not found 
matteo@matteo-OptiPlex-755:~$ sudo restart kdm 
sudo: restart: command not found 
matteo@matteo-OptiPlex-755:~$ startx 
X: user not authorized to run the X server, aborting.[/FONT]

 
Here's xorg.conf file... 
Section "Monitor"
Identifier "Monitor0"
VendorName "NEC"
ModelName "24WMCX"
HorizSync 28 - 85
VertRefresh 50 - 100
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "i915"
VendorName "Intel"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1200" "1280x1024" "1024x768" "640x480"
EndSubSection
EndSection

other info.. 

   [FONT=monospace][COLOR=#000000]matteo@matteo-OptiPlex-755:~$ xrandr [/COLOR]
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767 
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
  1024x768      60.00*  
  800x600       60.32    56.25   
  848x480       60.00   
  640x480       59.94   
VIRTUAL1 disconnected (normal left inverted right x axis y axis) 
matteo@matteo-OptiPlex-755:~$ cvt 1920 1200 60 
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz 
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsy
nc[/FONT]

---

