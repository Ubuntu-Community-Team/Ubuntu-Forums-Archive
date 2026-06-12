---
title: "Issues with Jack, qSynth &amp; RT"
date: 2009-06-14
forum: Ubuntu Studio
---

### Post by ZootHornRollo on 2009-06-14
Hi,

I have uStudio 9.04 installed.

I got a new midi keyboard (Miditech Midicontrol) that i did manage to get working through qsynth, jack and rosegarden.  I had one xrun in about two hours of playing around.

i then had a play with hydrogen and ever since i am having isses with jack and RT.  Have tried umpteen restarts and am about to try reinstalling uStudio unless someone can offer a solution.

qsyth messages :

```

07:47:47.573 Qsynth1: Creating synthesizer engine...
07:47:48.609 Qsynth1: Loading soundfont: "/home/graham/Desktop/Unison.SF2" (bank offset 0)...
07:47:49.401 Qsynth1: Creating audio driver (jack)...
07:47:49.414 Qsynth1: Creating MIDI router (alsa_seq)...
07:47:49.414 Qsynth1: Creating MIDI driver (alsa_seq)...
07:47:49.423 Qsynth1: Creating MIDI player...
07:47:49.423 Qsynth1: fluid_synth_program_reset()
07:47:49.433 Qsynth1: Synthesizer engine started.
07:47:49.433 Qsynth1: fluid_synth_set_gain(1)
07:47:49.433 Qsynth1: fluid_synth_set_reverb(0.2,0.4,0.45,0.9)
07:47:49.433 Qsynth1: fluid_synth_set_chorus(12,4.3,1.6,8.9,1)
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
fluidsynth: warning: Ignoring sample *KPianoB5: can't use ROM samples
cannot lock down memory for RT thread (Cannot allocate memory)
fluidsynth: warning: Could not connect to any physical jack ports; fluidsynth is unconnected
```

when pressing a key on the midi keyboard, Rosegardens transport recognises it and displays the key press in both the in and out.

I did briefly get some noise out of it this morning but it resulted in a million-and-one xruns.

PC spec :

Dell Optiplex GX520 case & motherboard
Onboard Graphics
M-audio Audiophile 2496 Sound Card
2.4Ghz P4
512MB DDR2 533Mhz
2x500GB HD

---

### Post by ZootHornRollo on 2009-06-14
my pc's qwerty keyboard has also stopped working two or three times.  had to switch pc's to write this.

---

### Post by barisurum on 2009-06-14
Ubuntu studio with rt kernel has serious issues on my computer too, so I don't use it. It is too bad they released the distro with that much problems. :(

---

### Post by ZootHornRollo on 2009-06-14
would i be better off getting a copy of the 8.04 LTS?  or (trying) to install a regular kernal?

are their any drawbacks with the non-RT kernal?

Would extra memory help?  i have ordered an extra 1GB module, just waiting for it to turn up.

i will add my PC's specs into first post.

---

### Post by raboofje on 2009-06-14
> **ZootHornRollo said:**
> I had one xrun in about two hours of playing around. i then had a play with hydrogen and ever since i am having isses with jack and RT.

Strange. If you look at 'top', are there any processes taking up a lot of CPU or memory?

> **ZootHornRollo said:**
> ```
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
fluidsynth: warning: Ignoring sample *KPianoB5: can't use ROM samples
cannot lock down memory for RT thread (Cannot allocate memory)
```

I think this suggests you don't have the changes to /etc/security/limits.conf described at [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support) yet.

> 512MB DDR2 533Mhz

More memory couldn't hurt, but i'm not sure that's your problem right now.

---

### Post by ZootHornRollo on 2009-06-14
I tried the /etc/security/limits.conf stuff in that link and so far it seems to have made a big improvement.

No xruns unless i really flood the transport with the midi keyboard and lots of reverb/chorus effects.

i still get this in qsynth messages :

```
fluidsynth: warning: Ignoring sample *KPianoB5: can't use ROM samples
fluidsynth: warning: Could not connect to any physical jack ports; fluidsynth is unconnected
```

don't know if thats bad or not.

I get sound through rosegarden and qsynth so at least i have a working base to build on.

thank you very much for your help.

---

