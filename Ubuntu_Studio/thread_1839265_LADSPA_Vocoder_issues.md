---
title: "LADSPA Vocoder issues"
date: 2011-09-05
forum: Ubuntu Studio
---

### Post by Sylos on 2011-09-05
Hello all.

Just wondering if anyone has successfully used the LADSPA vocoder from the link below with US Lucid.

[http://www.sirlab.de/linux/download_vocoder_ladspa.html](http://www.sirlab.de/linux/download_vocoder_ladspa.html)

I tried it myself and after some fiddling I did a make install that seemed to work. I now see the Vocoder in my host apps but when I try and use it I get no effect. None of the variables seem to do anything.

I tried it first in Ardour and didnt get any luck so I tried using jackrack as the host and running a mic directly into it from the capture. When I enable the Vocoder it kills the sound altogether. I tried using an overdrive effect and that worked ok so the problem doesnt seem to be the host.

Anyone have any ideas?

Thanks

---

### Post by JayPeeJay on 2011-09-05
I use it in JACK rack, and I usually have to add an amplifier effect below it to hear anything.  Also, make sure you have an input and carrier signal both hooked into it through jack (the microphone capture should be hooked up to jack rack in, and your instrument should be hooked up to the vocoder in).  Not every instument is going to give you that nice vocoded effect, I suguest a basic synth using triangle waves for the oscillator.

---

### Post by Sylos on 2011-09-06
Hello there and thanks for the post.

I have tried hooking it up like that but Im still not getting anything - even with an amp after the vocoder. I can hear the mic coming through until I hit the enable button on the vocoder - then silence. I am perplexed!

Any other ideas?

Thanks

---

### Post by Sylos on 2011-09-06
UPDATE:

I tried uninstalling and then reinstalling from the repos via synaptic but it made no difference.

I also tried VocProc from the repos but that shuts down imediately when launched complaining about it being a zombie.

Not sure where else to go for vocoders.

---

### Post by jejeman on 2011-09-06
I've compiled the jack variant of the vocoder you mentioned, and it's working. You can try that.

---

### Post by Sylos on 2011-09-06
Thanks jejeman. I have just downloaded that and Im trying to compile. Getting quite a lot of errors. Any idea what the crack is?

```
make -C util/ play_loop
make[1]: Entering directory `/home/ric/Downloads/vocoder/util'
g++ -ljack -lsndfile -o play_loop play_loop.cc
play_loop.cc:10:21: error: sndfile.h: No such file or directory
play_loop.cc:11:23: error: jack/jack.h: No such file or directory
play_loop.cc:22: error: expected constructor, destructor, or type conversion before ‘*’ token
play_loop.cc:28: error: expected constructor, destructor, or type conversion before ‘*’ token
play_loop.cc:29: error: expected constructor, destructor, or type conversion before ‘*’ token
play_loop.cc:30: error: ‘jack_nframes_t’ does not name a type
play_loop.cc:31: error: expected constructor, destructor, or type conversion before ‘*’ token
play_loop.cc:32: error: ‘SF_INFO’ does not name a type
play_loop.cc: In function ‘void playSample(const std::string&)’:
play_loop.cc:41: error: ‘sndFileInfo’ was not declared in this scope
play_loop.cc:42: error: ‘sndFileFD’ was not declared in this scope
play_loop.cc:42: error: ‘SFM_READ’ was not declared in this scope
play_loop.cc:42: error: ‘sf_open’ was not declared in this scope
play_loop.cc:52: error: ‘sf_close’ was not declared in this scope
play_loop.cc: At global scope:
play_loop.cc:62: error: ‘jack_nframes_t’ was not declared in this scope
play_loop.cc:62: error: expected primary-expression before ‘void’
play_loop.cc:62: error: initializer expression list treated as compound expression
play_loop.cc:62: error: expected ‘,’ or ‘;’ before ‘{’ token
make[1]: *** [play_loop] Error 1
make[1]: Leaving directory `/home/ric/Downloads/vocoder/util'
make: *** [all] Error 2

```

Cheers

---

### Post by jejeman on 2011-09-06
I don't know how much you are experienced with compiling. 
Did you install all needed dependecy packages?
> Requirements
  ============

  * FLTK (Fast Light Toolkit) development files and shared library
    tested with version 1.1.7

  * Fluid (FLTK User Interface Designer)
    tested with 1.1.7

  * JACK (Jack Audio Connection Kit) development files and shared library
    tested with version 0.102.20

  * sndfile development files and shared library
    tested with version 1.0.16

  * GNU C++ compiler
    tested with version 4.1.2

  * GNU make
I would guess not
> play_loop.cc:10:21: error: sndfile.h: No such file or directory
play_loop.cc:11:23: error: jack/jack.h: No such file or directory
you need to install dev packages for jack, sndfile, fltk. Then fluid, and build-essential.

---

### Post by Sylos on 2011-09-07
Thanks jejeman - thought I had them all but I obviously hadnt.

I have installed them all and done the 'make' command and all seemed to go well. But now when I try make install i get

```
make: *** No rule to make target `install'. Stop.
```

Not sure what to do with that.


EDIT: Seems there is an executable file in the src folder that works and I now have some vocoding goodness.

Cheers for the help. Sorry for the dunce dependencies moment - I should know better.

---

### Post by JayPeeJay on 2011-09-07
Glad you have your vocoder up and running, but I just remembered one thing, for anyone else looking.  It seems like on some of the Ladspa stuff the wet and dry is reversed, like you have to have the wet all the way down for it to work.  I think the vocoder is one of them that is like that.

---

