---
title: "new wild dog, no sound"
date: 2009-07-14
forum: System76 Support
---

### Post by DukeLuke on 2009-07-14
Hi all,

Just got my new wild-dog, assembled it, but no sound. Can anyone help? 

Thanks in advance!
DL

---

### Post by TheBuzzSaw on 2009-07-15
Which jacks are you using? Front or back?

---

### Post by DukeLuke on 2009-07-15
I am using the back jack (green), but have tried the other jack on the top (green) of the lian case. 

I have a intel P45SG MB and using Logitech SPK X240 3PCS.

Any help you can provide is appreciated. 

I tested speakers on a windows laptop and they work......

DL

---

### Post by thomasaaron on 2009-07-15
First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10 or 9.04, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. 

On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted. PCM is your main system amplifier. All other volume settings are relative to it.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to Autodetect. Click the first Test button to see if you now have sound.

---

### Post by DukeLuke on 2009-07-15
Tom - tried everything you asked and no joy! Although, when I clicked on "System76 drivers" install, nothing really happens other than a another blank window pops up.

Not sure what else I can do to get the sound working. Any other helpful ideas?

Luca

---

### Post by thomasaaron on 2009-07-16
Can you post screenshots of each tab of your sound control box, as well as one of System > Preferences > Sound? 

(I'd post screenshots of mine, but it is not available at the moment.)

---

### Post by katycorp on 2009-07-16
I am having the exact same problem. I attached a screenshot of my sound control panel and sound management boxes.
Thanks,
Kaitlin

---

### Post by DukeLuke on 2009-07-16
I booted into the live cd to test sound and it works. I rebooted into my profile and tried uninstalling and reinstalling the alsamixer, but still no luck. I then reformatted and installed a new fresh copy of Ubuntu 9.04 (64bit) and sound is now working. I then downloaded system76's driver .deb and installed it. All hardware seems to be functioning normal at this time.

---

### Post by katycorp on 2009-07-17
Reinstalling Ubuntu is not an option for me right now. When I go to install the System76 drivers it tells me that all the drivers on my system are provided by Ubuntu. Is there some more troubleshooting  I can do for this problem?
Thanks,
Kaitlin

---

### Post by thomasaaron on 2009-07-20
Hi, Kaitlin. 

Welcome to the hoard.

On System > Preferences > Sound, at the very bottom, highlight PCM instead of Headphones. This will allow your keyboard volume control keys to control the actual system volume.

In your volume control panel (the one you get when you double-click your speaker icon), turn up your PCM, MASTER, and FRONT.

Also, show screenshots of your other tabs.

---

### Post by memeri on 2009-09-28
I have the same problem [wild dog wilp4, Intel DP45SG mobo, logitech X-240 speakers (2.1 sound)]. Plugged into green socket -- either top or back. Running sys76 driver reports all drivers are supplied by ubuntu (Is this true? -- the grafics and wifi cards are proprietary). Also, input errors elicit system beeps, as though the driver really is not installed. Did we solve this problem yet? Thanks!

---

### Post by thomasaaron on 2009-09-28
Please send an email to support...at...system76...dot...com and I'll send you screenshots to help you configure it.

---

### Post by memeri on 2009-09-29
My problem was a just loose connection. I fixed it just by making sure all the connections were tight. Duh. Thanks especially to Tom for his patience.
Now the sound works nicely.

---

### Post by riseringseeker on 2009-09-30
I know I am jumping into this late...

When I got my Wild Dog, I also had troubles with the speaker.  IIRC, what I did was add "Mux" or "Surround", perhaps both to the preferences.  I seem to remember it being "Mux" though.  One of the other worked, couldn't hurt to try.

---

