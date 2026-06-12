---
title: "Default Audio"
date: 2017-10-12
forum: Ubuntu, Linux and OS Chat
---

### Post by azurinko on 2017-10-12
I don't know why 44.1 / 16 is default.
I would make it 24/96...

Even my old dual-core Athlon motherboard's sound-card does support it...

---

### Post by Rocky_Bennett on 2017-10-18
First, I use Audacious which sounds alright, it is not Windows quality. But considering that...

1. [https://www.learndigitalaudio.com/how-linux-audio-works-vs-windows-audio-2017](https://www.learndigitalaudio.com/how-linux-audio-works-vs-windows-audio-2017)

and then 

2. [https://r3dux.org/2013/12/how-to-enable-high-quality-audio-in-linux/](https://r3dux.org/2013/12/how-to-enable-high-quality-audio-in-linux/)

---

### Post by yoshii on 2017-10-23
Personally, I use 48 kHz 32-bit float for composing and saving files.  Then when I transcode to other formats, it's usually 48 kHz 16-bit.  A lot more hardware is now 24-bit, so 24-bit is not unusual anymore and that hardware usually has lower noise specs.  But even some best-selling USB speakers are still only 16-bit.  I used to have a 24-bit 96 kHz audio interface, but the rates above 48 weren't used except for experiments.  

Since most video defaults to 48 kHz and a lot of pro audio is also 48 kHz, I find that to be adequate without wasting drive space and making the CPU work harder for what's not usually audible anyhow because of bandlimiting.  All that stuff about LP filters is usually taken care of with 48 kHz and well-designed filters.  While a lot of experts say that 60 kHz would be ideal, it's never really been implemented.  And were still within the effects of the CD era of RedBook Audio which is standardized at 44.1 kHz 16-bit linear PCM.  

I often use FLAC audio and it translates easily back and forth between CD's and files while keeping the metadata and not using up too much space.  Eventually I will move to WavPack, but there's no rush.  
But it is nice that WavPack is there and some portable media players can be RockBoxed to support it.  FLAC players already exist.

---

