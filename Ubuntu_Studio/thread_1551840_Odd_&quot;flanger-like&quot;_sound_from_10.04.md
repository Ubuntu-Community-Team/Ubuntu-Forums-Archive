---
title: "Odd &quot;flanger-like&quot; sound from 10.04"
date: 2010-08-12
forum: Ubuntu Studio
---

### Post by MorphMaker on 2010-08-12
Hi all! I am at wit's end with this one....

I'm using 10.04, on a custom built box featuring an M-audio Delta 1010 (ICE 1712). In Qjackctl, I've got the Delta as the input, and the on board sound as output. This is working fine. Also in Jack, I've got my latency down to a decent 5.33ms, which is very difficult to even perceive, and works fine for my purposes. The problem is this:

I have an odd, almost "flanger-like" sound that fades in to the point of crippling my session, then back out to crystal clear sound. This has to be an issue with jack's settings I'm sure, but I just can't nail it down. It sounds as if the signal is being chopped up and "digitized" for a while and then fade back out to perfect sound. It does this only to instruments plugged into the Delta, and does NOT do it to sounds coming from virtual instruments (hydrogen). There is a definite rhythm to it as well, depending on jack's settings(most notably Frames/period, Sample Rate, and Periods/buffer.). I notice that with these settings @ 64/48000/4 respectively that it occurs every 30 seconds or so, and if I have these set to  128/44100/2 that it happens only about every 80 seconds. Both net a latency of 5.3 and 5.8, respectively.

Anybody got any ideas? I'm at a complete loss here.....

---

### Post by AutoStatic on 2010-08-13
Hello MorphMaker, my first bet would be the fact that you're using two different cards. Apparently those cards are not 'in sync'. I'm not an expert on that but all I know is that it is generally advised against using different soundcards with JACK for the input and output.

---

