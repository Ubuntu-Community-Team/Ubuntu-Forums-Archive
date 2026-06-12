---
title: "Command to adjust volume/gain of audio?"
date: 2008-06-10
forum: Ubuntu Studio
---

### Post by johann_p on 2008-06-10
I could have sworn there was a batch command that would adjust the gain of an audiofile so that recordings with a low level are becoming louder -- but I am unable to find it.

I think it works as a pipe.

Any ideas?

---

### Post by Stochastic on 2008-06-10
what format are your soundfiles? wav, aiff, mp3, ogg?

edit: also, do you want to turn all the fies in the batch up, or turn all the files to the same level (turning up quieter ones much more than louder ones, and medium ones up just a little - this is called normalization)

---

### Post by prismatic7 on 2008-06-10
> **johann_p said:**
> I could have sworn there was a batch command that would adjust the gain of an audiofile so that recordings with a low level are becoming louder -- but I am unable to find it.

I think it works as a pipe.

Any ideas?

you're not after replaygain, are you?

---

### Post by Stochastic on 2008-06-10
replaygain isn't actually software. see [http://en.wikipedia.org/wiki/Replay_Gain](http://en.wikipedia.org/wiki/Replay_Gain)

There's a few tools around that will do this batch processing (but some only support a limited set of sound formats), mp3gain, [normalize]("http://normalize.nongnu.org/"), or ecasound are just a few command line utilities out there.  Ecasound is a fully featured wave editor that can be run from command line.  To use it to normalize all wav files in a directory do ```
ecanormalize *.wav
``` but this will overwrite the originals so be warned!

---

### Post by prismatic7 on 2008-06-11
i meant mp3gain... gah, brainfart :)

---

### Post by Creative2 on 2008-06-11
form fuoco tools-------> this command line 

ffmpeg -i INPUT  -ab 192k -vol 400 -y OUTPUT 

it can work for the most of formats  sometime i use vol 700

---

### Post by Stochastic on 2008-06-11
> **Creative2 said:**
> form fuoco tools-------> this command line 

ffmpeg -i INPUT  -ab 192k -vol 400 -y OUTPUT 

it can work for the most of formats  sometime i use vol 700


Can you explain this command a bit?  Does it set all volumes to 400 (or 700 - what is that even relative to?) or does it normalize to that level (the man page didn't say anything about a -vol option)?  Also, 192kbs may be an acceptable bitrate for mp3s, but that's a significant audio degradation for uncompressed formats such as wav files.

---

### Post by Creative2 on 2008-06-11
i have just asked better 


i.e. 256 - no change, 128 - decrease amplitude two times, 512 - increase amplitude twofold, etc)


it multiplies every audio sample

---

### Post by johann_p on 2008-06-11
Thank you for all the valuable hints I will keep this thread bookmarked!
I think the one I was after (and already had installed on my computer) is normalize-audio and its mp3-wrapper, normalize-mp3.

Thank you!

---

### Post by Stochastic on 2008-06-11
if it's just mp3 audio you're looking to change, most people use mp3gain, but normalize-mp3 will also work (maybe try both and see which is better)

---

### Post by fotoni on 2009-04-14
I changed loudness of my pm3 file easily by using **lame**

        [COLOR="Blue"]  lame --scale [COLOR="Red"]n[/COLOR] test.mp3 test1.mp3[/COLOR]

              n > 1: increase volume
              n = 1: no effect
              n < 1: reduce volume

---

