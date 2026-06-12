---
title: "recording at 88.2khz"
date: 2010-03-07
forum: Ubuntu Studio
---

### Post by Pencilpen on 2010-03-07
Greetings,
I recently decided to convert some of my very old vinyl LPs to CD and have been having success with Audacity. However I have noticed some slight distortion and decided I'd like to try and up the quality a bit. 

So I upped the sample rate in Audacity to 88.2khz however I ran into the documented problem of Audacity recording for 1/2 a second then stopping. After some experimenting I found that my sound card isn't capable of 88.2khz only 44.1/48/96. I wonder if that is the problem some are having with Audacity ceasing after 1/2 second - but that isn't my main question.

I started looking around for a sound card compatible with Ubuntu and capable of 88.2khz and I was astounded to find that I couldn't find any cards capable of that unless I spend around $400 or so.

So, am  I correct in my assumption that to record in Audacity at 88.2 khz then my sound card would need to be capable of that? If my sound card is sampling at 96khz but Audacity recording at 88.2 then there would have to be some resampling done between the hardware and software an as 88.2 is not a multiple of 96 then I am assuming there would be some error involved.

And if my assumption is correct does anyone know of a cheap sound card these days that is capable of 88.2 khz and runs on Karmic? :-\"

TIA,
Karl

---

### Post by Capoeira on 2010-03-07
as long as you do some heavy sond processing or recording classical music you wont benifit from 88.2.

no home-recorder ever will.....you need high-end gear

---

### Post by Capoeira on 2010-03-07
you know that you can't connect the turntable directly to the line-in don't you?
you need a phono-pre-amp....or a an amp with a phono-line-in

if you have a phono-pre the distorsion might come from this device

---

### Post by Stochastic on 2010-03-07
There's no practical reason why you shouldn't just record at 96k (if you feel you need the headroom over 44.1).  The Secret Rabbit Code library 0.1.3, which is what many current open source programs utilize (ardour for instance), performs VERY well in these sample rate conversion tests: [http://src.infinitewave.ca/](http://src.infinitewave.ca/)

Sox (a very powerful text-based audio processor) is even better in the tests.

You would need to be quite the audiophile to worry about the level of distortion that this conversion imparts to your signal.

---

### Post by Capoeira on 2010-03-07
> **Stochastic said:**
> 
You would need to be quite the audiophile to worry about the level of distortion that this conversion imparts to your signal.

And how audiophile do you have to be to hear those extra-frequencies that SR over 44.1 can capture (and how expensive your equipment has to be? And "hear" you can't those frequencies), or to heare those distrosions of aliasing wich higher frequencies than 22.050HZ generate in 44.1? and the effect of aliasing a good converter manages with oversampling.

that is what i know, reading a lot.

MUCH more important is the bitrate (if you do audio-processing!)

---

### Post by Pencilpen on 2010-03-07
Thanks for your replies guys. 

Yes I am recording classical music. And yes I have my turntable plugged through a pre-amp. 

I've tested the setup by plugging the turntable directly to my main amp via two different pre-amps and there is less distortion than through my sound card. Mind you we're not talking a great amount of distortion and it's only noticeable on heavy choral pieces.

---

