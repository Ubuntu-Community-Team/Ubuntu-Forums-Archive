---
title: "[SOLVED] KDENLIVE 0.6 - need path settings for MLT and Inigo"
date: 2008-06-05
forum: Ubuntu Studio
---

### Post by fizzybrain on 2008-06-05
What-ho.
I'm using kdenlive 0.6. It seems to be better in many ways than 0.5. However, I'm having trouble exporting - it just gets stuck on 0%.

By trying to export a script I have guessed that the path setting for "Inigo renderer install path" needs to include the name of the executable - "/usr/bin/inigo" instead of "/usr/bin/" which is what it said to start with.

I'm guessing that the same is true of the MLT framework install path ...

AH-HA!

I was writing this and I had a thought, and I think I've solved my own problem! (I'll submit this post anyway in case anyone else is looking for it)

I have set "MLT framework install path" to "
/usr/lib/mlt
(a directory), and "Inigo renderer install path" to 
/usr/bin/inigo
.

The script now works, and I can also export from within kdenlive - it's rendering as I write this (though, amusingly, it is now at 752% !)

Yup, the test seems to have worked.

I hope this is helpful to anyone who stumbles across it!
Share and Enjoy

---

