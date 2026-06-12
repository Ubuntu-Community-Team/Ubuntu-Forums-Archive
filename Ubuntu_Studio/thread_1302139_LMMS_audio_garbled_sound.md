---
title: "LMMS audio garbled sound"
date: 2009-10-26
forum: Ubuntu Studio
---

### Post by Arcturus691 on 2009-10-26
Hello,
I was using the newest version of LMMS and it started producing stuttering and garbled audio.  LMMS played clearly for the first two days and then this afternoon it was garbled.  I cannot find anyway to fix the issue. If anyone has any ideas, they would be greatly appreciated.

_My Config_:
-Nvidia NForce Main Board
-AMD64 Athlon 2.4Ghz
-2 X 512mb of Dual DDR 533
-card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
-Ubuntu Studio 9.04
-LMMS ver 0.4.5 updated from version that comes with Ubuntu Studio via update manager

_Things I have tried_:
[LIST=1]
[*]Reinstall LMMS via synaptic

[*]Changing buffer to 2048 in LMMS & buffer in Jack server to 2048
[*]Tried setting "Settings for Alsa"  to:  hw:0,0 (lmms will not let me set this, starts with audio settings until I put in "default")
[*]Set sound settings from auto to Alsa (System/Preferences/Sound)
[*]going back to a single screen from a dual config  (Nvidia video  ver 180)
[*]disabling compiz desktop effects
[/LIST]
Problem occurs with Sound Blaster Live! MP3 sound card with nvidia on board disabled in BIOS (currently using on board nvidia sound w/ SB card not installed)

_**Update**_:  I recorded one song to .wav from LMMS and none of the stuttering and/or noise could be heard in the recording.  this must be some sort of playback issue in LMMS.  OK also noticed that when testing sound in System/Preferences/Sound that I get popping clicking sound.  This is looking more like an ubuntu sound issue not LMMS.

I reinstalled pulseaudio  via synaptic and the problem stopped, however about 5m later it is now happening again.  What is wrong with pulse audio that it could be corrupted that easily?  Does this have something to do with the realtime kernel?

---

### Post by Arcturus691 on 2009-10-27
I ended up giving up and reinstalling.  My new hard drive just arrived anyways.  

**Some of the suspected culprits are**:
[LIST=1]
[*]Xbindkeys
[*]Nvidia and their closed source drivers with xinemera enabled (need to ditch nvidia next time for something with open source drivers)
[*]changing from 2 channel to 6 with pulse audio
[/LIST]

This was definitely not an issue with alsa but an issue with pulse audio.
Really wish ubuntu dev's had waited before switching to pulse,  IMHO changing to pulse was premature.  It stills skips makes noise if I even move a screen in X.   From what I heard those who dropped pulse altogether and back to alsa are not having these issues.  I am reluctant to do this as it is packaged with ubuntu desktop.

---

### Post by AutoStatic on 2009-10-27
Hello Arcturus691, I use JACK instead of PulseAudio and then LMMS still skips when moving windows, but that's mainly due to the JACK support of LMMS that is still a bit buggy. There are some other options though, you could try killing PulseAudio with the help of a startup script, that's what I do. I use a special music account for that, for my day to day account I leave PulseAudio as is.
If you want to I could try helping you out setting up a similar configuration.

Best,

Jeremy

---

### Post by Arcturus691 on 2009-10-28
Hi Jeremy thanks for the response.  

I would be interested in that script.  If I had to guess, I'll bet the script is running pulseaudio killall.   It makes sense to use jack, I know that LMMS starts the jack server when starting anyway.   What is interesting is currently I am running LMMS 0.4.2 without the nvidia video drivers, 2 ch sound and LMMS is working really good.   Now I need to do one thing at a time and test LMMS after each change.  
Which version of LMMS are you running?

---

### Post by AutoStatic on 2009-10-28
I'm running 0.4.5.
The script is dead simple:
```
#!/bin/bash

killall -9 pulseaudio &&
sleep 3
/usr/bin/jackd -R -m -dalsa -dhw:0 -r48000 -p256 -n2
exit
```

Of course you have to adjust the JACK settings to your specific needs.
You could also start Qjackctl if you want to instead of just JACK:
```
#!/bin/bash

killall -9 pulseaudio &&
sleep 3
/usr/bin/qjackctl.bin -s -p YourProfileNameHere
exit
```

If you use this script you also have to create a client.conf file in ~/.pulse/ with one line:
```
autospawn = no
```
To prevent PulseAudio from respawning after killing it.
LMMS 0.4.2 does not start a JACK instance AFAIK, besides JACK support in 0.4.2 is very, very poor. Are you sure you're using it with JACK?

---

