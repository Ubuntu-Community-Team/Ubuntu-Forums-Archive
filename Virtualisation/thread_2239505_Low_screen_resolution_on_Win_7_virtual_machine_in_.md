---
title: "Low screen resolution on Win 7 virtual machine in Virtual Box"
date: 2014-08-14
forum: Virtualisation
---

### Post by johnyjj2 on 2014-08-14
Hi,
I have Ubuntu as main OS on my Lenovo computer and Windows 7 x64 on virtual machine. I want to have better screen resolution for virtual machine. I have found in the internet that in order to enable more screen resolutions I should install guest-on additions that come from Virtual Box. I have installed those and only have the following available: 800 x 600, 1301 x 722.
What else can I do to ensure I can choose higher screen resolution?
Regards!

---

### Post by TheFu on 2014-08-14
What resolution does the Linux desktop use?  If you run virtualbox full screen, then that should be the maximum resolution available.

**xrandr** will show the resolutions.

---

### Post by johnyjj2 on 2014-08-15
In VMWare I can choose up to 2560 x 1920 but unfortunately VMWare works extremely slowly in Ubuntu so Virtual Box is much better.


The command shows in Terminal as follows:


> Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
VGA-1-2 disconnected

And yes, I use full screen. It has some small problem in Virtual Box because there is something like border around virtual machine in full screen without Windows guest desktop (black screen around full screen machine so it does not use all available pixels in full screen).

---

### Post by TheFu on 2014-08-15
Have you increased the video memory?  For a desktop, use at least 64MB.
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) has settings to get vbox working faster.

---

### Post by SeijiSensei on 2014-08-15
I usually just bump the video memory up to the 128MB maximum.  Unless you're trying to use VB on a machine with less than two gigabytes of memory, this isn't a lot to allocate to video.  And if you are trying to use virtualization on a machine with less than two gigabytes, it's going to have horrendous performance if you even get it to work at all.

Disabling 3D video acceleration can also help.

---

