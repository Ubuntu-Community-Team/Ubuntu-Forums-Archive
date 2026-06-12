---
title: "Serval Performance Midi"
date: 2008-02-10
forum: System76 Support
---

### Post by Squish on 2008-02-10
I was wondering if it is possible to get the midi working?

I dont know much about sound, but I would like to get working with programs like rosegarden, among many other midi using programs. I also need it for some of my wine applications.

Some help would be greatly appreciated.
Also, it is the issue that made my friend switch back to windows, while he would like to actually be on ubuntu.
cool

---

### Post by thomasaaron on 2008-02-11
I know of some customers who have tried diligently to get midi working under Ubuntu but weren't able to. They ended up dual booting.

There is some community documentation on it you want might want to look at:
[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

---

### Post by Squish on 2008-02-15
If I were to switch to the 64 bit version... would I be able too?

Or perhpaps there is another linux distro which can accomplish this?

---

### Post by thomasaaron on 2008-02-15
We do no testing with midi devices, so I don't know.
But I doubt 64-bit would make any difference in whether or not it was supported.

As for other distros, I have to leave that one to customers to answer. We only test with Ubuntu.

Sorry to be so useless on this one. It's just that midi seems to be a niche that we haven't had a lot of call for. I should probably talk to R&D about it. Maybe they can incorporate some testing/development for it into the process at some point.

---

### Post by darkbob9 on 2008-02-15
> **Squish said:**
> I was wondering if it is possible to get the midi working?

I dont know much about sound, but I would like to get working with programs like rosegarden, among many other midi using programs. I also need it for some of my wine applications.

Some help would be greatly appreciated.
Also, it is the issue that made my friend switch back to windows, while he would like to actually be on ubuntu.
cool

Just out of curiosity, what sort of midi devices are you trying to work with?
I've managed to get a nice external sound card (M-AUDIO Fast Track Pro)
working with my Serval Performance, and with the realtime kernel, jackd
works very well for passing midi between programs.  I haven't connected
my midi keyboard to tthe fast track pro yet (I've been too lazy to go buy
a midi cable).

---

### Post by asmiller-ke6seh on 2008-03-06
It would be nice just to be able to start with KMid playing MIDI through ALSA.

---

### Post by darkbob9 on 2008-03-07
> **asmiller-ke6seh said:**
> It would be nice just to be able to start with KMid playing MIDI through ALSA.

I haven't messed with any midi players playing directly to ALSA.


with the same jack configuration that I discussed in my other thread,
I was able to simply start jackd with qjackctl, and play a midi
file with timidity by just typing:

tmidity file.mid

---

