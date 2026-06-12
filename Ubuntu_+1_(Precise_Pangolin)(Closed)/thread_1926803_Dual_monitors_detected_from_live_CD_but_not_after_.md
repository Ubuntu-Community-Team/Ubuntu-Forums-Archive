---
title: "Dual monitors detected from live CD but not after install"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-02-16
I just tried an install of 12.04 on a secondary disk in my workstation, which has an nVidia GTS250 card driving two DVI-connected monitors. I downloaded the precise-desktop-amd64.iso dated 16 Feb, burnt a CD, and booted off it. When running off the live CD, both monitors (Dell U3011 in normal orientation and Dell U2311 in portrait orientation) are correctly detected under System Settings / Displays, and I can unmirror the displays and get a desktop spanning both monitors with each monitor at it's native resolution and correct orientation. 

However, after installation from the live CD to the hard drive, when I boot off the installed copy of 12.04, I only get a display on the U3011 monitor, and System Settings / Displays just shows a single monitor of type "Unknown", although it does recognise that the monitor supports 2560x1600 resolution. Running xrandr in a terminal gives:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 2560 x 1600, maximum 2560 x 1600
default connected 2560x1600+0+0 0mm x 0mm
   2560x1600      50.0* 
   2048x1536      51.0  
   1920x1440      52.0  
   1920x1200      53.0     54.0  
   1920x1080      55.0  
   1856x1392      56.0  
   1792x1344      57.0     58.0  
   1680x1050      59.0     60.0     61.0     62.0     63.0  
   1600x1200      64.0     65.0     66.0     67.0     68.0  
   1600x1024      69.0  
   1440x900       70.0  
   1400x1050      71.0     72.0     73.0     74.0  
   1360x768       75.0     76.0  
   1280x1024      77.0     78.0     79.0  
   1280x960       80.0     81.0  
   1280x800       82.0  
   1152x864       83.0     84.0     85.0     86.0     87.0     88.0     89.0  
   1024x768       90.0     91.0     92.0     93.0     94.0     95.0     96.0     97.0  
   960x720        98.0     99.0    100.0  
   960x600       101.0  
   960x540       102.0  
   928x696       103.0    104.0  
   896x672       105.0    106.0  
   840x525       107.0    108.0    109.0    110.0    111.0  
   832x624       112.0  
   800x600       113.0    114.0    115.0    116.0    117.0    118.0    119.0    120.0    121.0    122.0  
   800x512       123.0  
   720x450       124.0  
   720x400       125.0  
   700x525       126.0    127.0    128.0    129.0  
   680x384       130.0    131.0  
   640x512       132.0    133.0    134.0  
   640x480       135.0    136.0    137.0    138.0    139.0    140.0    141.0  
   640x400       142.0  
   640x350       143.0  
   576x432       144.0    145.0    146.0    147.0    148.0    149.0    150.0  
   512x384       151.0    152.0    153.0    154.0    155.0  
   416x312       156.0  
   400x300       157.0    158.0    159.0    160.0    161.0  
   360x200       162.0  
   320x240       163.0    164.0    165.0    166.0  
   320x200       167.0  
   320x175       168.0  

```
Any suggestions on where I can look for the problem? I ran a sudo apt-get update / upgrade after installation to pick up any updates since the CD image was created, but on reboot after applying those patches, the problem is unchanged.

---

### Post by starNIX on 2012-02-25
I am having the exact same issue.  The monitor being detected is on a VGA interface while the one on the HDMI interface is just not there.  My video card is an NVidia.

---

### Post by effenberg0x0 on 2012-02-25
I *think* it loads nouveau on the live session by default and, AFAIK, /usr/bin/gnome-control-center 'display' is only able to show dual monitors when running with it. 

For an example: I have blacklisted nouveau at /etc/modprobe.d/blacklist.conf and downloaded / installed NVIDIA-Linux-x86_64-295.20 driver (and Kernel Module) from NVIDIA's proprietary binary installer. In this setup, I can only see one monitor in System-Settings/Displays, but /usr/bin/nvidia-settings correctly shows me 3 displays connected and they work perfectly.

See what kernel module you're using (nouveau, nvidia) with:

lsmod | grep -i nouveau
lsmod | grep -i nvidia

Regards,
Effenberg

---

