---
title: "Linux MultiMedia Studio"
date: 2010-02-16
forum: Ubuntu Studio
---

### Post by Jordii on 2010-02-16
My instrument samples in lmms really suck. For example the bass drums sound like "brr" it doesn't even sound like it. Can I replace it or something?

---

### Post by Chronon on 2010-02-16
Many of the samples are just audio files.  You can certainly record new samples (or obtain them elsewhere).  However, you might have other issues that are causing the signal to clip.  Are you sure the audio files contain clipping?

---

### Post by alvaroguillen on 2010-02-16
hey,

the sounds sound like that when youve got the wrong sound driver selected. try with alsa, or alsa with jack running.

---

### Post by elliotn on 2010-02-17
Were can one download more sounds for lmms

---

### Post by 5010 on 2010-02-17
If you export to a wav and play the song outside of lmms, does it still sound bad?  If it sounds better outside the app, then try tweaking the audio settings.  When I started using lmms it was running thru jack badly and I finally gave up and ran it with alsa and it works great.
 
I've been using the soundfont player for drums with lmms.  There are free drum kits available, just search the web and download.  You can get entire drum kits on a single patch, then use the piano editor in 1 track to trigger them all.

---

### Post by Jordii on 2010-02-18
> **alvaroguillen said:**
> hey,

the sounds sound like that when youve got the wrong sound driver selected. try with alsa, or alsa with jack running.

This solved it! Thanks.

---

