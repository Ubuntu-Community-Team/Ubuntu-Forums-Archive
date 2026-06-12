---
title: "Pangolin 8.10 Skype Sound &amp; Mic Fixed"
date: 2009-04-16
forum: System76 Support
---

### Post by bill516 on 2009-04-16
I have been trying to configure Skype on my new Pangolin and posts here have been helpful.  I have sound when I make a Skype test call and I have video when I test that capability.

Sound was a problem.  Initially there was none at all and the microphone did not work with Skype.  Putting together several posts on this forum here are the settings that appear to work for my Pangolin using Skype.

In Ubuntu System/Preferences/Sound everything tests as it should with default settings.

Next, make certain keyboard sound is set to maximum for testing purposes.

In Skype Sound Devices are as follows

Sound In:  HDA Intel (hw:Intel,0)
Sound Out: Pulse
Ringing: Pulse

This works and it is worth a try if you are experiencing lack of sound on Skype and/ a seemingly inoperative microphone.

---

### Post by thomasaaron on 2009-04-16
Way to research it!

---

### Post by andrewdied on 2009-04-16
That worked great!  And great timing for me, since making skype work was on my to-do list.  One note is that for me on my Serval the sound in was the plug-in mic, not the internal mic.  


> **bill516 said:**
> I have been trying to configure Skype on my new Pangolin and posts here have been helpful.  I have sound when I make a Skype test call and I have video when I test that capability.

Sound was a problem.  Initially there was none at all and the microphone did not work with Skype.  Putting together several posts on this forum here are the settings that appear to work for my Pangolin using Skype.

In Ubuntu System/Preferences/Sound everything tests as it should with default settings.

Next, make certain keyboard sound is set to maximum for testing purposes.

In Skype Sound Devices are as follows

Sound In:  HDA Intel (hw:Intel,0)
Sound Out: Pulse
Ringing: Pulse

This works and it is worth a try if you are experiencing lack of sound on Skype and/ a seemingly inoperative microphone.

---

### Post by atorch on 2009-06-19
> **bill516 said:**
> Sound In:  HDA Intel (hw:Intel,0)
Sound Out: Pulse
Ringing: Pulse

Before applying the changes above, I would leave a message with the Skype test call and it would play back silence.

After, the test call plays back static.

Any suggestions?

Edit:  Ubuntu's Sound Recorder also plays back static, so it isn't just Skype.

---

### Post by thomasaaron on 2009-06-20
atorch, if you're using a System76 machine. Contact me at support(at)system76(dot)com, and I'll send you screenshots of how to set it up.

---

### Post by hkarl629 on 2009-06-20
Your post was just what I needed. Those settings for Skype got it working on my Serval.

Thanks,

hkarl629

---

### Post by ddiamantaras on 2009-06-26
Same question as above, with a brand new Pangolin and Ubuntu 9.04. I have set up the preferences as the first poster said to do, and I still do not hear myself in a Skype test call. Thanks in advance for any help!
Dimitrios

---

### Post by thomasaaron on 2009-06-26
ddiamantaras, you first have to set up your system so that you can record with Applications > Sound & Video > Sound Recorder. Then the above settings for Skype will work. 

First do this to open all audio channels...

> First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10 or 9.04, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to Autodetect. Click the first Test button to see if you now have sound.   

Then see the attached screenshots.

---

### Post by ddiamantaras on 2009-06-26
Thanks thomasaaron, your suggestions resulted in a successful Skype test message.

---

### Post by Jozza The Wick on 2009-07-25
bill516 - this worked great for me too - thanks very much!

---

