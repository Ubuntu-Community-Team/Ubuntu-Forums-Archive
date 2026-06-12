---
title: "GazP1 upgrade problems (and some solutions)"
date: 2008-11-10
forum: System76 Support
---

### Post by nerdboy4200 on 2008-11-10
Over the weekend, I decided to upgrade from Hardy to Ibex. The base update (using the update manager) went very smoothly. But several problems have arisen since that easy upgrade:

1) Sound did not work correctly. It did not have the appropriate input controls like under Hardy. In fact, no microphone input was working (internal and external), but there is a temporary fix. :)

Based on the documentation and some early probing of the soundcard under Hardy, I think that the soundcard is being improperly detected. It is detecting the base device properly (Analog Devices AD1986A), but it does not load the proper mixer and extra drivers. The fix for this is to currently add:

**options snd-hda-intel model=laptop-automute**

to /etc/modprobe.d/alsa-base file. Under Hardy, this would have been detected as laptop-eapd.

thomasaaron - you might want to add this into the system76 driver (unless this fix is not needed in an upcoming kernel)

2) I have discovered that the internal intel 3945 abg wireless card does not work under Ibex. This can be attributed to this line that I found in dmesg:

**[   23.911006] iwl3945: Unknown symbol lbm_cw_print_ssid**

I had installed the backports package (since I needed it under hardy also). I wonder if it is possible that I can use the one from the kernel package (not the backport edition)?

Other than that, and a few minor details (VPN and the like) I am currently happy with the upgrade.

-Josh

**Update:** Ok, so this doesn't work perfectly, the audio does not play through the internal speakers, it will only play through the headphones. So it is not a perfect fix...

thomasaaron - am I missing something here about my machine? Should I switch back to the auto-detected driver for now?

---

### Post by thomasaaron on 2008-11-10
That's the first I've heard of a possible sound regression with Intrepid. In fact, I've found computers that had sound regressions under Hardy now working perfectly in Intrepid.

Let's cover some basics before you use that kernel option.

1. Double-click your speaker icon. In the resulting window, click Preferences. Make sure all of the available checkboxes are selected.

2. No, go to System > Preferences > Sound and make sure all of the drop-down boxes are set to Pulse Audio

Did that help?

---

### Post by nerdboy4200 on 2008-11-10
> **thomasaaron said:**
> 
1. Double-click your speaker icon. In the resulting window, click Preferences. Make sure all of the available checkboxes are selected.


I checked all the items in the volume controller. I also tried recording audio while changing the items, it didn't work.

> **thomasaaron said:**
> 
2. No, go to System > Preferences > Sound and make sure all of the drop-down boxes are set to Pulse Audio

Did that help?

I also tried that. It made no difference. By using the pulse volume monitor for inputs and it does not show any difference.

I also tested using audacity, sox's rec program, the Sound Recorder program, and skype. 

-Josh

---

### Post by thomasaaron on 2008-11-10
Thanks. Probably the best way to proceed with this one is to file a bug report here...

[http://launchpad.net/system76](http://launchpad.net/system76)

We'll have a look at it and see what we can figure out.

---

### Post by nerdboy4200 on 2008-11-10
A bugreport has been added:

[https://bugs.launchpad.net/system76/+bug/296403](https://bugs.launchpad.net/system76/+bug/296403)

-Josh

---

