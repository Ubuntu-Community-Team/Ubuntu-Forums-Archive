---
title: "FL91 laptop: volume buttons going bad? or caused by update?"
date: 2009-04-01
forum: System76 Support
---

### Post by aaronLund on 2009-04-01
8.10 here.

For the past couple of days sound has been really weird on this laptop.

I push the 'fn' + 'f8' key to turn the volume up and it has 3 settings: volume all the way down, volume half way up, and volume all the way up.

Also, when sound is working, I get a very loud "click, click, click" through the headphones.  Loud enough that it is audible with the headphone just laying on my desk.

Pretty frustrating.  Anyone else experiencing anything like this?

Thanks.

---

### Post by thomasaaron on 2009-04-01
It definitely sounds like a configuration issue.

The clicking is *probably* caused by your PCM slider being set way too high. Follow the instructions below to make sure everything is set up correctly.

> First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.   First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, make sure your Sound Device is set to "HDA Intel (Alsa Mixer)." Then go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.   

---

### Post by aaronLund on 2009-04-01
thanks, thomasaaron.

> Second, double-click on the speaker icon in the upper right corner of your screen. 

I don't have a speaker icon up there.  i used to but don't anymore.  how do i get it back?

thanks!

EDIT:  found it here [http://ubuntuforums.org/showthread.php?t=197980](http://ubuntuforums.org/showthread.php?t=197980)

So, I've got sound back now (that's good!).  However, there seems to be a bunch of white noise even with no sounds playing.  I can turn down volume faders but then my sound goes down too.  Is there some rogue fader on that I can't find?

---

### Post by rose1 on 2009-04-01
I'm having similar problems with Dell Inspiron 1525.  I downloaded Hardy H, thus removing Gutsy G - and my volume/sound.   How can I get this back?

---

### Post by thomasaaron on 2009-04-01
> However, there seems to be a bunch of white noise even with no sounds playing. I can turn down volume faders but then my sound goes down too. Is there some rogue fader on that I can't find?

Try muting your mic sliders. Sounds like you may be getting some feedback.

---

### Post by aaronLund on 2009-04-01
> **thomasaaron said:**
> Try muting your mic sliders. Sounds like you may be getting some feedback.

Yep. That was it.  $5 into the dummy jar for me.

Hey...I'll be broke soon if I keep this up!

;-)

Thanks.

---

