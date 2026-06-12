---
title: "Recording and playing music at the same time"
date: 2008-04-29
forum: Ubuntu Studio
---

### Post by Zach_the_Lizard on 2008-04-29
Hello there,

I am running Hardy Heron on my laptop and would like to record my playing guitar. If I simply plug it into the mic jack and use a recording program, I can't hear it being played back. If I use a program such as GNUitar or Creox c to act as an amp, I can't use a sound recorder. I get errors such as "can't open audio device!: and such.

Another idea I've had is to simply use the headphone out jack and plug it into the computer for better sound quality. That works great and all, but I would like to be able to hear what I'm playing at the same time. Does anyone have any ideas?

---

### Post by warbread on 2008-04-30
For this you'll need real time monitoring.  Unfortunately, I haven't had much luck with this on my laptop as it's pretty DSP intensive.  Still, I don't think it could hurt to try.

If you haven't already, start using Jack with real time enabled.  This is the hard part as it takes some tweaking and you may need a separate sound card.  Once you have jack running, you can easily hear yourself by splitting the output of Creox to both PCM and Ardour/Audacity/Jokosher/etc...

This process may be complicated by Hardy's use of Pulseaudio.  I'm not an early adopter, so I can't tell you anything to that effect.  Let me know if you have any more specific questions and I can give you all the information I have.

---

