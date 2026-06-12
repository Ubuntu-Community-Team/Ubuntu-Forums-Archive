---
title: "Playback Volume Issue"
date: 2008-08-25
forum: Ubuntu Studio
---

### Post by Faximili on 2008-08-25
Hey folks,

I'm having an annoying problem recording sound. Though the problem is not with a specific application, it is certainly a "Multimedia Production" issue, so I'll post here.  If that's not correct, kindly point me in the right direction.

Basically, I can plug my keyboard into the microphone jack of my computer (an HP pavilion laptop, if it matters), and I get very lovely play-through to my external speakers. Opening up any of a number of recording programs, I can see the levels change in the meters, hit record, and play a little diddy. However, when I press stop and play it back, the playback is BLARINGLY LOUD.

No amount of playing with any setting in my volume control panel has made any difference. I can, of course, simply turn down the Master volume when I want to play back--but that's extremely annoying to do when you're flipping back and forth between recording and playback. Similarly, I can adjust the gain on individual tracks, but none of the programs I've tried out will let me set a default Gain level, so I end up doing each track (or worse, clip)'s gain by hand.

The ideal behavior would be that the sound I hear when I record and the sound I hear when I playback are identical. But for the moment I'd settle for close.

Any advice?

Thanks in advance!
~Faximili

---

### Post by markbuntu on 2008-08-26
So what application are you using?

---

### Post by Faximili on 2008-08-26
I've played with Audacity, Rosegarden, Ardour, and a few others.  All have the same problem.

---

### Post by markbuntu on 2008-08-28
I would guess that the capture level in your mixer is set very low so that is why capture volumes seem reasonable. But the output mixer levels are very high so playback would blare. 

This is the alsamixer I am talking about. It controls the system volume levels and jack must play through them so try fiddling around with you alsa mixer setup. 

I use the gnome-alsamixer for that sort of stuff. It is easier to use, lives in Applications/Sound and Video, and shows more options than the plain alsa mixer from the command line.

---

### Post by Faximili on 2008-08-31
Alright, I seem to have got it figured out.  One of the sliders provided by my volume control application is "PCM".  Now, muting this slider disables playback of recorded sound altogether.  But turning it down all the way seems to make playback fall in line with the recorded volume.

Can anyone explain this behavior to me?

---

