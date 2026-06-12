---
title: "SEQ24 &gt; Bristol &gt; Ardour problems"
date: 2011-05-16
forum: Ubuntu Studio
---

### Post by onewayness on 2011-05-16
Hi all.
 
I'm trying to record something I sequenced in SEQ24 in Ardour, using Bristol -mini as the synth.  With jackd, SEQ24, and Bristol all running, I'm getting the audio output I'm looking for, but as soon as I fire up Ardour, the sequence in SEQ24 stops playing and won't restart.  When I hit the 'play' button, it triggers and sustains the first note in the sequence, which stops when I hit the 'stop' button.  Nothing else.  I've tried both starting Ardour first, and starting SEQ24 first, and doesn't seem to make a difference...
 
Any suggestions?

---

### Post by Pablo_F on 2011-05-16
Maybe problems or unexpected behaviour with the jack transport?

Try disabling all the jack transport options both in seq24 and ardour.

(In ardour, select "internal" to the right of the big clocks)

---

### Post by onewayness on 2011-05-22
Thanks, Pablo.

Looks like it was the JACK transport controls in SEQ24.  Disabled them and it's working now.

adh

---

