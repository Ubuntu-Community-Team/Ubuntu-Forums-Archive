---
title: "jackd frames/period &amp; latency"
date: 2012-12-30
forum: Ubuntu Studio
---

### Post by BrianSwatton on 2012-12-30
I recently upgraded to 12.04 and found that with jackd latency coming out at 46mS, using my midi keyboard to play into rosegarden wasn't, in fact, very usable at all.   

I found with some experimentation that I could get the latency figure down to a more usable 11mS by altering frames/period from 1024 down to 256.

Can someone give me an idea if there will be other repercussions to look out for?  I seem to remember some online documentation for jackd that mentioned this, but I can't seem to find much in my searches.

I'm a guitar/bass player usually, so don't use keyboard input very often, maybe I should just change this parameter when I need to and stay at 1024 otherwise?

---

### Post by jejeman on 2012-12-30
It all depends on how much CPU power you have. Lower the frames as much you can for JACK to work stable.
Ussualy I set it to 128. If I can I'm setting it to 64. That's for i3-i5 CPUs.
It is true that for playback you don't need low value, but hey if it works, no need to change it.

---

### Post by BrianSwatton on 2012-12-30
That's helpful, thank you.

---

### Post by RaumTrug on 2013-01-01
How low you set that parameter (and yes, it's meant to be used for individual tuning) depends on what you want to do with jack. Keyboard responsiveness is one reason to set it low, other's are when you use your pc to modify input (mic, guitar, ...) and need to monitor effected signal in realtime. so if you sing through a mic and want to hear yourself with digital reverb and eq from pc on headphones, or use stuff like guitarix, you need to go low, too.

When using 1024 for mastering and such, when realtime processed monitoring isn't required, and the delay from hitting play to sound starting doesn't matter, well...will take some load from the cpu:

how well things go when using low latency also depends on the hardware and software you're using. some programs do extensive calculations every period, with variable computation load, so going too low might then cause instabilities, or more load on the cpu, higher chances of dropouts, etc. you can also use values like 92, 192, so non-powers of 2, by inputting in the number field with keyboard. Most Soundcards have some kind of restriction, though, i.e. lower than 32 might not be possible, or just multiples of 32 or 64, while other cards might accept almost any frames/period value you've got to experiment yourself. Also soundcards will add some ms internally in hardware that you can't control, or the amplifier of the speakers might add a little, too.

---

### Post by BrianSwatton on 2013-01-01
Thanks for that RaumTrug,  that's very helpful.  I was wondering how problems would start to show.  By the way though, I think propagation delay through the amplifier would be insignificant in terms of the times we are talking about.

Probably the only time I'll need it low is for keyboard input, so I'll set it when needed I think.

Thanks again

---

### Post by RaumTrug on 2013-01-03
o.k., good amps won't mess...but I have cheap 2.1 speakers lying here, I cannot really use for realtime stuff because they add quite some latency somewhere. got me nuts when messing with the soundsystem untill I tried headphones...

---

### Post by BrianSwatton on 2013-01-04
That's pretty odd, I'm at a loss to explain more latency with headphones.  

I repair professional music equipment for a living and know that amplifier delay is tiny compared to the time periods we are working with for latency figures.

Mind you, I also know that after 25+ years in electronics, I still come across things I struggle to explain.

All the best, thanks for your help.

---

