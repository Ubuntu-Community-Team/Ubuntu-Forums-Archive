---
title: "how is qjackctl related to jackd?"
date: 2014-10-17
forum: Ubuntu Studio
---

### Post by drumanart on 2014-10-17
Hello.
My question is:
When I start jackd from a terminal:
jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2

and afterwards start qjackctl is the above configuration overwritten with the qjackctl configuration file stored in .jackdrc ?


I can't figure out the relationship. It seams that in my system jackd is not related to qjackctl what I thought is just a graphical representation of jackd.


Thanks Martin

---

### Post by jejeman on 2014-10-19
If JACK is already running Qjackctl will only "join in" the session.

Qjackctl is just GUI for JACK. It has nothing to do with .jackdrc file, JACK writes it itself.

---

### Post by drumanart on 2014-10-20
So if I start jackd with:  jackd -r -dalsa -dhw:0 -r48000 -p1024 -n2 and afterwards open the GUI (qjackctl) the sample rate should be also changed (before I started it with -r44100), right ?
In my system the jackd configuration is not shown in the qjackctl, as if I would have different qjackctl instances. 
Any idea to investigate the issue?

Thanks Martin

---

### Post by jejeman on 2014-10-21
There can't be any changes to the running JACK server. Qjackctl should just show the running server.
There can be more than one JACK server running at the same time (AFAIK, never tested). Each instance should have unique name.

---

