---
title: "Volume control doesn't allow me to smoothly change volume"
date: 2009-04-20
forum: Ubuntu Studio
---

### Post by OneSeventeen on 2009-04-20
I'm running Ubuntu 8.10 and have an M-Audio MobilePre USB with some speakers plugged into the line-out.

I can easily change the master volume by clicking once on the volume icon and sliding the fader.  If I double-click to adjust the specific inputs and outputs, it gets very weird very fast.

I'll just play around in volume control and describe what's going on.
What I do **-->** What Happens.
Click and drag "PCM" volume from 0 to 75% **-->** volume went up to 75% for both left and right channels, then left channel dropped to 0.

Click the "link" button **-->** Both channels go to 0

Click and drag "PCM" volume back to 75% **-->** both left and right jump between 75% and 0 at different times (not both at once) and left channels stays at 75%, right channel goes to 0.

Click and drag right-channel back to 75% **-->** both channels stay at 75% un-linked

Click and drag PCM capture to 75% **-->** both channels stay at 75% (first time that's happened... normally it makes PCM playback go to 0 and then behaves like PCM playback did earlier)

Another weird thing is the speakers are always "monitoring"... meaning I can't record without turning the speakers down.  I'd rather just route audio using JACK, ignoring the speakers except for output from Ardour... but that's not happening because the speakers are always playing whatever is going into the microphone, even if JACK isn't telling them to.

Any advice, or just format & reinstall?

---

### Post by OneSeventeen on 2009-04-20
My temporary fixes:
[list]
[*]Turn down speakers when recording
[*]Use CLI alsamixer -D hw:1 to control the MobilePre volume controls.
[/list]

Still a bummer, because I can't simply tell JACK to put clear audio in the left speaker and distorted audio in the right speaker (which is just a fun way to test that JACK is routing properly.)

---

### Post by markbuntu on 2009-04-23
This is a very common problem with usb devices and has been off and on for a year or so. You should file a bug with alsa or at launchpad so they will know the m-audio is also effected.

---

