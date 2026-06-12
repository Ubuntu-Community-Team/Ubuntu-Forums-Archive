---
title: "Pangolin Volume Very Quiet"
date: 2009-05-27
forum: System76 Support
---

### Post by vgrisham on 2009-05-27
I just got my new-ish Pangolin pan4pn. What a sweet laptop. So far, I love it. 

I did a fresh install of Jaunty 64 and then installed the System76 driver. Subsequently, I did a System76 restore to factory defaults.

I am having one issue; the volume is very low when playing system sounds, music and dvds. Any tips on getting the volume louder? All my switches are maxed. All sound devices were set to auto-detect; after searching this forum, I switched the device to ALSA, but the volume is still way too low.

LSPCI shows that this has an Intel Corporation 82801I (ICH9 Family) HD Audio Contoller (rev 03)

Any tips on making this thing louder?

---

### Post by thomasaaron on 2009-05-27
Make sure PCM, Front, and Master are all turned all the way up. For your leisurely reading...

> First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10 or 9.04, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to Autodetect. Click the first Test button to see if you now have sound.   


---

### Post by vgrisham on 2009-05-27
Switching from Autodetect to ALSA and then back to Autodetect must have jarred something loose. She's loud now. Thanks.

---

