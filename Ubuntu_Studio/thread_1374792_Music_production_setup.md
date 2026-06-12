---
title: "Music production setup"
date: 2010-01-07
forum: Ubuntu Studio
---

### Post by aimpau on 2010-01-07
[I]I got a glimpse of how garageband works in Mac and I thought "hmmm...linux should have a definite replacement for this one...". So I scour the U-SoftCenter and found jokosher and LMMS. Cannot anyone help me set my laptop in such a way it would run as the garageband?
[/I]
**My specs:**
[I]HP Touchsmart Tx2 notebook PC
AMD Turion x2 ultra
2GB RAM
Intel HDA soundcard so it's Alsa based
A Keyboard that says can be connected to a PC (with what, I don't know, USB i think)
[/I]
**Software:**
[I]Ubuntu 9.10
Nted
Timidity
Seq24
LMMS
Jokosher
VLC
Virtual Midi Keyboard
[/I]
**What I want to do:**
Basically record music in MIDI format + **_see a musical score being written out as I play (like garageband)_**. Now, it's not pure grand piano, I want to throw in some drums or strings but still using the same midi Keyboard.

**What can I do so far:**
I've been playing around with Nted and I can play the notes there too. I'm also having fun with seq24 and I know how to change the voices there by changing the channel of Timidity.

**Honestly, I do not know:**
- JACK and what it really does
- Other MIDI terminologies

**However:**
I know how to edit songs through DAW (Audition, etc...).

[I]Basically, this is the first time I'll be doing this kind of thing since I play in a band but it is performed live and we normally do not record our P&W.

Thanks![/I]

PS[I]
Jokosher always says that there has been an error about GStreamer though it doesn't really says what it is. Any ideas?[/I]

---

### Post by thorgal on 2010-01-07
have you tried rosegarden ? 

Jack is a low latency audio / MIDI server. It streams data between apps and your h/w layer via jack ports. 

Jack is a bit of a smart patchbay system on the software side. It also includes a transport mechanism so many apps can be sync'ed together and controlled from one location (qjackctl, ardour, rosegarden, hydrogen, etc). It is a modular philosophy. Instead of having one single-do-it-all app, jack allows various apps to be "glued" together. It is very convenient once you get used to it. You can patch rosegarden's MIDI outputs to an external synth, or hydrogen's audio outputs to ardour for recording, or use effect racks (guitarix, rakkarack, etc), even have h/w routes (inserts) if your h/w has enough IOs, etc.

All this routing, streaming, sync'ing is sample accurate and jack can be used at very low latency if you system is well configured for it (h/w and OS).

---

