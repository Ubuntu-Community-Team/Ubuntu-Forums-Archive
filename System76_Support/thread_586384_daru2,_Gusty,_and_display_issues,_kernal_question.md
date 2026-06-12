---
title: "daru2, Gusty, and display issues, kernal question"
date: 2007-10-22
forum: System76 Support
---

### Post by GregCwx1 on 2007-10-22
Since an upgrade to Gusty from Feisty on the Darter Ultra laptop I have been unable to change screen resolution to anything other than 1280x800. Under Feisty I was able to switch to a higher "virtual" screen resolution using the 
gnome-display-properties applet.

Also, when I use displayconfig-gtk either from the System -> Admin -> Screens and Graphics of from the terminal (displayconfig-gtk) I see the "screen" is "unknown and graphics card is generic vesa. Shouldn't these be better defined by the configuration?

When I use the test button on the screen or graphics card my screen goes blank for a moment and then returns this error:

displayconfig-gtk: Fatal IO error 104 (Connection reset by peer) on X server :9.0.

and displayconfig-gtk crashes.

Anyone have a xorg.conf file for the darter ultra or know of a way to go back to the settings I had?

Also, has anyone had any issues with the different kernels offered in 7.10. My menu.lst has two:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.20-16-generic

in addition to the recovery entries.

Why the two kernels? Any reasons to use one over the other?

Thanks for any help you can provide!

-Greg

---

### Post by palintheus on 2007-10-22
If you upgraded the likely reason you have 2 kernels is because one is the previous kernel, prior to the upgrade. I had to use the 2.6.20* one to get sound to work on my daru2.

---

### Post by thomasaaron on 2007-10-22
> Also, when I use displayconfig-gtk either from the System -> Admin -> Screens and Graphics of from the terminal (displayconfig-gtk) I see the "screen" is "unknown and graphics card is generic vesa. Shouldn't these be better defined by the configuration?

See how many of your darter's issues this fixes:

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

In the resulting window, choose *ALL* defaults *EXCEPT*:
* for the video driver, select "intel"
* for the resolutions, select all of them

---

### Post by GregCwx1 on 2007-10-22
Thanks for responding thomasaaron...

I did a reconfig on the xorg.conf file as suggested and it did result in
other "lower" resolutions being made available as well as having the
Intel card recognized by gtk-displayconfig.

However, I still cannot switch a a higher vertical screen resolution that
was available before. I think it was something like 1280x1024 which
was partly virtual because you had to scroll down to see what was on
the desktop. I'm stuck at 1280x800 which fits. I liked to switch between
the two on occasion but that option is not being recognized even though it
now is listed in xorg.conf.

Greg

---

### Post by GregCwx1 on 2007-10-23
I've cleaned up /etc/X11/xorg.conf considerably and it seems to have helped speed up the start of the X server when first logging in using GDM. However, I'm still stuck at no higher screen resolution than 1280x800.

Someone please correct me if I'm wrong but I distinctly remember changing to a higher vertical resolution under Feisty. On daru2 with Feisty this desktop resolution was greater than the laptop screen resolution so you could use the mouse to move around this larger desktop. It was useful given the smaller screen on the Darter. It was easy to switch between the higher resolution (1280x1024?) and the standard 1280x800.

I'm beginng to think it might be related to the newer version of X under Gusty but I can't get the GDM to know about anything higher than 1280x800.

Am I missing something? Help!

Thanks,

-Greg

---

### Post by thomasaaron on 2007-10-24
I've used higher resolutions on the DarU2 using an external monitor, but I don't remember a higher resolution available for the LCD.

Once I clear my plate of the Gutsy release issues, I can re-load Feisty and give it a lookie-see.

Best,
Tom

---

### Post by GregCwx1 on 2007-11-02
I'm still puzzled about the LCD display capabilities of the daru2 under Gusty. I am almost certain I was able to achieve a higher virtual display resolution than 1280x800 under Feisty. So far, I have been stymied from doing so with Gusty. I've tried different xorg.conf configurations all to no avail. But I'm being careful with the xorg.conf settings and I'm not an expert.

This morning I was trying out xrandr and here's the outout:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 261mm x 163mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right)
TV disconnected (normal left inverted right)

This looks like screen 0 should be able to go as high as 1280x1280. This would
probably be a virtual size because the XGA specs say the LCD resolution is 1280x800 which is what is working fine.

If anyone has some examples of xorg.conf files that are working for them. Or if anyone has memories of higher virtual screen resolution under Feisty, I'd sure like to hear from you. Thanks and have a great weekend!

---

### Post by thomasaaron on 2007-11-02
Were you, by chance, using 915resolution to achieve higher resolutions?
I've not tried it on the Darter2, but it just might do the trick.

See this how-to:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

