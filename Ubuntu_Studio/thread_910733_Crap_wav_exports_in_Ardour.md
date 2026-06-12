---
title: "Crap wav exports in Ardour"
date: 2008-09-04
forum: Ubuntu Studio
---

### Post by originalsynthesis on 2008-09-04
Hi there, just recently started using Ubuntu studio and have been enjoying it. This is my first install of a linux OS, so I'm pretty green to the whole scenario. Im fairly proficient with computers in general, though being spoon fed by windows all these years has whittled me down to a certain kind of helplessness now that im on linux. So, I hope you'll bear with.
My prob right now w/ Ardour is that when i export projects to .wav, in any bitrate/sample rate, it will come out clipped and glitchy. A sub-issue that slowed me down at first, was getting files with length, yet no sound whatsoever. I fixed that by specifying in the export menu all the tracks i want. I dont see why it didn't just export through the master outs. everything in jack was connected AFAICT
As for the main issue, iv tried running on rt and generic kernels with no result. I changed my memlock to 65%, then to 50%, which helped oh so slightly. I played with 16,24, and 32 bits, and all the sampling rates (using dithering when doing so). Though i haven't tried files other than WAVs.
Here's my humble little laptop machine:
Toshiba Satellite p25 s509
2.8 ghz p4
*512m RAM
*realtek ALC202 sound
*80 gig hard drive( though the linux partition is nearly full)

the last three items are what im thinking the problem is coming from, though the memory and sound card are the main issues i see. although, maybe increasing my partition size would help, dunno. What do y'all think?

---

### Post by BlackCat13 on 2008-09-12
Same problem here... have you tried the Ardour users list... I am going to ask there if I get an answer I will reply here...

---

### Post by joe56 on 2008-12-16
Are your 'master: out-1' and 'master: out-2' checked left and right respectively in your export dialog? 

Also before you try to play your exported files in another app make sure you kill ardour2 and the jackd server.

---

### Post by kayosiii on 2008-12-19
can you explain the sound issues you are getting in a more detailed way. The most likely problem I can see is that Ardour uses floating point precision which will let you have a signal above 0db and not clip - however when you export with frequencies heading over 0db All tracks summed - then you will get clipping which sounds pretty terrible. you can try dropping the level on the master channel and see if that improves the quality or you can use say a parametric eq to cut the offending frequencies a bit if you can figure out what they are... Some indication of what you are recording and how would help with giving more specific advice - also I reccomend signing up to the linux-audio-users mailing list.

---

### Post by babarosa on 2008-12-27
Hi Folks,

you didn't tell us which version of ubuntu you use.

Thanks to the great guys of the team at [www.getdeb.net](www.getdeb.net) since a few days you can download the newest ardour 2.7.1 package  now for _both_ versions ubuntu **8.04.1** and 8.10.

Maybe it was a bug being resolved in this new packages.

Regards, Michael

---

