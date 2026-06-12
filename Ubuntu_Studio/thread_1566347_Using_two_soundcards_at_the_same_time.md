---
title: "Using two soundcards at the same time"
date: 2010-09-02
forum: Ubuntu Studio
---

### Post by Peter7K on 2010-09-02
Everything I've read on this subject is pretty outdated, so I succumbed and decided to post.  I'm running Ubuntu 10.04 with RT kernel.  


I purchased a cheap little [http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_3?ie=UTF8&s=electronics&qid=1283180816&sr=8-3]("http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_3?ie=UTF8&s=electronics&qid=1283180816&sr=8-3").

I would like to do the following (it seems like they go hand in hand):

1. Enable both sound cards at the same time (have audio output go to both if I want).

2. Use it in Mixxx for headphone cueing (there is no way to use this for headphone cueing?)

---

### Post by Pablo_F on 2010-09-02
You can try mixxx through the jack audio server and then use alsa_out. 

For example:

$ alsa_out -dhw:1

assuming jack is using hw:0

I hope both play in sync. In any case, check the man page.

$ man alsa_out

Cheers! Pablo

---

### Post by Peter7K on 2010-09-02
I do this and it runs... but no sound.  Very strange.

```
alsa_out -dhw:1
selected sample format: 16bit
delay = 977
delay = 972
delay = 1006
delay = 999

```

And I know it's hw:1 because hw:2 etc doesn't work.

EDIT: Ah.. of course I forgot to use jack connections.  So I connected system -> alsa_out.. and I just get max volume distorted sound blasting :(

---

### Post by Pablo_F on 2010-09-02
If I understood corrrectly, you want to connect the output ports of mixxx to both pair of outputs, this is, to system (your main card, selected in the jack setup) and to "alsa_out" (your second card). 

I am not sure what connections you are trying to do, but system captures to alsa_out does not make sense to me right now.

In mixxx, choose the jack audio plugin as the "sound api". Now you will be able to connect the master and headphone channels as said above.

Cheers! Pablo

---

