---
title: "Rosegarden's CPU level too High"
date: 2009-04-28
forum: Ubuntu Studio
---

### Post by angelsguitar on 2009-04-28
Hi all.  When using Rosegarden along with Qsynth (to play MIDI sequences with some soundfonts) I notice that the CPU level on Rosegarden is too high - mostly between the middle and full bar sometimes.  Revising the System Monitor shows Qsynth is taking sometimes up to 50% of CPU power.  I'm not using Jack; just Rosegarden and Qsynth through ALSA alone.

How can I bring those levels down? I'm afraid it will crash or something.

---

### Post by barisurum on 2009-04-28
I have the same problem. Are you using the generic kernel?

---

### Post by angelsguitar on 2009-04-28
No, I'm using the default rt kernel that comes with Ubuntu Studio 9.04

---

### Post by barisurum on 2009-04-28
I too had this issue with rt kernel, switching to generic solved the problem for me. Although rosegarden says system timer resolution is low, I experienced no latencies between ardour and rosegarden when I connected the two. External midi control is fluent too. I don't suggest you switching to generic kernel if you are fine with rt. I had serious issues with rt and had to quit it. If you experience futher anomalities with rt, generic one may be an option. Cheers 'n happy arranging :popcorn:

---

### Post by raboofje on 2009-05-28
[some people](http://www.linuxmusicians.com/viewtopic.php?f=4&t=1090) are reporting unusually large CPU usages in other applications when pulseaudio is running under the rt kernel.

---

### Post by pittmantechno on 2009-05-28
I am experiencing this as well as frequent freezing with the new rt kernel - I will add i am using an atom processor hah - but i get great performance with it in windows 7 and MacOS 10.5.7 using Reason and Live  hehe - so then lets get this updated !! I love me some ubuntu -

---

### Post by kayosiii on 2009-05-28
PulseAudio is a definate suspect....

---

