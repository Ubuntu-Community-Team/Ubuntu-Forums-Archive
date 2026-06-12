---
title: "how to install qjacktuner ?"
date: 2010-11-09
forum: Ubuntu Studio
---

### Post by MoRoBoShi on 2010-11-09
Hi to all,
I recently (and successfully) joined my new M-audio sound card to my karmic [9.10]
Now, I have red about qjacktuner which should JACK AUDIO CONNECTION guitar tuner.
Can someone please tell me how install qjacktuner?

---

### Post by Stochastic on 2010-11-09
Have you tried fmit?  It's easier to install and does the same thing, just click this link to install it: [apt://fmit]("apt://fmit")

After looking for how to install qjacktuner, I noticed that it has yet to be released and does not look like it is actively developed.  I would NOT recommend it for a beginner to use/try.  FMit is much more developed and user friendly.  Here is FMit's homepage for more info [http://home.gna.org/fmit/](http://home.gna.org/fmit/)

---

### Post by Pablo_F on 2010-11-09
Rakarrack has a tuner too.

I dig tuneit. You will only see numbers (HZ and cents) and note names because it is CLI only. This is all what I need and it is precise!

$ sudo apt-get install build-essential libasound2-dev libfftw3-dev libjack-dev

Download tuneit-0.3.tar.gz from:
[http://delysid.org/tuneit.html](http://delysid.org/tuneit.html)

Extract the files

$ cd tuneit-0.3

$ ./configure
$ make
$ sudo make install

To see the options:

$ tuneit --help

To run it:

$ tuneit -jf

(for example)

Cheers! Pablo

---

### Post by MoRoBoShi on 2010-11-12
fmit works great!!
Thank you Stochastic!!

---

### Post by trulan on 2010-11-13
While discussing tuners, don't forget Lingot.  I've used tune-it as well as FMIT and I've finally settled on Lingot mainly because I like the analog tuner feel it has.  Jack support for Lingot had been iffy in the past but it is getting pretty good.  If you're running Karmic though, I'd venture a guess that FMIT will be a lot easier to get working than Lingot.  FWIW.

---

