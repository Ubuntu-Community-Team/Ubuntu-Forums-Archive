---
title: "Why is this?"
date: 2013-08-13
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2013-08-13
So I finally got my Studio and Jacks setup to record. When I recorded my bass track, from looking at the recorded track in Ardour, it looked kinda week, but when I play it back it's loud and clear. 

[ATTACH=CONFIG]245348[/ATTACH]

Why is that? I showed a screenshot of what I mean. Am I doing somthing wrong? Does it even matter?

Thanks ahead for the help. 

-Nate

---

### Post by tgalati4 on 2013-08-13
The scale is typically -1.0 to 1.0 where a maximum audio signal will represent digital clipping for a 16-bit (CD quality) recording.  Normally you would set your bass preamp (volume knob) such that your signal is at 70 to 80% of full scale.  Then you adjust your output volume to a reasonable listening level.  This process is called gain-staging.  You set the input gains at 70% so the downstream gains don't need to be turned up as high--which amplifies noise.

If your playing is weak, then that is another issue.

---

### Post by cub on 2013-08-14
Before you record, how's the input on the channel from the bass?

As per this image (but in this one it overloads which is far worse): [http://en.flossmanuals.net/ardour/ch023_recording-audio/_booki/ardour/static/Ardour-RecordingAudio-recording_audio_04-en.png](http://en.flossmanuals.net/ardour/ch023_recording-audio/_booki/ardour/static/Ardour-RecordingAudio-recording_audio_04-en.png)

---

