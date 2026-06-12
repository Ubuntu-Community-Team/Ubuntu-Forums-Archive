---
title: "I'm going to rebuild my machine for rose garden.....aren't I?"
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by bolex100 on 2009-03-22
Jaunty is around the corner.  Intrepid didn't really work for me somehow.  Even my real time kernal doesn't boot anymore, so I might as well rebuild.  But am I rebuilding what I need?  will it work?

On a PC I've used Cubase for audio segments Fruity loops for drums.  FL works as a virtual instrument controlled by cubase so they work well together. One big plus is to put a slight advance or delay on a track (funk is ALL timing).

So I imagine that I should be using Rosegarden ('cept I did get to grips with it before) and a drum sequencer to nest inside.(can you?).  Then there's the time slip thing.... And I imagine that it all needs to run on Ubuntu Studio ..... with a RT kernal.

I would imagine that this is a fairly standard configuration.  For audio production, but has anyone actually done it?  Am I working in the right direction?

---

### Post by thorgal on 2009-03-22
sounds fine, except that in general, you don't run programs inside others (like FL inside Cubase), you instead connect programs together via the jack audio connection kit, like you would connect pieces of hardware together via input and outputs sockets.

Rosegarden can take plugins of course, so if you need drum tracks in Rosegarden, you can easily do if you find a drum plugin that is DSSI compliant (plugin architecture). But I would rather go the other way: fire up say Hydrogen (which is a drum sequencer) and connect rosegarden's MIDI track to hydrogen's MIDI input. You can then redirect hydrogen's audio output back to rosegarden's track audio inputs. Or you can do all the drum sequencing in Hydrogen, and use rosegarden for other MIDI purposes (synths), and bind all these programs transport wise via the jack transport slave mode, so that you can control the transport of all apps from anywhere.

---

### Post by bolex100 on 2009-03-22
So what do you run?  what actually works?

---

### Post by thorgal on 2009-03-22
for me, what works is:

- jackd as the audio server, using the ALSA backend to communicate to my RME Hammerfall system
- ardour for multitrack recordings, editing, DAW work in general
- rosegarden for drumming via a MIDI track connected to an external VSTi (Addictive Drums by XLN Audio). The VSTi is hosted by a vst host like dssi-vst or fst. It works great with this VSTi.
- I rarely use other big programs. The rest is plugins for dynamic effects (EQ, reverb)

My needs are dictated by my work-flow. It's a home studio where I do things alone so I do not need special programs. And since i am not into loop based music, I have no use of loopers. I actually happen to play instruments for real and like to have variations and even small mistakes in my music.

---

### Post by bolex100 on 2009-03-22
On top of Intrepid or Ubuntu Studio?

---

### Post by thorgal on 2009-03-22
neither of them, I use a customized debian sid (I recompile my kernel when needed, and other things quite regularly like jack and ardour).

---

### Post by bolex100 on 2009-03-23
debian ................. that's where it gets even more complicated.

---

### Post by thorgal on 2009-03-24
mmmm it depends, for me debian is easy to use and very flexible. But having been a linux users for 11 years, and unix in general for more, I may be a bit biased. I tried ubuntu on my laptop for a few months. It just screwed it eventually. So I reverted back to debian. I see the point with ubuntu, don't get me wrong ... but coming from the "oppposite" side of the spectrum (i.e. neither windows nor mac), I was disturbed by the windowish quality of ubuntu and some things that I take for granted on linux wre either changed or removed. I am too dumb to administrate a windows box, so that could explain my failure with ubuntu (a simple dist-upgrade ****** it up completely ...).

---

### Post by markbuntu on 2009-03-26
I have had some success using Ubuntustudio with the Hydrogen-Rosegarden-Ardour-jack setup with the rt kernel in Hardy amd64. The 386 kernel just could not do it. Anyway, the rt kernel is broken in Intrepid and will probably not get fixed. The Jaunty rt kernel just came out and it is also somewhat broken but there is some hope it will eventually work.

Most of the rt effort now is on the 2.6.29rt kernel which will most likely come out with Koala 9.10. You could try 64studio but if you want to use UbuntuStudio stick with Hardy for now and use the 64 bit amd64.

---

### Post by simtaalo on 2009-03-26
i think you could do all you need inside lmms, its a very similar setup to fl studio. you can use your midi in on that, although better through alsa rather than jack. its also got a vst host so no need for dssi-vst.

i personally don't use the rt kernel, but some people do.

make sure you try ver 0.4.3

[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/)

---

