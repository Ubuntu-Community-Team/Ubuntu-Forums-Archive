---
title: "Alesis io2 express, microphone issues"
date: 2014-05-06
forum: Ubuntu Studio
---

### Post by cliff4 on 2014-05-06
Hi, I have an Alesis io2 express external sound card connected to my laptop via USB. I have a microphone plugged in to the sound card. In "sound settings" the microphone barely registers any sound whatsoever regardless of the slider above. The internal mic that's built in to my laptop is registering sound fine however. I'm not sure where to even begin. I've tried playing around with jack and ALSA, but I really don't know what I'm doing. The sound card and microphone are working fine in Windows with Audacity with no additional drivers.

Thanks, 
     Cliff

---

### Post by jejeman on 2014-05-06
See in alsamixer if this card has any controls. Press F6 and choose the card.

---

### Post by cliff4 on 2014-05-06
I've chosen the card in the alsamixer. There is a L and R channel map index, but when I move the slider up it doesn't affect the input volume, and if I close the mixer and bring it back up the settings are back to default. There's no way to save that I know of.

---

