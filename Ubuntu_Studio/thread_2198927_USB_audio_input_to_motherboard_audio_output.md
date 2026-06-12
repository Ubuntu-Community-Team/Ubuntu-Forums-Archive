---
title: "USB audio input to motherboard audio output"
date: 2014-01-11
forum: Ubuntu Studio
---

### Post by Stabadie on 2014-01-11
Setup info first:
Ubuntu Studio 13.10 (tried both low latency and the standard Ubuntu kernel)
LIne 6 Tone Port GX, usb audio interface which has a line in and out

I have been able to get JACK setup and working fine with input from the Tone Port and output to the Tone Port line out. However, I'm getting a bad popping sound in higher volume ranges in the right channel, only on the output. I'm nearly certain it is the physical line out jack on the Tone Port that is damaged but I would like to test if I get the same popping by pushing the output to the motherboard audio card.

Is there a way to use USB audio as input and output to the mother board audio? I've tried multiple configurations in the JACK setup and it either causes a crash or JACK stalls and fails.

---

### Post by jejeman on 2014-01-11
You need to set different cards for capture and playback in JACK, and figure out with wich settings will work.
It is not recommended to use two cards with JACK. Clock issue.

I've managed to use Zoom G2.1Nu and ALC888 with this settings
```
/usr/bin/jackd -t1000 -dalsa -r48000 -p512 -n3 -Xseq -D -Chw:CODEC -Phw:Intel -o2
```

---

