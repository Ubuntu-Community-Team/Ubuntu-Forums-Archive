---
title: "Yay got everything working! Except Ventrilo..."
date: 2008-12-03
forum: Wine
---

### Post by VampiricFang on 2008-12-03
When I run Ventrilo and WoW, I can hear both now, which is good. The only I problem I really have, and what is inhibiting me from deleting WoW/Vent/WoWMatrix off my vista boot is that Ventrilo while I'm running it under Wine doesn't recognize any of my inputs (Microphones). I have both a microphone built into the lid of my laptop and a USB Headset.

Running Wine 1.1.9, Ubuntu 8.10, my system specs are my signature.

Any help would be awesome.

---

### Post by SBFC on 2008-12-03
Try these settings for Output device, Input device, and Hardware input mixer.

---

### Post by Ixonal on 2008-12-03
how'd you get audio from both vent and WoW? mine will just play the audio from the first one opened.

---

### Post by SBFC on 2008-12-03
Have you ran 'winecfg' and clicked the audio tab so that it chooses some audio settings for you? I use Alsa.

---

### Post by Ixonal on 2008-12-04
indeed, have it set to OSS right now because it's all choppy with ALSA

---

### Post by SBFC on 2008-12-04
Hmm...that's interesting.

What is your sound device? Integrated, USB headset, separate sound card?

---

### Post by Ixonal on 2008-12-04
integrated. tried a separate sound card, but never could get it to work (freakin sound blaster live)

---

### Post by SBFC on 2008-12-04
Yeah, I had no luck with my current mobo's integrated soundcard either. To be honest it doesn't even work that well in Windows. My last one worked perfectly. 

I was using a separate soundcard that worked well but am now using a USB headset that works well, too.

---

### Post by VampiricFang on 2008-12-05
Kind of weird, it plays sound in my headset headphones, like my push to talk being pressed down and testing to see if my voice can be heard (I hear myself through the headphone), but when other people talk in vent, they go through my monitor speakers _like I want_. What is up?

---

### Post by SBFC on 2008-12-05
Huh. Can honestly say I've never had that happen before. 

Wish I knew how you were doing that though. ;)

But you're able to talk/hear in Vent and hear the sounds of your game?

---

### Post by Ixonal on 2008-12-06
I can hear whatever is loaded first, the other program is mute.

---

### Post by Zackie on 2008-12-22
If your running OSS, Depending on what Program loads first will determine which as priority... I usualy load vent first then WOW since i don't need to hear toons hitting each other.. My problem is that my PTT while In WOW and MAX window my PTT will not work my Vent app has to be the active app or the one that is on top if that makes sense any ideas?

---

