---
title: "Audio input with Plantronics USB headset using Skype with Ubuntu 10.04"
date: 2010-06-21
forum: System76 Support
---

### Post by volkerbradley on 2010-06-21
After spending quitle some time with this problem, here is what I did to get perfect audio using a Plantronics USB headset with Skype in Ubuntu 10.04:
Removed the .asoundrc file with the following two lines in it (if you have created this file):
pcm.pulse { type pulse }
ctl.pulse { type pulse }
As long as this file was present, I could not record sound from the Plantronics headset.
Then rebooted the computer
Do not open any other apps that might use sound like Firefox
Then click on the Gnome Audio Applet -> Sound Preferences -> Input -> and then put a dot in front of Internal Audio Analog Stereo
Then click on the Pulse Audio Applet -> Volume Meter (Recording). You will see a little movement in Front Left and Front Right from the Internal Audio Analog Stereo device
Now close the volume meter.
Return to Gnome Audio Applet -> Sound Preferences -> Input -> and then put a dot in front of the USB DSP v4 Audio Interface Analog Stereo line
Again click on the Pulse Audio Applet -> Volume Meter (Recording). You will see a little movement in Front Left and Front Right from the USB DSP v4 Audio Interface Analog Stereo device
Minimize, but do not close, both screens. Skype should work perfectly now
You can open Firefox now if desired.
If I closed the two screens, the sound input from the Plantronics headset would be lost.

---

### Post by isbiyanto on 2010-08-08
thanks for sharing :popcorn:

---

### Post by HotForLinux on 2010-08-09
Unbelievable!!!
Somehting must be wrong.

---

### Post by hifly1231 on 2011-02-05
Here's the solution that I found to use Skype 2.0.0.81 with my Logitech ClearChat USB Headset.  After reboot, Skype once again will let you choose which sound devices to use (just like Skype 2.0.0.72).

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

Just thought I'd share this with everyone.

:D

---

