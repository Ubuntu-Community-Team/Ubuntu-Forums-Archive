---
title: "Audio not working"
date: 2016-09-10
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-09-10
Hello,
the Audio in my yakkety installation worked fine for months. Now, for some reason, it doesn't work anymore. I don't know if this is due to an update or something else, but could you help me please? I really don't know what I should check...

---

### Post by grahammechanical on 2016-09-10
On my yakkety system an update the other day reset the sound settings for audio output to Line Out - built in audio. I usually have it set to HDMI/DisplayPort2 to use the audio out of the Nvidia graphic card.

It is not the first time a reset like this has happened. It results in all sound being muted even though sound settings is not muted. It is just a switch in output devices.

Regards

---

### Post by enricobe on 2016-09-11
> **grahammechanical said:**
> On my yakkety system an update the other day reset the sound settings for audio output to Line Out - built in audio. I usually have it set to HDMI/DisplayPort2 to use the audio out of the Nvidia graphic card.

It is not the first time a reset like this has happened. It results in all sound being muted even though sound settings is not muted. It is just a switch in output devices.

Regards
Hi, you are right. I looked at Audio Settings and found that the output was set to "HDMI" and the sound test didn't work. I changed it in "5.1 HDMI" and pressed the "sound check" button. The sound test window opened up and I have been able to do the test with success.
When I closed the sound test windows, the "5.1 HDMI" setting was disappeared....

Now it works. Thank you!

P.S. should we report is as a bug?

---

