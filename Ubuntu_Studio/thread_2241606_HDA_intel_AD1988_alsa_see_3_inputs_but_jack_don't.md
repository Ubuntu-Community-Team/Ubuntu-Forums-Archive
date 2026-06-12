---
title: "HDA intel AD1988 alsa see 3 inputs but jack don't"
date: 2014-08-27
forum: Ubuntu Studio
---

### Post by marun2 on 2014-08-27
hi i have audio card with AD1988 chip it has 3 indipendent inputs i see them in QasMixer an i can loop to speakers every of them
but jack see only input 0 (Zachytávání 0) 
i can change source of that input 
i want to have them all at same time

---

### Post by jejeman on 2014-08-27
Did you choose right card when setup JACK?
Hm, don't believe that internal audio card has more than 1 input.

---

### Post by marun2 on 2014-08-27
> **jejeman said:**
> Did you choose right card when setup JACK?

yes i choose intel as device and input and output left default

> **jejeman said:**
> Hm, don't believe that internal audio card has more than 1 input.

look at this datasheet [http://www.hardwaresecrets.com/datasheets/AD1988A_1988B.pdf](http://www.hardwaresecrets.com/datasheets/AD1988A_1988B.pdf) it says 6 indipendent ADCs 
and i made test
i started jack with SB card through alsa_in i added hw:intel,0 (input 0) set as mircophone and looped together so i heard microphone pluget into intel in SB headphones
and i plugged into intel my phone into line in input and througt QasMixer set line to playback so i heard my phone in headphones plugged into intel card
conclusion: rear mic and line in are independent (front mic is on front panel header which i don't have so i did not testet it)

---

### Post by jejeman on 2014-08-28
Okay, looks like you got some better audio chip. So, lets say it has three independent stereo inputs, 2 mics and 1 line in.
Well, since JACK shows just one stereo input, if you didn't set yourself just 2 channels, it means > ALSA doesn't support these features or maybe ALSA is not set to enable this features.
Give me screenshot from alsamixer, for both playback and capture faders. Make sure it has all faders in picture, and it is in English (use live CD if necessary).
Settings for this chip are
```
AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack        6-jack
  6stack-dig    ditto with SPDIF
  3stack        3-jack
  3stack-dig    ditto with SPDIF
  laptop        3-jack with hp-jack automute
  laptop-dig    ditto with SPDIF
  auto          auto-config reading BIOS (default)
```I don't see anything with 3 inputs. Is there some setting in BIOS? Does pulseaudio maybe shows some configuration that includes 3 inputs?

---

### Post by marun2 on 2014-08-28
i know that settings, i tried 6stack but no difference (maybe i set it bad)

QasMixer is alsamixer

only mention of sound card in bios is here (MB is asus P5B-E) [ATTACH=CONFIG]255901[/ATTACH]

here are thees screenshots[ATTACH=CONFIG]255902[/ATTACH][ATTACH=CONFIG]255903[/ATTACH][ATTACH=CONFIG]255904[/ATTACH]

i think alsa see these inputs

---

### Post by jejeman on 2014-08-28
Okay, looks like ALSA recognizes all 3 inputs.
Did you tried in audacity maybe to record from all or to choose one of these 3 inputs?

Did you tried in windows maybe, does this 3 input thing works?

---

### Post by marun2 on 2014-08-28
i tried audacity but it also see only one input 

i did not tried windows

MB desciption speaks of 8 channel audio with retasking support but i think it means 8 channel output

---

### Post by marun2 on 2014-08-28
i read that datasheet and i realized that i can use HDAJackRetask i retasked one output jack to microphone and i can see him in alsamixer i can choose it as input source but jack still see only one input source (capture0)

---

### Post by marun2 on 2014-08-28
I MADE PROGRESS
i picked kernel from utopic ```
Linux studio 3.17.0-031700rc2-lowlatency #201408251935 SMP PREEMPT Mon Aug 25 23:44:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
``` and this appeared in audacity[ATTACH=CONFIG]255912[/ATTACH] and choice made changes in alsamixer ( if i choose reart mic:0 it will set capture0 to rear mic an unmute it) but i can pick only one stereo input

but jack still nothing

EDIT:

i upgraded pc througt kxstudio repositories but no change (only that dependncies installed wine and my pc started to lag)

---

### Post by marun2 on 2014-08-30
nobody knows?

---

### Post by marun2 on 2014-09-05
bump

---

