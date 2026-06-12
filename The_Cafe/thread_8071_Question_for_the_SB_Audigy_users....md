---
title: "Question for the SB Audigy users..."
date: 2004-12-13
forum: The Cafe
---

### Post by Quake on 2004-12-13
Don't know if its in the right thread but...

I have the [Logitech Z-640](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2,CONTENTID=5047)  and for some reason, the bass doesn't blend well with the music like in Windows. I tried adjusting the bass, treble and other options in alsamixer but the bass still sound awful. Anyone else has this issue?

---

### Post by kleeman on 2004-12-13
I had a problem very like this with the Audigy 2 card and the Logitech Z-5300 speakers (5.1 system). I was able to solve it by ugrading the warty alsa libraries from 1.0.5 to 1.0.6 (work has been done to improve Audigy 2 support recently in alsa). The packages you need to upgrade are:

                                  alsa-base 1.0.6a-11
                                   alsa-utils 1.0.6-4

You can find these by googling "alsa-base ubuntu" etc.

Sound now sounds great although I had to turn down the base a bit (my wife threatened divorce ;-))

---

### Post by Quake on 2004-12-15
Nice, I installed Alsa 1.0.7 and the sound quality is much better now... even better than windows ;)
Thanks for the help.

---

### Post by macewan on 2004-12-20
[QUOTE=Quake]Nice, I installed Alsa 1.0.7 and the sound quality is much better now... even better than windows ;)
Thanks for the help.[/QUOTE]
 this from source at alsa-project?

---

### Post by Quake on 2004-12-20
[QUOTE=macewan]this from source at alsa-project?[/QUOTE]

Nope, From Debian unstable

---

