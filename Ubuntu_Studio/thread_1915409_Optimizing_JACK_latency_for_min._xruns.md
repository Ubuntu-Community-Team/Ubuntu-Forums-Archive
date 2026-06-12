---
title: "Optimizing JACK latency for min. xruns?"
date: 2012-01-26
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-01-26
How should I set latency for minium xruns on my system?
I have no idea how to test it, or know if I have it optimized.
I have a Dell Optiplex 330 dual core desktop, which has about 2 gig memory,
and only an nvidea Geforce and a network card in the slots.
The system tells me that I have:
Intel N10/ICH7 Family High Def. Audio Controller rev.1.
- So presumably, my playback should be better than an AC/97 like my old computer.

I would like to know what the ballpark best setting might be, 
and how to set it in JACK (I suppose)..

---

### Post by CivilizationII on 2012-02-17
To optimize xruns, you only need to increase latency.

---

### Post by RaumTrug on 2012-02-17
run Jackd in realtime mode & disable cpu frequency scaling (bios disable eist/amdcnq, or by setting all cores to "performance" governour). few years ago people would install realtime kernels to push even further, but grapevine uses to whisper normal/generic kernels fare almost as well now.

then you can experiment with latency, i.e. the frames and periods values. note the frames value is not fixed to 2^x, you can enter values in between with the keyboard as well (as well as specifying the number as parameter when starting jackd without qjackctl from cli/script).

how low you can go depends on the audio-software you're using, the cpu-load, the complexity of the "working setup" and such. try to set the latency to the highest value you can tolerate well with your ears to be on the safe side stability-wise.

also it depends on what latency you really _need_ for your purposes. real low latency is only needed when using midi-synths realtime, software guitar (or voice or whatever) realtime fx, when the artist needs to monitor the processed signal while performing.

another factor is the soundcard/driver stuff, onboard chips are not so likely to produce good latencies reliably, while an m-audio for example can be pushed real far (like 16-32 frames/period on light setups regarding the programms used in the chain).

i also have an optiplex, and will experiment on it with jack as soon as i have time & free winds around my head - also with the m-audio, I just hope the f***ing oem bios won't play unfair regarding parallel use of onboard/pci/usb devices - i've seen your other thread where you ranted about problems on your system. the idea of having the onboard as extra monitoring tap is appealing.

---

