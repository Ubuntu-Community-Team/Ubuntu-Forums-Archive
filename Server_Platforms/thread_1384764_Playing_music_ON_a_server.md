---
title: "Playing music ON a server"
date: 2010-01-18
forum: Server Platforms
---

### Post by humphreybc on 2010-01-18
I have a headless server set up in our lounge with Ubuntu Server Edition 9.10 on it that acts as a file server for our house. It's got a tonne of music on it.

We don't have a stereo in the lounge but I did find some old speakers that I plugged into the server.

I installed mplayer, alsa and pulseaudio and rebooted. Then ran "mplayer * -shuffle" in my root Music directory.

It starts playing something:
```

Player SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing The Beatles - All The Lonely People.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video

A:  72.2 (01:12.2) of 124.0 (02:04.0)  0.7% 

```

But there is no sound... I have my speakers plugged into the back audio plug on the box, there are also front jacks but I'm not sure if they're connected to the motherboard properly.

Ideas?

---

### Post by cariboo on 2010-01-18
I would check what the volume levels are, try alsa-mixer to see if every thing is turned up.

I use a combination of alsa, mpg321 and randomplay to play music on my command line only iMac.

---

### Post by humphreybc on 2010-01-19
Hmm see I've done that already, I've turned all the volume leves to 100% and unmuted them.

---

### Post by samosamo on 2010-01-19
Just because your headless doesn't mean you have to tackle this blind.  Treat it like any other issue.  What kind of sound card is it?  Does linux/ubuntu support it natively? Are the drivers loaded properly? What sound card is it, did you google it? Did you cat a wav file to the sound device to test it at the lowest level, before getting into third party apps?

Those are some ideas, try them and post back.

---

### Post by gobbledigook on 2010-01-19
it would probably help to install the sound modules... plus then you will need alsa + alsa-mixer, however these didn't work for me! I run a local file-server using XBMC as a front-end for playing music and video though my telly/amp - so i had to use oss4 and set it to emulate pulse audio (XBMC uses pulse audio).

I know this sounds complicated... and it is! but that is because sound issues don't get a huge amount of attention over here, I mean why would you want to be able to play sound from you bank of servers?? its kinda set up for large installations not the home user. 

I posted here and on the XBMC forums over sound issues and got little response.. but i have linked below my threads so you can glean what help you can from them :)

[http://ubuntuforums.org/showthread.php?t=1292977](http://ubuntuforums.org/showthread.php?t=1292977)

I'll have to do an edit when i get home as the xbmc forums are blocked from my office!!!

---

