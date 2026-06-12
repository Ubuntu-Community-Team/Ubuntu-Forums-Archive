---
title: "Advice on hardware for audio capture, preferably for a new laptop"
date: 2014-09-17
forum: Ubuntu Studio
---

### Post by fitzhugh2 on 2014-09-17
I'd like any/all input on two things: what to look for in terms of basic audio interfaces, and minimum requirements shopping for a computer that I'll use for hobby/nothing fancy - just not awful sounding - multitrack recording of guitar, bass, etc.

I'm ready to buy a new  computer but am not sure what to look for. I suspect just about anything  modern would be OK latency wise, but I thought that last time. My AMD64  x2 3800+ (If I recall correctly) and 3G ram didn't do well.    I'd  really prefer a laptop but that leaves me even more unsure what to look  for. I last tried this around 6 years ago and the state of things then were  just not quite ready, plus my computer was not quite up to par. I tried  really hard with ubuntu studio, studio 64 and AVLinux, put in quite  the effort over a couple months. Never did get to the point where I felt  it was worth buying the audio interface. The old version of ardour kept  crashing, other DAWs were problems as well... plus I had latency  issues.

From what I can tell, the audio interface is a big problem, especially if I go with a laptop. I don't mind stereo - this is for solo use.
Cheap is critical. For both the computer and the audio interface I can't spend more than $500, maybe $600 (doubtful), and most of that would have to go to the computer. I'm quite fine buying an old audio interface off ebay if I know what to get. I'm hoping some old cheap device would be sufficient. 
Am I expecting too much to hope for imperceptable latencies? I don't need to run effects on a bunch of audio tracks all at the same time. 

What I have pieced together (not much):
USB 2.0 is very risky - most not supported
USB 1.1 is more likely to work, but with serious limitations in bandwidth. How much of a problem? I'm not looking to make a high quality demo, just fun multitracking at home. 
PCI card based solutions seem most likely, only then I'd have to get a desktop computer.
PCIe based solutions - don't think I've seen any, read something about how many PCIe busses actually being  emulated/virtual and hence having suprising amounts of latency (can't  find the link, I'm afraid).
Firewire is gone, though may be able to use PCIe adapter (see above)

I did get a hand-me-down Line 6 POD 2.0 recently. It has outputs, of course. If I connect them to the mike or line in on the computer will it just suck so bad I don't use it? I'm not clear on what the limitations are in this whole realm. If it doesn't sound awful that would suffice for 95% of my hopes.  I'd try it but my current computer's back panel was physically damaged (don't ask) and I can't get a line in or mike signal to work at all. 

Now, if I can get midi as well I'd be really happy - I'd get a cheap used keyboard and use it to play with synths like yoshimi.

Thank you!!!
Fitzhugh

---

### Post by jejeman on 2014-09-18
There are no bandwidth limitations with USB1.1 card, specially for stereo one.
For laptop you need to go for USB device.
Look here for device choice
[http://wiki.linuxaudio.org/wiki/hardware_support](http://wiki.linuxaudio.org/wiki/hardware_support)
There are fine small cheap Behringer USB mixers, maybe thats for you. Or Scarlett 2i2, etc.

---

### Post by davevr on 2014-09-24
I have bought the Roland Quad Capture second hand for 75&#8364; what has a very good on board sound card. I use it for recording guitar, bass, and connecting my midikeyboard. 
And I did not have to install any drivers, Ardour recognized it immediately. (I have more trouble with Ardour then with the Quad Capture.) I would advice to stay away from Behringer, they are cheap but the quality is likewise. 
If you just want to record guitar, bass etc seperately and want to go cheap maybe the Peavey Xport is something for you. New it's around 45&#8364; here, and comes with Reaper for free (DAW) and Revalver.  (you can run them with Asiowine)

---

