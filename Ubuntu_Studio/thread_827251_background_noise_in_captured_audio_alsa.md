---
title: "background noise in captured audio alsa"
date: 2008-06-12
forum: Ubuntu Studio
---

### Post by roberto.eiberle on 2008-06-12
I am capturing VHS footage with XDTV for dvd production, everything works fine, i get good sound while capturing, but on playback there is a strange backgroundnoise like 1940ties radio. If I use xdtv -noalsa that is with oss, I get perfect sound, but sincronization is not that good, which in turn is perfect with alsa. I would very much appreciate help for solving this as I use it for work.

---

### Post by aeiah on 2008-06-12
have you checked it isnt audio clipping from excessive volume? obvious i know, but its best checking the simplest things first. 

is there an option to change the sample rate? (i havent used the program myself). if its at 44.1khz try changing it to 48khz etc.

---

### Post by roberto.eiberle on 2008-06-12
I use 48khz as it is meant for dvd, mike muted linein at 1/3 - I get good sound while recording, the trouble only starts when playing back.

---

### Post by Stochastic on 2008-06-12
> **roberto.eiberle said:**
> like 1940ties radio

Do you mean that the entire soundtrack sounds like it's coming out of a 1940's radio? or do you mean that it sounds like there's a 1940's radio in the background?

If it's the former, then you probably are experiencing some filtering (the main characteristic of 1940's radio is that it has a very narrow-band frequency response).  Unfortunately, I don't know that program so I can't help troubleshoot what's causing the filtering.

---

### Post by roberto.eiberle on 2008-06-13
it's the entire soundtrack that gets some crackling,hissing and sissling added to it, there should be a way to filter that out, maybe in postproduction, but I have no idea how to do that

---

