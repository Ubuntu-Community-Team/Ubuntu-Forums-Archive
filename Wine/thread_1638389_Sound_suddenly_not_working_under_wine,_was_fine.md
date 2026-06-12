---
title: "Sound suddenly not working under wine, was fine???"
date: 2010-12-05
forum: Wine
---

### Post by jotto! on 2010-12-05
Sound is working in the system as normal however, went to have a quick game of BF1942 and desrt Combat and the sound wasnt working. Went to configure wine and the Audio tab and clicked on test sound and got an error Audio Test Failed.

It is set to ALSA and I havent changed anything.....any ideas?

---

### Post by Soulcage on 2010-12-06
Sounds like the sound problems in bf1942 haven't been fixed or have regressed.

---

### Post by jotto! on 2010-12-06
> **Soulcage said:**
> Sounds like the sound problems in bf1942 haven't been fixed or have regressed.


Have been playing BF1942 etc with sound, all was working ok. Yesterday, son and daughter were playing a LAN game and I noticed no sound. 

I have no sound in WINE, not just BF1942, all wine apps have no sound and I get the Error,
'Audio Test Failed' from the configure wine screen under the audio tab.

---

### Post by mastablasta on 2010-12-06
long shot, but perhaps alsa is misconfigured (choose another device as sound card)? 
 
```
sudo alsaconf
``` 
 
Also check
 
```
alsamixer
```
 
if all sound is set up propperly-
 
Is the sound working normally elsewhere?

---

### Post by DocMindie on 2010-12-06
Got the same problem here... it started last Linux Kernel update... 2.6.35.something which was last thursday or friday, I think.

---

### Post by jotto! on 2010-12-06
> **DocMindie said:**
> Got the same problem here... it started last Linux Kernel update... 2.6.35.something which was last thursday or friday, I think.

Ahh, that could be about right. Kids were playing over the weekend but son doesnt like sound turned on for some reason so I didnt notice then.


Sound is working fine in all other aspects of ubuntu.

Will post up what I get from the code above.

---

### Post by jotto! on 2010-12-06
> **mastablasta said:**
> long shot, but perhaps alsa is misconfigured (choose another device as sound card)? 
 
```
sudo alsaconf
```Also check
 
```
alsamixer
```if all sound is set up propperly-
 
Is the sound working normally elsewhere?

Getting error with sudo alsaconf of command not found.
Alsamixer shows device installed and level where I had set them.

---

