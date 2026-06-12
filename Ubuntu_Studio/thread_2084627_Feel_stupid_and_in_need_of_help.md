---
title: "Feel stupid and in need of help"
date: 2012-11-16
forum: Ubuntu Studio
---

### Post by nickgee667 on 2012-11-16
So... Normally I don't break stuff, right... Well, it's been a long day.  

I clicked on the audio icon in the status bar tray, and went into sound settings.  For some ungodly reason, I turned something off, and now JACK and Ardour have no sound... Funny thing, though, prior to turning this mystery item off (I can't recall what it was), I couldn't play WAV files in any playback application, but now I can.

So... I can't find out how to turn it back on, or configure it at all, it is completely gone.  I'm attaching an image of the audio window... But it seems to me there used to be a few more tabs, one of which is not there now is the one I made the unwanted change on...

Please help.

---

### Post by CrocoDuck on 2012-11-16
EDIT: Watching better the picture you posted I can see that a parameter is setted on the HDMI Output. If you need the output from the analog output or speakers maybe you have to set a different thing for it. Make sure that output devices and input devices are the ones you want to use for that purpose.

Hi. I experienced some similar issue too using ubuntu studio 12.04. So I choosen to use alsamixer to make all my adjustments for devices, channels and levels. In a terminal:

```
alsamixer
```You'll find in the window all the help you need to try to configure your devices (is very easy). In my case I found that alsamixer is more effective and reliable than other tools. Sometimes it happens to me this odd thing: If i turn off the pc with a cable plugged into the pc's audio output the next boot the system thinks that something is still plugged, even if I unplugged it, and to make him to understand that sound has to come out from speakers I have to plug again a cable, then I have to unplug it. Maybe something similar is happening to you...

---

### Post by nickgee667 on 2012-11-16
you know, thanks for the reply, but I've resolved the issue in the same accidental fashion in which I caused it.

---

### Post by nickgee667 on 2012-12-27
Oh wow... I'm now having the same problem.  No output device is shown, just "Dummy output" and I've done NOTHING to any of the audio settings this time.  Was working fine last night, was trying to get FF7 installed through wine, but didnt change any audio settings, then when I turn it on this morning: no sound...  Ugh...

Still my experience is better than Windows.

---

### Post by CrocoDuck on 2012-12-28
:confused:... Maybe a closer look can help us:

Repost the output of this guys:

```
cat /proc/asound/cards
``````
cat /proc/asound/devices
``````
cat /proc/asound/pcm
``````
arecord -l
``````
aplay -l
``````
cat .jackdrc 
```

---

### Post by nickgee667 on 2012-12-31
Hahaha, you know what I have no frigging idea what I did (again) but I accidentally fixed it (again).  Definitely the most fun I've had with an OS yet.  :)  Thanks for the post though~

---

