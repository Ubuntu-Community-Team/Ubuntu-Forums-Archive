---
title: "Gazelle Performance microphone problems."
date: 2007-05-07
forum: System76 Support
---

### Post by sail on 2007-05-07
Just got my new lappy today, and very pleased blah blah blah. I can't for the life of me get my mic to work. It's a computer mic and I'm plugging it into the ports right below the touchpad. I've been testing it with Skype and so far no dice. Suggestions?

---

### Post by thomasaaron on 2007-05-08
Hi, sail.

If you're trying to get it to work with Sound Recorder, it won't happen. Try Jokosher or GnuSound.

Here are some precautions about GnuSound:
> GnuSound Crashes if it is not set to OSS.
To do this, open GnuSound and go to:

Settings > Preferences
Click on the Playback tab.
Make sure "Available Audio Drivers" is set to OSS. 

Also, make sure your microphone is not muted.
Check settings in these locations:

1. Double click on speaker icon in upper right.
2. In the resulting window, look at settings within all tabs
3. Also go to File > Change Device. Make sure you are set to the Alsa mixer.
4. Also click Edit > Preferences (select all checkboxes)

---

### Post by sail on 2007-05-08
Ok, I can hear my voice through the speakers, but I can't record anything(GnuSound and Skype).

---

### Post by thomasaaron on 2007-05-09
If you can hear your voice through the speakers, it is a configuration problem with a) your sound controls, or b) the recording program.

The following thread shows pics of how you should be configured...
[http://system76.com/forums/viewtopic.php?t=1561](http://system76.com/forums/viewtopic.php?t=1561)

---

### Post by sail on 2007-05-09
Alright, I got it all figured out. Thanks, and I'm enjoying my laptop.

---

### Post by thomasaaron on 2007-05-10
I'm glad you got it worked out.

Could you share the fix so that there is a record of it on this forum for others who might experience the same difficulties?

Best,
Tom

---

