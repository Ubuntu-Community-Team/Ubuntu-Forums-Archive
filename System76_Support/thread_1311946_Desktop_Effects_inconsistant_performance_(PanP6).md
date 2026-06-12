---
title: "Desktop Effects inconsistant performance (PanP6)"
date: 2009-11-02
forum: System76 Support
---

### Post by samh785 on 2009-11-02
On my PanP6 with Karmic the desktop effects become choppy after a while of use. This seems to be remedied by moving the wobbly windows around (this feature is never choppy it seems). Then the desktop effects will return to the original normal smoothness. The new smoothness lasts for less than 3 minutes usually and the wobbly windows must be wobbled again to remedy it. 

This seems very strange to me. I cannot say if this happened in Jaunty or not, because I upgraded this computer to Karmic as soon as I received it. 

My Nvidia driver version is 185, and my graphics card is a  512 MB DDR2 nVidia GeForce G105M.

---

### Post by HotShotDJ on 2009-11-02
> **samh785 said:**
> On my PanP6 with Karmic the desktop effects become choppy after a while of use. This seems to be remedied by moving the wobbly windows around (this feature is never choppy it seems). Then the desktop effects will return to the original normal smoothness. The new smoothness lasts for less than 3 minutes usually and the wobbly windows must be wobbled again to remedy it.I've had similar experiences with Compiz effects on the PanP5 (very similar hardware, exact same graphics adapter).  This is caused be the NVidia card's adaptive scaling -- that is, when the GPU is not being taxed, it will scale back, just like your CPU.  It takes a few moments for it to scale back up when you suddenly use something with a Compiz effect.  That is why moving a wobbly window smooths things out... it is getting the GPU to scale back up.  Really, it is not a bug, but a feature.

The newer 190.* driver allows you to change this behavior through System -> Administration -> NVidia X Server Settings.  For now, you can either scale back your Compiz effects (that's what I've done), upgrade to the new NVidia driver (covered elsewhere in Ubuntu Forums) or tweak your driver settings using RegistryDwords in your xorg.conf.  I've tested all three options, and have chosen to go with scaling back my compiz effects... just a bit.  What is left is still very impressive to those watching over my shoulder at work. :)  Once I get a few other issues sorted, I will likely upgrade to the 190 series drivers, though.  IMHO, the RegistryDwords option is an ugly hack, but it does work to a greater or lesser extent.

---

### Post by samh785 on 2009-11-02
> **HotShotDJ said:**
> I've had similar experiences with Compiz effects on the PanP5 (very similar hardware, exact same graphics adapter).  This is caused be the NVidia card's adaptive scaling -- that is, when the GPU is not being taxed, it will scale back, just like your CPU.  It takes a few moments for it to scale back up when you suddenly use something with a Compiz effect.  That is why moving a wobbly window smooths things out... it is getting the GPU to scale back up.  Really, it is not a bug, but a feature.

The newer 190.* driver allows you to change this behavior through System -> Administration -> NVidia X Server Settings.  For now, you can either scale back your Compiz effects (that's what I've done), upgrade to the new NVidia driver (covered elsewhere in Ubuntu Forums) or tweak your driver settings using RegistryDwords in your xorg.conf.  I've tested all three options, and have chosen to go with scaling back my compiz effects... just a bit.  What is left is still very impressive to those watching over my shoulder at work. :)  Once I get a few other issues sorted, I will likely upgrade to the 190 series drivers, though.  IMHO, the RegistryDwords option is an ugly hack, but it does work to a greater or lesser extent.

Ahh thank you. This definitely makes sense. I scaled back some of the compiz effects, and it is annoying me far less now :D

---

### Post by samh785 on 2009-11-06
I upgraded my Nvidia driver to the latest version, but I cannot locate the control to remove the adaptive scaling :P

---

### Post by HotShotDJ on 2009-11-06
> **samh785 said:**
> I upgraded my Nvidia driver to the latest version, but I cannot locate the control to remove the adaptive scaling :POpen NVidia X Server Settings.  Then find "PowerMizer" and select it.  Look at the PowerMizer Information and look just above the "Help" and "Quit" buttons.  You should see "Preferred Mode:"  with a drop-down menu with two options -- Adaptive or Prefer Maximum Performance.

If you don't see that, you might have not installed the nvidia-settings-190 package.

---

### Post by samh785 on 2009-11-06
> **HotShotDJ said:**
> 

If you don't see that, you might have not installed the nvidia-settings-190 package.
Yep, that was the problem :D 
Thank you so much!

---

### Post by HotShotDJ on 2009-11-06
> **samh785 said:**
> Thank you so much!Not a problem.  We System76 owners need to stick together.  I think it's like a club rule or something. Besides, if we just let Tom handle all the support questions, he'll be going home at the end of the day and kissing the dog before teaching his kids to fetch. :lolflag:

---

### Post by thomasaaron on 2009-11-06
> Besides, if we just let Tom handle all the support questions, he'll be going home at the end of the day and kissing the dog before teaching his kids to fetch.

That's not what I'm supposed to do? :lolflag:
[B]
THANKS FOR ALL THE HELP, GUYS![/B]

---

### Post by samh785 on 2009-11-07
ok, so now I am able to turn off adaptive scaling. The last little bothersome thing about this is saving that setting. When I turn the computer off the setting resets back to adaptive scaling.

---

### Post by HotShotDJ on 2009-11-07
> **samh785 said:**
> The last little bothersome thing about this is saving that setting. When I turn the computer off the setting resets back to adaptive scaling.I honestly don't know if it can save those settings.  For me, I wouldn't want to save such a setting, since I sometimes use my PanP5 on battery power, and the time it will last on a full charge is already just under 2 hours... I don't want to make it worse by defaulting the graphics card to its most power-hungry state.

Having said that (hopefully to dissuade you from wanting to do something like that ;)) you can try the following:

1) Open a terminal and type```
sudo nvidia-xconfig
```This will produce an xorg.conf file that NVidia X Server Settings understands.

2) Restart X (Log out, log back in... no need to reboot).

3) Now, you need to edit your new xorg.conf:```
gksudo gedit /etc/X11/xorg.conf
```Find the "Device" section -- it will look something like this:```
Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce G 105M"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```Add the following to this section (the line in [COLOR="Red"]red[/COLOR] is what you add):```
Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce G 105M"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
        [COLOR="Red"]Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
[/COLOR]
EndSection
```Using the line in red, we have told your G105M card to use regular adaptive scaling of the GPU whilst on battery power and Maximum Performance when plugged in.  To make it use Maximum Power all the time whether plugged in or not (NOT RECOMMENDED), use```
Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"
```

---

