---
title: "gazp5, 8.04 built-in mic troubleshooting"
date: 2009-01-01
forum: System76 Support
---

### Post by akfrancis on 2009-01-01
I've tried all the volume control settings in this thread:
[url]http://ubuntuforums.org/showthread.php?t=712172&highlight=gazp5+microphone&page=3
...but the built-in mic in my gazp5 running 8.04 produces constant static (and repetitive loud clicks depending on the format or setting) and only faint playback of the desired sound through the speakers.  I've only tried Sound Recorder so far, and ALSA mixer with PCM are the only selections in Sound Preferences that will produce any playback besides static/clicks.  Ideas?
Thanks--Chris

---

### Post by thomasaaron on 2009-01-02
Hi, Chris.

Did you try these settings?
[http://ubuntuforums.org/showthread.php?t=712172&highlight=gazp5+microphone](http://ubuntuforums.org/showthread.php?t=712172&highlight=gazp5+microphone)

ALSA doesn't provide the highest quality sound with the *internal* mic on the GazP5. It doesn't in Hardy or Intrepid. It *can* be made to work, but it will always have some static.

To get rid of the clicking, you probably need to drop your PCM a bit. You also will need to play with the Digital and Capture sliders. They have to be balanced just right.

On the other hand, an external mic works great.

---

### Post by akfrancis on 2009-01-03
Thanks Tom, 

I did try those settings and can get the clicking to subside--voice just remains faint.  I'll play with the sliders a bit, but will probably just get an external mic before using skype.

Chris

---

