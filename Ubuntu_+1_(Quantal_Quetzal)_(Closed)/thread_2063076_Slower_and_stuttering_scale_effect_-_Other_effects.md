---
title: "Slower and stuttering scale effect - Other effects are fine"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-26
This is up-to-date QQ with no alternative sources/packages. Hardware (CPU, GPU, RAM) broadly exceeds the requirements of Compiz/Unity. The desktop is blazing fast and so are all the effects. 

Except for Scale. It's taking too long to go from the beginning of the effect to the screen showing the scaled windows side-by-side and the transition is not smooth, there's some stuttering.

Increasing the speed and time-factor in ccsm / Scale makes the effect transition faster, but the stuttering is still there and the transition gets even less smooth. 

To test:
- Open some instances of any program. Example: Middle-click any application in the launcher any number of times.
- Left click the launcher icon of this app to trigger scale. 

or
- Open some instances of any program. Example: Middle-click any application in the launcher any number of times.
- Press Super+w

This was tested on Nvidia 304.48 and 304.51. I do not see this problem on PP with Nvidia and PP with Intel. I do not have ATI hardware to test.

I read somewhere that this could:

-  be related to wrong detection of refresh rate (workaround: disable "Detect Refresh Rate" in ccsm / Composite) and set it manually in ccsm or xorg.conf;
- only affect people using more than 1 monitor (workaround: test with only one monitor);
- be related to trouble with Nvidia's Dynamic TwinView (workaround: add Option "DynamicTwinView" "false" to /etc/X11/xorg.conf)

None of the above worked for me. Anyone else seeing it (or knows of a fix/workaround)?

It would be interesting to know:
- Am I the only one seeing it?
- Compare to your PP install. Do you see a significant regression in the speed/smoothness of Scale in current QQ?
- Does it only affects people using Nvidia? Or Intel and ATI too?
- Does it only affects people using more than 1 monitor?
- Do the mentioned workarounds fix it for you?

Regards,
Effenberg

---

### Post by nicholas.alipaz on 2012-10-11
This affects me, I have only tried the first fix in your list.  I will try the others too and report back if I have success.

---

### Post by nicholas.alipaz on 2012-10-17
Okay, I added the following:
Option "DynamicTwinView" "false"
to my /etc/X11/xorg.conf under Section "ServerLayout", like following:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
    Option         "DynamicTwinView" "false"
EndSection
```

Then I changed the Scale settings in ccsm to be Speed "10.0000", Timestep "0.1000".  This seems to have helped, I still see some slowness in response to my key binding in exposing the windows.

Best

---

### Post by nicholas.alipaz on 2012-10-17
For the record, I also had already set the refresh rate in ccsm and I did a compiz --replace and unity --replace after changing the xorg.conf, not sure if that was needed.

---

### Post by Milos_SD on 2012-10-17
I have nvidia and one monitor, and have this issue. It takes between 1 and 2 seconds for effect to start, and then there is a stutering when they are scalling. In PP I didn't have that issue, it was smooth as butter.

I never used "detect refresh rate" option in ccsm. Compiz in QQ have a lot of bugs and memory leaks. And a lot of effects are missing. :(

I only have nvidia, so can't test it with intel or amd.

---

