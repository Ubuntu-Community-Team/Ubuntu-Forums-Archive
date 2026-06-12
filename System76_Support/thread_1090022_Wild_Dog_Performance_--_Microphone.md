---
title: "Wild Dog Performance -- Microphone"
date: 2009-03-07
forum: System76 Support
---

### Post by TheBuzzSaw on 2009-03-07
I have a Wild Dog Performance that I bought spring of 2008. I've been wanting to get my microphone port working, but nothing I do seems to work. I tried many varieties of settings, but nothing gets it to receive anything.

I am running Ubuntu 8.10 64-bit. I have the System76 driver installed.

EDIT -- Nevermind! Why didn't anyone ever tell me about the gstreamer-properties console command??? I just ended weeks of hassle! XD

---

### Post by flukeairwalker on 2009-03-09
What command is this? I'm not familiar with it and I'm having trouble with the mic on my Pangolin working with Skype. I should clarify that my mic seems to work, just not with Skype.

---

### Post by thomasaaron on 2009-03-09
Flukeairwalker, that has nothing to do with gstreamer. It has to do with your setting in Skype.

First get your mic working in Sound Recorder. Then open Skype and go to Options > Sound Devices. Send the Audio In to "HDA Intel(hw:Intel,0).

---

### Post by TheBuzzSaw on 2009-03-09
> **thomasaaron said:**
> Flukeairwalker, that has nothing to do with gstreamer. It has to do with your setting in Skype.

First get your mic working in Sound Recorder. Then open Skype and go to Options > Sound Devices. Send the Audio In to "HDA Intel(hw:Intel,0).
Yup. That is exactly how I did it. Once I verified it was working in Sound Recorder, I started messing with the "Sound In" setting of Skype. Now, I Skype often! :)

TA, are you really still running 7.04? :P

@flukeairwalker -- The console command I mentioned lets you set some of your system sound settings (slightly different from the Preferences > Sound option). As TA said, if you already have your mic working in Sound Recorder, just mess with Skype itself.

---

### Post by thomasaaron on 2009-03-09
No! I saw that the other day and made a mental note to change it!
I'll make another mental note. :popcorn:

---

### Post by flukeairwalker on 2009-03-11
That was the missing piece. Thanks!

---

### Post by riseringseeker on 2009-03-14
I don't mean to hijack this thread, but I also have a Wild Dog and am using a USB headset/microphone with Skype.

Almost everything is working the way I would like - the ringing still comes over the speakers (and music I may be playing for that matter), and the conversation is strictly through the headset/mike.  It's a nice way of having things.

The only problem that I have with this setup is that I have **no** control over the headset volume.  I have to put it off my ear somewhat or I get blasted out.  

I've looked and looked in the volume control panel, but see no control for the USB headset/mike (I have all the options checked).  The mikes volume seems to work OK, but the "speakers" in the headset are *way* too loud.  I do have Skype set to "automatically adjust mixer levels".

If anyone can point out something I've missed, would appreciate it.

---

### Post by PatrickVogeli on 2009-03-14
As you are telling, I understand you aren't changing the device. The USB headset is actually not using you laptop's sound device, but it's a different one. To clarify: your laptop device would be HDA Intel and the USB headset, let's say, USB Sound or whatever.

To change it, open the audio control panel and there you should see the device options. My laptop has Device: HDA Intel, (Alsa mixer) as default, and it has a bunch of options, like OSS Mixer, and stuff ending with PulseAudio Mixer. There you should see the headset.

If you already checked this, I'm sorry, I missunderstood you

---

### Post by riseringseeker on 2009-03-18
> **PatrickVogeli said:**
> As you are telling, I understand you aren't changing the device. The USB headset is actually not using you laptop's sound device, but it's a different one. To clarify: your laptop device would be HDA Intel and the USB headset, let's say, USB Sound or whatever.

To change it, open the audio control panel and there you should see the device options. My laptop has Device: HDA Intel, (Alsa mixer) as default, and it has a bunch of options, like OSS Mixer, and stuff ending with PulseAudio Mixer. There you should see the headset.

If you already checked this, I'm sorry, I missunderstood you

Took me a bit to understand what you were saying, but it worked, though the left/right volume controls won't stay linked, at least I have control over the vilume now, thanks.

---

### Post by TheBuzzSaw on 2009-04-07
For what it's worth (to anyone else trying to make this work), in my Sound Preferences, my *Sound capture* is set to **HDA Intel STAC92xx Analog (ALSA)**.

---

