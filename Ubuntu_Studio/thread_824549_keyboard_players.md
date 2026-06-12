---
title: "keyboard players"
date: 2008-06-10
forum: Ubuntu Studio
---

### Post by tizo_rh on 2008-06-10
Hi,

I am a keyboard player, and I am testing different software for live playing. My idea is:

Connect a keyboard synthesizer and a keyboard midi controller to PC. Control the sound, and make the sound synthesis only by the PC; may be have a pedal to change sounds; so, I have some questions:

- Which is the best way to make the synthesis by the PC? I have tried fluidsynth, Zynaddsubx and Sound Fonts directly, as my card support those (the three options with jack). I would like some software that make a good quality synthesis, and allows me to quickly change the sound; for example, with qsynth, I can save different presets configuration, and change it easily whereas I am playing. I would like to be able to change it with a pedal or something like that. Is there a software specifically designed to achieve that goal?. Maybe I could program the way to change them by another usb controller for example (instead of the PC keyboard).

- What would I have to do for the midi events not to be lost?. With timidity, the delay is too long. With others no, but when I play much notes, not all events are played "instantly". I believe, that the better solution is to install a distribution with only the software I need, and switching off the unnecessary services. But what about compiling a new kernel specifically for this?. Other thing I have though, but I don't know if it possibly, was to have an entire /etc directory, specifically for this tasks, but in the same installation, and could choose which to use a boot time.

Well, that's all for now; I surely will have more questions later. I will post here if I find some solutions.

Thanks very much,

tizo

---

### Post by darsu on 2008-06-10
I'm not too knowledgeable about these things, but one way to get easy patch changes in ZynAddSubFX is to rig it up polytimbrally so that each patch listens to a different incoming MIDI channel.

---

