---
title: "Help with recording audio"
date: 2009-06-18
forum: Ubuntu Studio
---

### Post by Revolutionary101 on 2009-06-18
Hello I am new to Ubuntu and I was trying to record audio with a basic microphone. I just plugged the microphone into the jack on my laptop but sound will not record in the sound recorder program.

I already turn the microphone recording volume up to its max but it still will not record. I don't know if it is a problem with the audio driver because the audio works fine.

---

### Post by igorzwx on 2009-06-18
Try this:
[How to record sound on Ubuntu 8.04, 8.10, 9.04]("http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html")
[http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html](http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html)

---

### Post by Revolutionary101 on 2009-06-23
Thanks

---

### Post by igorzwx on 2009-06-24
Examples:
     
ffmpeg -f oss -ar 44100 -ac 1 -i /dev/dsp1 -acodec pcm_s16le mumuv-dsp1.wav 

ffmpeg -f alsa -ar 44100 -ac 1 -i plughw:1,0 -acodec pcm_s16le alsa-exp-1.wav

arecord -D plughw:1,0 -d 10 -r 44100 -c 1 -f S16_LE -t wav alsa-exp-2.wav

My experiments with recording sound on a very old IBM notebook (Ubuntu 9.04) and
a relatively new Dell notebook (Ubuntu 8.04).

On IBM best results:

iMic, on battery. OSS and ALSA, online and offline.

Very little noise.

On Dell best results:

iMic, on battery, ALSA, offline. (ALSA and OSS is about the same)

Still enough noise. DSL modem should be disconnected. Otherwise 50Hz with odd overtones.

Conclusion: IBM (made in China) is still IMB

---

