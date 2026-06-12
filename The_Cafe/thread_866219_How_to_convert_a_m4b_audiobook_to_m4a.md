---
title: "How to convert a m4b audiobook to m4a"
date: 2008-07-21
forum: The Cafe
---

### Post by Jordanwb on 2008-07-21
I have an mp3 player that supports m4a audiobooks. I downloaded an m4b audio book and the mp3 player won't recognize it. Does anyone know how to convert them.

---

### Post by ajgreeny on 2008-07-21
Looks like soundconverter or soundkonverter will do the job, though I have never had a m4b file to test it out.  In spite of my running gnome, I find that soundkonverter is better than soundconverter, which often leaves me with unusable output files which are too noisy, whilst soundkonveter is great at the same conversion job.  No idea why, just what I have found.

---

### Post by mc4100 on 2008-07-21
> **Jordanwb said:**
> I have an mp3 player that supports m4a audiobooks. I downloaded an m4b audio book and the mp3 player won't recognize it. Does anyone know how to convert them.
Have you tried renaming them from .m4b to .m4a?

I used to do the opposite (.m4a to .m4b) when I was using iTunes, so my files would be classed as "Audiobooks" ... so I assume it would work. Another point, if you bought them online (like from Audible) chances are they're wrapped in D.R.M. and will not play anyway.

---

### Post by amoocool on 2008-09-08
```
mplayer /Path to file/name.m4b -vo null -aopcm:file=/path to file/name.wav

```

This will give you a wav file and then convert it in anything you need.

---

### Post by sassur on 2008-09-08
m4b and m4a is the same format, it's just that ipod places the m4b files in the audiobook category

as said above just rename the m4b to m4a

---

### Post by qazwsx on 2008-09-08
Nice work Apple (tags would be much more suitable) another way to cause problems with mpeg4 standard!

---

