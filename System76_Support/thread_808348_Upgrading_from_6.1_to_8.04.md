---
title: "Upgrading from 6.1 to 8.04"
date: 2008-05-26
forum: System76 Support
---

### Post by awright on 2008-05-26
Koala model MP915-B(C)

When loading a Ubuntu 8.04 live CD, I get a blank screen and the monitor turns off.

Any suggestions?

Thanks,

Allen

---

### Post by cdtech on 2008-05-26
Why don't you upgrade using the command line?

---

### Post by SkonesMickLoud on 2008-05-26
When you're making that large of a jump in distro's, it's faster and easier to burn your Home directory to a CD/DVD format your disk/partition and install 8.04 fresh.

Otherwise you would have to upgrade to each release separately:

6.1 >> 7.04 >> 7.10 >> 8.04

---

### Post by thomasaaron on 2008-05-27
Also, you will probably need to use "Safe Graphics Mode." for it to work correctly.

---

### Post by cdtech on 2008-05-27
> **SkonesMickLoud said:**
> When you're making that large of a jump in distro's, it's faster and easier to burn your Home directory to a CD/DVD format your disk/partition and install 8.04 fresh.

Otherwise you would have to upgrade to each release separately:

6.1 >> 7.04 >> 7.10 >> 8.04

Just saying. I did mine from 6 - 8 on the command line, no problems. I also had a lot of programs installed that I wanted updated as well. I can see your case where you don't have anything worth keeping though.

Good Luck....

---

### Post by schryer on 2008-05-29
I have almost the same problem with the exact same computer MP915-B(S).

I installed from scratch (as I always do) and all graphics give a blank screen.  This is also true of the 7.10 distribution.

There is a graphics conflict with this machine.  The graphics card is an Intel 915GM/GMS/910GML

This thread explains that there is a problem outputting graphics to the external screen (the MP915-B(S) is essentially a laptop without a screen), so I suspect that the video is working properly for the screen that does not exist)
[http://ubuntuforums.org/showthread.php?t=393851](http://ubuntuforums.org/showthread.php?t=393851)

This thread explains that there is a new Intel driver available:
[http://ubuntuforums.org/showthread.php?t=113829](http://ubuntuforums.org/showthread.php?t=113829)

However, it is not a simple install (kernel recompile and loads of extra packages needed for compiling the package itself). Furthermore, Intel only shows that it is compatible with Ubuntu 6.10.

It would be nice to have this graphics card work with new versions of Ubuntu, otherwise I may be forced to downgrade again.

Is anyone able to help with this problem?

---

### Post by thomasaaron on 2008-05-29
Did you try installing in Safe Graphics mode?

---

### Post by schryer on 2008-05-30
The install works just fine, even using graphics, the problem occurs when it tries to start the x-server, it just gives a blank screen and no errors.  I suspect that this means that it is outputting the graphics to the wrong head of the dual head video card (there is only one on this computer, but the card supports two).

Note:  The graphics work fine in the other operating systems installed on this computer.

Any other thoughts?

---

### Post by thomasaaron on 2008-05-30
I think I've seen this before on older chipsets. It ended up being incorrect (or non-existent) refresh rate settings for the monitor in xorg.conf.

If you can boot into recovery mode...

Back up your xorg.conf...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then open it up...
sudo nano /etc/X11/xorg.conf

Change the monitor entry to include the correct refresh rates. Below is a sample listing...

```
Section "Monitor"
Identifier "Monitor1"
VendorName "DEL"
ModelName "DELL P1110"
HorizSync 29-121
VertRefresh 50-180
EndSection 
```

Then save the file...
Ctrl-X
Y

Then reboot...
sudo reboot now

---

### Post by schryer on 2008-06-05
To make a long story short, changing the monitors section worked.  

Thanks for the tip!

---

