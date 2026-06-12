---
title: "Problem: RealPlayer and SMPlayer"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by W A L E E D on 2009-01-06
I face a problem with smplayer and realplayer.

It is because there is some conflict between them!

I can play files with smplayer, but if I played a file in realplayer then I play a video file in smplayer, it will play BUT WITHOUT sound! So I need to restart my Ubuntu!

It is really weird! It is OK with the others players VLC and Movie Player!
But I like SMPlayer because it gives me more options with subtitles.

Thank you.

---

### Post by skern03 on 2009-01-06
> **W A L E E D said:**
> I face a problem with smplayer and realplayer.

It is because there is some conflict between them!

I can play files with smplayer, but if I played a file in realplayer then I play a video file in smplayer, it will play BUT WITHOUT sound! So I need to restart my Ubuntu!

It is really weird! It is OK with the others players VLC and Movie Player!
But I like SMPlayer because it gives me more options with subtitles.

Thank you.

I had a similar problem with sound in SMPlayer. What I found is that I needed to install PulseAudio, and then turn up the sound in the Pulse Audio Device Chooser, Volume Control. There are four tabs on it for different sound devices.

To install Pulse Audio, see the sticky post at the top of the Multimedia & Video forum:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

There's also a sticky post there for video.

---

