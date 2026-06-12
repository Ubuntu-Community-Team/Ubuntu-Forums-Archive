---
title: "Listening to line in?"
date: 2008-07-05
forum: Ubuntu Studio
---

### Post by mechaxl on 2008-07-05
Hello all,

In a nutshell, what I want to do is:
```
cat /dev/dsp1 > /dev/dsp
```

but without the latency that that causes.

I tried Jack, but I just can't get it to work. I've got a Delta44 card and a simple soundblaster card. I'm trying to send the input from the Delta44 card to the soundblaster card. Any clue how I would go about doing this? Thanks

---

### Post by sisco311 on 2008-07-05
You can try sox:
```
sox -r 32000 -w -t alsa hw:1,0 -t alsa hw:0,0
```
[http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa#ALSA_audio_with_other_applications](http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa#ALSA_audio_with_other_applications)

---

