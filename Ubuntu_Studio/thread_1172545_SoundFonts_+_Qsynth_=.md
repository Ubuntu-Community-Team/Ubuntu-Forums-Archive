---
title: "SoundFonts + Qsynth = ???"
date: 2009-05-28
forum: Ubuntu Studio
---

### Post by emu42 on 2009-05-28
So I have Jack set up and everything, and Rosegarden works fine under Timidity. But I heard Qsynth/Fluidsynth works well with Jack, so I'm using that. Problem is, it doesn't seem to be loading the SoundFont correctly, because on start-up I get this in the messages:

fluidsynth: warning: Instrument "Honky-tonk": Some invalid generators were discarded
fluidsynth: warning: Instrument "Piano 3": Some invalid generators were discarded
fluidsynth: warning: Instrument "Piano 2": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnop1": Some invalid generators were discarded
fluidsynth: warning: Instrument "pno0": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnom1": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnom2": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnom3": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnom4": Some invalid generators were discarded
fluidsynth: warning: Instrument "pnom5": Some invalid generators were discarded
fluidsynth: warning: Jack sample rate mismatch, expect tuning issues (synth.sample-rate=44100, jackd=48000)


(By the way, the SoundFont I am using is Chorium if that matters)

When I finally go into Rosegarden, and go into Fluidsynth's output, it only has a piano-like sound (which makes a weird buzzing sound anyway), and nothing else.

I am using a Realtime kernel. I have "No Memory Lock" on in Jack (because it messes up without). I have a SoundFont-compatible SoudBlaster Audigy card.

---

### Post by StudioDave on 2009-05-28
> **emu42 said:**
> So I have Jack set up and everything, and Rosegarden works fine under Timidity. But I heard Qsynth/Fluidsynth works well with Jack, so I'm using that. Problem is, it doesn't seem to be loading the SoundFont correctly, because on start-up I get this in the messages:

fluidsynth: warning: Instrument "Honky-tonk": Some invalid generators were discarded
...
fluidsynth: warning: Jack sample rate mismatch, expect tuning issues (synth.sample-rate=44100, jackd=48000)


Have you tried it with JACK's sample rate set to 44100 ?

The "invalid generators" messages don't mean anything serious, at least I don't think they're the source of the problem.

Let me know if changing the sample rate helps, we'll go from there.

---

### Post by emu42 on 2009-05-28
Sample rate has always been 44100, which was default. 

I actually just found out about a feature in Rosegarden to load SoundFont banks, and so I have all the sounds instead of just piano. But there is still a very annoying buzzing sound which sounds like reverb.

Also, Jack kept locking up so I set it to Soft Mode, which seems to solve the problem. My system ran much slower after that. I really have no idea what I'm doing. :P

---

### Post by raboofje on 2009-05-29
> **emu42 said:**
> I heard Qsynth/Fluidsynth works well with Jack, so I'm using that. When I finally go into Rosegarden, and go into Fluidsynth's output, it only has a piano-like sound (which makes a weird buzzing sound anyway)

About the buzzing: try reducing the master gain in qsynth (big knob on the left).

---

### Post by StudioDave on 2009-05-29
> **emu42 said:**
> I actually just found out about a feature in Rosegarden to load SoundFont banks, and so I have all the sounds instead of just piano. But there is still a very annoying buzzing sound which sounds like reverb.


Perhaps the reverb is enabled in the Fluidsynth/QSynth engine ?

And raboofje is right, the master gain may be up too high.

---

### Post by emu42 on 2009-05-29
Believe me, I spent a while adjusting the knobs in Rosegarden and Qsynth and nothing comes close to working, so I don't believe that's the source of the reverberating buzzing. What else might effect it? Latency, buffer size, sample rate, polyphony?

Edit: I have also found that the buzzing happens with Hydrogen as well.

---

### Post by emu42 on 2009-05-30
Here's a screenshot of my current Jack setup:

[http://img16.imageshack.us/img16/1879/screenshotsetupjackaudi.png](http://img16.imageshack.us/img16/1879/screenshotsetupjackaudi.png)

I noticed that taking Jack off of Soft Mode not only causes Jack to freeze up easily, but also makes the noise much worse.

And I'm not sure why, but whenever I fire up Jack, even after a restart, Timidity always comes up in the connections. I don't connect it to anything, but it might be interfering with Jack in some way. So how do I stop Timidity, since there isn't a frontend like Fluidsynth has?

---

### Post by raboofje on 2009-05-30
> **emu42 said:**
> whenever I fire up Jack, even after a restart, Timidity always comes up in the connections. I don't connect it to anything, but it might be interfering with Jack in some way. So how do I stop Timidity, since there isn't a frontend like Fluidsynth has?

To stop it (as root): /etc/init.d/timidity stop

To make sure it isn't started automatically anymore: edit /etc/default/timidity

---

### Post by emu42 on 2009-05-30
Thanks. Timidity is off now. It didn't solve my problem though.

Edit: Solved! StudioDave, you were thinking correctly when you mentioned the sample rate. There is some problem (probably a bug) in Jack where I can't set the sample rate by myself, it stays at 48000. So simply changing the sample rate in all my Jack applications to 48000 solved the noise.

Thanks for all your responses.

---

### Post by StudioDave on 2009-05-31
> **emu42 said:**
> Solved! StudioDave, you were thinking correctly when you mentioned the sample rate. There is some problem (probably a bug) in Jack where I can't set the sample rate by myself, it stays at 48000. So simply changing the sample rate in all my Jack applications to 48000 solved the noise.

Good to hear. You should probably just keep your sample rate at 48000 for all your apps. IIRC the Audigy is hardwired to a default sr of 48 kHz. It will perform at 44.1 kHz but perhaps not well (as you discovered).

All problems solved ? :)

---

