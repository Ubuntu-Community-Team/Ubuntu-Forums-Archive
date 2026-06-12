---
title: "Custom resolution and xrandr agony"
date: 2015-08-02
forum: Ubuntu/Debian BASED
---

### Post by anes2 on 2015-08-02
I am using Zorin OS 9 (ubuntu based), I have NVidia GTX 750 GPU. My goal is to have 1920x1080 resolution but I guess NVidia are too big to allow that by default like in Windows, to steer you from the platform I suppose. After about 4 hours of googling, searching on  variosu forums, reinstalling the OS 3 times and installing (and reinstalling) the NVidia (not nouveau) drivers countless times. I have probably inserted the xrandr command at least 100 times. I followed all the videos and guides and nothing seems to work. Get the modeline thing with gtf or cvt with command: gtf 1920 1080 60. You get a modeline thing and you copy the thing after the <Modeline>. You enter xrandr --newmode (copied thing from modeline). xrandr --addmode VGA-0 (name of the thing, in my and most cases, 1920x1080_60.00). And here on the addmode it displays and error, and it's always the same bloody one;
```
Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34


```
I also tried the permanent solution of editing the xorg.conf file also 4 times in 4 different ways and neither work. Here's my xrandr:```
Screen 0: minimum 8 x 8, current 2040 x 1152, maximum 16384 x 16384
VGA-0 connected primary 2040x1152+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x1f1)  172.5MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.0KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   59.9Hz
  1920x1080_59.90 (0x1f2)  172.5MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.0KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   59.9Hz
  1920x1080_60.00 (0x1f9)  172.8MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz
  1080p (0x1fa)  172.8MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz
  1920x1079_60.00 (0x1fc)  172.6MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.0KHz
        v: height 1079 start 1080 end 1083 total 1117           clock   60.0Hz
  1600x1200_60.00 (0x204)  161.0MHz
        h: width  1600 start 1712 end 1880 total 2160 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1207 total 1245           clock   59.9Hz


```
Yes, I know there's lots of these things but it just shows the many times I've tried it this session; it resets after rebooting, and I've also reinstalled the OS to make sure this is not the issue. So yeah, I can make them but can't add them to my VGA-0 output, always the same invalid parameter error, which makes me think, maybe the syntax or something changed but surely it didn't because it lists the same thing on the wiki. Oh, and also, don't tell me to do the 4 step xrandr thing one more time because I'm so happy right now. Any commands or info you want just let me know I'll be constantly refreshing this and thanks in advance

---

### Post by howefield on 2015-08-02
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by anes2 on 2015-08-15
I have found the solution to my problem, I'm posting here for the sake of helping future people and so you can close the thread. So I got rid off Zorin and installed Linux Mint 17.2 to make sure it's not zorin only problem, and the problem persisted on mint. I reinstalled mint and installed the drivers from nvidia.com (which in itself had some problems but I managed to install them) and I only had 640x480 resolution. I googled for the solution of this and found that you need to change horizontal and vertical rates in xorg.conf and after you do that and reboot you get all the resolutions normally (yay 1080p finally). Here's the solution for people with my problem:
1. Install NVidia drivers (whether by command line, with .run or something 3rd)
2. Go to terminal interface with Ctrl Alt F1
3. Stop the GUI (service [GUI] stop) (lightdm,mdm etc.)
4. Go to the root folder of your system (repeat cd .. commands until you get to root)
5. cd etc/X11
6. Open xorg.conf with your editor of choice, and make sure to run as root (sudo nano xorg.conf)
7. Go down to the Monitor section and look for HorizSync and VertRefresh, and change them from HorizSync 28.0-33.0 VertRefresh 43.0-72.0 to HorizSync 30.0-83.0 VertRefresh 56.0-75.0 (just change the numbers)
8. Save it (ctrl+0 in nano) and reboot (sudo reboot 0 or harware reset or whatever you want)
9. Enjoy 1080p goodness!
If you still have some problems with my solution, email me at [email]a.sprecic@live.com[/email] and I'll see what we can do. Cheers!

---

