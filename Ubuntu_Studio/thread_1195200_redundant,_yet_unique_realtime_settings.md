---
title: "redundant, yet unique: realtime settings"
date: 2009-06-23
forum: Ubuntu Studio
---

### Post by balloooza on 2009-06-23
I do have complete understanding of all the settings in jack, ardour, /etc/security/limits.conf, I just do not know a resonable value for them!!

SO, here is my question I have a system with these specs:

[LIST]
[*]AMD Athlon X2 64 2.8 GHz
[/LIST]

[LIST]
[*]4 GB of memory (only 2.7 are recognised, I thought 32 bit ubuntu supported more, OH well, I will never use that much)
[/LIST]

[LIST]
[*]No Nvidia drivers (these are so bad for rt)
[/LIST]

[LIST]
[*]9.04 with rt kernel.
[/LIST]

[LIST]
[*]Maudio audiophile 2496
[/LIST]

[INDENT]I would like to know what you think for thee settings
[/INDENT]
[LIST=1]
[*]realtime (in limits.conf)
[*]nice (in limits.conf)
[*]I did not forget memlock... I just know what it should be
[*]frames/period (I want latency of 20 ms, not 17, not 21, 20, as a musician, that is when my ears hear no difference)
[*]periods/buffer  (again, I would like to balance the latency, and I think that I can go low here (I have a nice sound card)
[*]nice (in jack) I would guess -19, seeing that is the nice I have in limits.conf, but will adjust with the nice we set
[/LIST]
Mark "balloooza"

---

### Post by kayosiii on 2009-06-25
I don't quite understand why you would want exactly 20ms -- It's not as if you are going to hear sounds at 17ms before they happen. 

For realtime performance I would aim for under 5ms (which is what is often referred to as zero latency by manufacturers).

In a nutshell latency doesn't configure to exact MS values - it configures to optimal buffer sizes for computer processing. I imagine this to be true for practically all computerised equimpent and anything that is giving you exact values is probably just rounding things. 

If you need a specific latency then I suggest going for anything under the latency you are looking for and then using the artificial latency ladspa plugin to make up the difference.

---

