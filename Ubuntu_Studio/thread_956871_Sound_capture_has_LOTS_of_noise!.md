---
title: "Sound capture has LOTS of noise!"
date: 2008-10-23
forum: Ubuntu Studio
---

### Post by Envergure on 2008-10-23
I'm having horrible noise difficulties when capturing from internal mic, external mic and line-in, regardless of what capture program and external imput i use.

I only have this problem in Ubuntu, not in Vista.

It's enfuriating because i'm trying to record percussion sounds to use in LMMS and there's more noise than signal most of the time.


EDIT:  I used [this fix]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=806620"), which solved the headphones problem but not the noise.

---

### Post by Stochastic on 2008-10-24
what soundcard do you have?  what version of hardy are you running?  what do you mean by external mic setup (i.e. what input are you running that into)?  what did you plug into your line-in?  Can you post a screenshot of alsamixer in the capture view?

---

### Post by Envergure on 2008-10-24
> **Stochastic said:**
> what soundcard do you have?
Don't know.  How do i find this out?
> what version of hardy are you running?
8.04.1 kernel 2.6.24-19-generic
> what do you mean by external mic setup (i.e. what input are you running that into)?
Microphone plugged into the "microphone" jack.
> what did you plug into your line-in?
Roland JX-3P polysynth
> Can you post a screenshot of alsamixer in the capture view?
See attached.  In the "Options" tab the two menus have the same options:  "Mic" (external mic), "Front Mic" (built-in mic), "Line" (line-level inputs) and "CD".  The top menu has no efect, only the bottom one.

---

### Post by komoras on 2008-10-26
if you have some kind of distorsion
then check my post:

[http://ubuntuforums.org/showpost.php?p=6024149&postcount=4](http://ubuntuforums.org/showpost.php?p=6024149&postcount=4)

---

### Post by Envergure on 2008-10-26
That isn't the problem.  The mic *works*, just there's a lot of noise.  I'm going to see if i can reproduce my Ubuntu problem in Vista and maybe that'll shed some light on it.  I wonder if maybe the Windows driver has software noise removal built in.

EDIT:
So yes, Acer's drivers have a noise canceler built in (maybe hardware, maybe software, can't tell).  I turned it off but got still less noise than in Ubuntu, and the signal was centered while in Ubuntu it's 1/4 (or so) of the way to the top in the right channel and a bit low in the left.  Also, in Vista i get fan noise, but in Ubuntu there's both fan noise and some hiss.

Mic and synth in Windows with noise filter off are not perfect, but better than in Ubuntu.

---

### Post by komoras on 2008-10-26
> **Envergure said:**
> That isn't the problem.  The mic *works*, just there's a lot of noise.  I'm going to see if i can reproduce my Ubuntu problem in Vista and maybe that'll shed some light on it.  I wonder if maybe the Windows driver has software noise removal built in.

EDIT:
So yes, Acer's drivers have a noise canceler built in (maybe hardware, maybe software, can't tell).  I turned it off but got still less noise than in Ubuntu, and the signal was centered while in Ubuntu it's 1/4 (or so) of the way to the top in the right channel and a bit low in the left.  Also, in Vista i get fan noise, but in Ubuntu there's both fan noise and some hiss.

Mic and synth in Windows with noise filter off are not perfect, but better than in Ubuntu.

didn't want to tell you bout the mic
but bout the line-in

I play bass guitar 
and if the line-in level is high 
the sound has a lot of distorsion and buzzing

I reduced the line-in level and record capture level
bouth in volume control and in software I use

and the sound I record is crystal clear
no noise no distorsion no buzzing no nothing

just check my setings for the line-in


there is no software that can reduce your noises
it depends on lot of things:
cables, curent, level adjustments...

bout that low line-in level
is an advice I recived from a tone engenier once
and from there on I recive just clean sound
where ever I record

---

