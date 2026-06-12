---
title: "Sound card order is switched on each boot"
date: 2016-08-23
forum: Ubuntu Development Version
---

### Post by darran-kelinske on 2016-08-23
I am running the latest Yakkety packages. Each time I reboot the order of my sound cards is switched resulting in me having to go reselect the correct one to use each time. I have onboard sound and an external sound card. Is there a way to get the sound cards to maintain the same order? I've attached a screenshot of the two sound cards.



Thank you,

Darran

---

### Post by #&amp;thj^% on 2016-08-23
I used to fight with this also...my solution was: [http://ubuntu4me.blogspot.com/](http://ubuntu4me.blogspot.com/)
[h=2][SIZE=2]Change the default sound card in Ubuntu Karmic[/SIZE][/h]It is an older topic but still works for yakkety.
And if you are not using your on board sound device, you could just disable it from the bios.
Regards

---

### Post by ventrical on 2016-08-23
> **1fallen said:**
> I used to fight with this also...my solution was: [http://ubuntu4me.blogspot.com/](http://ubuntu4me.blogspot.com/)
**[SIZE=2]Change the default sound card in Ubuntu Karmic[/SIZE]**

It is an older topic but still works for yakkety.
And if you are not using your on board sound device, you could just disable it from the bios.
Regards

There were a couple of cases where I could get both cards to work simutaneously :) but that was with older version Maveric. Usually there is an interrupt conflict. Haven't tried with  yakkety yet. 

Regards..

---

### Post by #&amp;thj^% on 2016-08-23
> **ventrical said:**
> There were a couple of cases where I could get both cards to work simutaneously :) but that was with older version Maveric. Usually there is an interrupt conflict. Haven't tried with  yakkety yet. 

Regards..

Yes with pulseaudio slow maturity I can also get two cards working simultaneously using the Pulse Audio Volume Control now with out intercepts...but seems to work better at least on my end with a HDMI cable.
```
$ inxi -A
Audio:     Card-1 NVIDIA GF106 High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Creative Labs SB Audigy driver: snd_emu10k1
           Sound: Advanced Linux Sound Architecture v: k4.7.1-1-ARCH

``` 
But I will confess that Pulseaudio is a bit buggy on Yakkety for me so far.
Thanks Vent...keep up the "Great" work here.:)

---

### Post by darran-kelinske on 2016-08-24
Thank you for the suggestions. I disabled the onboard audio in the BIOS and now I only have one sound card available. Thank you!

---

### Post by #&amp;thj^% on 2016-08-24
Glad to hear you have an acceptable solution.:)
Kind Regards

---

