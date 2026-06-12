---
title: "Live/real time sampling into a midi loop, is it possible?"
date: 2008-07-16
forum: Ubuntu Studio
---

### Post by rlameiro on 2008-07-16
I everyone!
I am kind of a newbie in the audio scene. I am a bassoon player and I want to make an electronic performance live, real time effects, pitch shifting etc. I thought using the jack rack with the ldaspa plugins, and control it with a midi foot pedal (like the Behringer FCB1010).
Said this I am stuck in one idea that I had tha was use the live sound for a sample. After sampling it I want to run a pre-made midi loop with the sound that I sampled before. anyone got ideas for this?
I also need to say that i have some problems putting linuxsampler to work...

---

### Post by angelsguitar on 2008-07-20
I'm not sure if I understand your question, but I'll try.

I think you may be able to record a sample of your instrument with ardour, or even Audacity.  There are two things I'd like to point out.  First, you should have some sort or click or metronome at the time you make the recording, preferably at the same tempo of your MIDI loop, so later you can sync both up easily.  If you record without a click you may have problems later because the sound sample may not be at the same tempo as the MIDI loop, and it may be harder to edit it and sync it later.

Second, it is preferable to record your sample dry, without effects, and add them later (maybe using Ladspa plugins in Ardour).  Effects can get in your way if you later need to edit the sample recorded, specially modulation effects and reverb/delay.  There are some exceptions; for example, a distorted guitar or some effect that is necessary for the sound of the performance (sometimes, for example, I record guitars with delay because I want a specific delay time that syncs with the tempo of the MIDI sequence), but generally is better without effects.

Once you record your signal you can launch Jack (or Jack Control if you prefer the GUI) launch Ardour (to play/edit your sample) and lauch a MIDI sequencer (like Rosegarden, for example) to play your MIDI loop.  If you configure it right, you can manage both programs from Jack and sync their output, playing both the MIDI loop and sample in sync.

---

### Post by thorgal on 2008-07-20
you could try sooperlooper, a jack client used for looping stuff live. You can record sample on the fly and loop it within sooperlooper. Because it's a jack client, you can have jack-rack in the routing and enable effects on the fly. Whether you can enable /disable effects with a foot pedal via MIDI, I don't know, never tried it, no interest in it until now.

[http://www.essej.net/sooperlooper/](http://www.essej.net/sooperlooper/)

[img]http://www.essej.net/sooperlooper/sshot5.png[/img]

by reading more about it, this looks like the tool you need :

> 
 SooperLooper is a live looping sampler capable of immediate loop recording, overdubbing, multiplying, reversing and more. It allows for multiple simultaneous multi-channel loops limited only by your computer's available memory. The feature-set and operation was inspired by the impressive Gibson Echoplex Digital Pro (EDP). When used with a low-latency audio configuration SooperLooper is capable of truly realtime live performance looping.

The application is a standalone JACK client with an engine controllable via OSC and MIDI. It also includes a GUI which communicates with the engine via OSC (even over a network) for user-friendly control on a desktop. **However, this kind of live performance looping tool is most effectively used via hardware (midi footpedals, etc) and the engine can be run standalone on a computer without a monitor**. 


---

### Post by Stochastic on 2008-07-20
There's also freewheeling to try, it's another program designed for live looping (MIDI based I believe). [http://freewheeling.sourceforge.net/](http://freewheeling.sourceforge.net/)

---

### Post by rlameiro on 2008-07-20
Ok a lot of info! thanks, but the idea wasn't sampling a audio loop, but sampling the sound of my instrument and using it to play it from a midi file in loop. In other words using the sound sample as a "synth" for the midi software.

Finally the idea is to use this process in live performance and no in studio because the idea is to perform an big improvisation :)

---

### Post by Capoeira on 2008-07-20
you are looking for an "sample synthesizer". don't now if there is one for linux but there are VSTi like CronoX

---

### Post by Stochastic on 2008-07-21
ahh, sorry I only skimmed the original posting.  You'll probably want to look into software such as PD (pure data).  It's actually a programming language, so it can have a difficult learning curve in comparison to most audio apps, but what you're talking about is fairly easy to construct.  Here is a beginner's tutorial on the PD: [https://help.ubuntu.com/community/HowToPureDataIntroduction](https://help.ubuntu.com/community/HowToPureDataIntroduction)

This forum: [http://puredata.hurleur.com/index.php](http://puredata.hurleur.com/index.php) is a great place for friendly PD help.

---

### Post by angelsguitar on 2008-07-21
Ok, I think I finally understood :) Sorry for the misunderstanding.

Well, after you record the sound of your instrument, you can use that sample (and a couple of other samples or takes from your instrument) to create a soundfont bank with a program called swani.  Then, to play it back with a MIDI instrument, you can use FluidSynth or, if you prefer a GUI, QSynth (which is a front end to FluidSynth).

---

### Post by thorgal on 2008-07-21
looks like we all got it wrong :lolflag:
so if I understand correctly, you want to create a soundfont before your live perf and use it during your live perf with sequenced MIDI loops using your home made soundfont ?

---

### Post by rlameiro on 2008-07-21
> **thorgal said:**
> looks like we all got it wrong :lolflag:
so if I understand correctly, you want to create a soundfont before your live perf and use it during your live perf with sequenced MIDI loops using your home made soundfont ?

Well not quite. I want to do everything in LIVE ! yeap It is a crazy idea.
I want to sample during the playing then start the loop with the sound of my instrument that I sampled seconds ago. :guitar:  crazy idea hein?

Stochastic - Thanks about PD. I already knew Pure data, actually I am reading the book of Miller Puckette. Do you think that with pd I can sample audio and then using it to play on midi? If so, man thats the way!! I was thinking to use pd for other thing so is just another patch. the problem is that it seem difficult to make.... will search more about it.

And for every one with more thoughts about this, please bear in mind that the goal is to use ONLY open source software, as the result will be also a free audio recording and also a open score :):guitar::lolflag:

---

### Post by thorgal on 2008-07-22
no, it's not that crazy, it sounds actually interesting but may I ask, why a MIDI loop is important here ? I understand the role of MIDI triggers (activate a loop, stop a loop, shift a loop, etc) but when I think about a MIDI note  sequence, I don't really see the point unless you want to alter the original sound (and now, it is becoming a bit crazy : you want to improvise a soft synth in realtime!).

---

### Post by rlameiro on 2008-07-22
Yeap!!!! thorgal - you got it! is just that that I want to do! Sound crazy, but the loops will be bass line giving the rithm and harmony base.But I will like to use the sound I like during the performance, even with efects or either clean, also to change the pitch (transpose) is easier to use midi.

---

### Post by Stochastic on 2008-07-22
PD is totally the right tool for ya, you could also use a different audio programming language such as supercollider or chuck, but PD is easiest to get into for beginners.  Try posting on that PD forum I mentioned, they're very friendly there and can explain in great detail how to do fft analysis/resynthesis, live processing, etc... but Miller Puckette's book is an excellent resource too.

---

### Post by Live Loop on 2008-07-26
Hi !
There is a new **Live Looping sequencer** . You can download it at [[COLOR="Blue"] Live Loop[/COLOR]]("http://code.google.com/p/liveloop/").
You just need to select your midi keyboard and begin to create loop.

Note : it works only with windows but a linux compatible version is coming very soon.

---

