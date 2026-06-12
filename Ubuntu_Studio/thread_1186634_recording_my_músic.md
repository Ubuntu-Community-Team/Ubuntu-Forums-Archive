---
title: "recording my músic"
date: 2009-06-13
forum: Ubuntu Studio
---

### Post by Barasuishou on 2009-06-13
Hi i'm trying to record músic in kubuntu, using audacity, witch is the most similar programa to what i was using in windows(sony soundforge), now i have this problem, when i press record it captures only half of a second of sound, and then it keeps recording but without making any audio capture,

if you want to recomend me another program you think is better for this, please go ahead, anything is accepted

i'm using quickcam pro 9000 mic to record

i'm not so advanced user on linux so please explain simply. Thanks

can someone help me???

---

### Post by Amilo1718 on 2009-06-13
rosegarden & ardour => great ;)

---

### Post by paulmerchant on 2009-06-17
I'll chime in with a similar answer as Amilo. Learning Ardour is a smart thing if you want to use a Linux computer as a recording studio. I'm now very happy with the new version of Renoise + Ardour.

---

### Post by kayosiii on 2009-06-17
> **Barasuishou said:**
> Hi i'm trying to record músic in kubuntu, using audacity, witch is the most similar programa to what i was using in windows(sony soundforge), now i have this problem, when i press record it captures only half of a second of sound, and then it keeps recording but without making any audio capture,

if you want to recomend me another program you think is better for this, please go ahead, anything is accepted

i'm using quickcam pro 9000 mic to record

i'm not so advanced user on linux so please explain simply. Thanks

can someone help me???

I am trying to replicate your problem here - I am using kubuntu 9.04 (jaunty) and trying to record using a quickcam pro 9000...
Basically everything here is working as is should...

There are a few things that you might want to look at.
1) check the samplerate of your project. (bottom left hand corner of Audacity) Mine is set to 4800.
2) in edit->preferences I have my playback set to alsa hw(0,0) and my recording set to the quickcam pro 9000 with the number of channels set to 1 (mono).
3) if you are still getting issues with these settings then perhaps pulse-audio is the culprit. Search the forums for advice on how to disable it.

Like the above people if you want to go beyond very simple recordings then Ardour is the most practical option. Jokosher is somewhat simpler and might also be worth a look in.

---

### Post by sedawk on 2009-06-17
Audacity needs lots of disk space for caching.
If your home directory is nearly full you might see
unexpected results.

---

### Post by Barasuishou on 2009-06-17
ok i'll installed arduor can you recomend me any tutorials??? or would you say any google search could be enougth?

---

