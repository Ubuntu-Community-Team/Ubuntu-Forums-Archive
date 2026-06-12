---
title: "Testing microphone"
date: 2010-10-26
forum: System76 Support
---

### Post by Dave_L on 2010-10-26
Ubuntu Netbook 10.04, model star3

I tested the microphone by recording five seconds of audio and playing it back:

$ arecord -d5 /tmp/test-mic.wav
$ aplay /tmp/test-mic.wav

It works, but the sound level is very low, even though the input volume is set to the maximum.  To hear the playback, I had to shout, or place my mouth an inch from the microphone.

Is this normal?

---

### Post by HotShotDJ on 2010-10-27
We're having the same problem with a star1 in 10.10.  I just did a clean install of 10.10 (Kubuntu this time) and still having difficulty with the internal microphone.

I've tried making adjustments using the PulseAudio Volume Control input devices tab -- I unlock the channels and then bring the "Front Right" channel down to 0,  This works temporarily, but with a very loud background humming.  Within a short time, the "Front Right" channel resets itself to the same level as the "Front Left" channel (usually 100% -- neither channel stays where I set it) and the microphone becomes super soft again.

The microphone HAS worked in the past using the above method. And at one point, it worked "out-of-the-box" (I believe that was with 9.10).

---

### Post by HotShotDJ on 2010-10-27
OK... I've done another clean reinstall and had the same problems... but I did some more research...

My problem with the pulseaudio resetting itself is actually a FEATURE of the Googletalk plugin for Linux.  I was able to disable it using [THIS LINK]("http://www.google.com/support/forum/p/gmail/thread?tid=389e3b70988a1711&hl=en").  Now the microphone works just fine after making the tweak using Pulseaudio Volume Control.  Note:  I did not have this issue on my PanP5... just on my friend's Star1.

Dave_L:  Try installing pavu.  It will show up under Sound and Video as Pulseaudio Volume Control.  Open it up and go to the "Input Devices" tab.  First, you'll need to unlock the channels (it is the button that looks like a shield) then slide either the Front Left or Front Right channel to 0.  Your microphone should begin working as expected.

---

### Post by Dave_L on 2010-10-27
Thanks, HotShotDJ, I'll keep your suggestion in mind.

But I'd like to get some feedback from System76 before making changes. Maybe it's a hardware issue, and my netbook is still within the 30-day return period.

---

### Post by Dave_L on 2010-10-27
I just tried repeating the previous test, using an external microphone, and it worked properly.

Then I repeated the test with the internal microphone, and now it works much better.  At least the volume is reasonable; there's noticeable background noise, but maybe that's unavoidable with this kind of microphone.

By the way, the internal microphone is "Microphone 3", the external jack is "Microphone 2".  I don't know what "Microphone 1" is.

---

### Post by syed.rakib.al.hasan on 2010-12-21
My microphone is not working at all.
donno what. i went to System > Preferences > Sound > InputTab
no matter what i do, the microphone level monitor does not show any response at all.
I installed pavuControl, still did not work.
Then i tried opening Sound Recorder from Application > Sound and Video. Over there also, when i click on record and no matter what i speak, yell or shout the volume level meter does not show any response.
What do i do???

---

### Post by isantop on 2010-12-21
First, on the hardware tab of the sound preferences dialog, make sure that the "Profile for selected device" is set to "Analog Stereo duplex".

Next, on the Input tab, ensure that the radio button next to "Internal Audio Analog Stereo" is filled in. Then, if there is a Connector dropdown, try each of the settings in that. It should work on one of those.

---

