---
title: "Controller will not control Aeolus"
date: 2011-06-19
forum: Ubuntu Studio
---

### Post by ERRRIMMAD on 2011-06-19
I'm sure I'm doing something stupid here, I want to run my controller keyboard through a midi input and have it control Aeolus, this is my first time running a soft synth in Linux so I'm sure I'm missing some simple stupid thing.

As far as I can tell I patch the midi in to Aeolus through jack, than I patch Aeolus to system.

Whats the trick, someone must see my missing link here. LOL

---

### Post by ERRRIMMAD on 2011-06-19
Also here is the readout on my system.

[http://www.alsa-project.org/db/?f=33...498164b358fbc3]("http://www.alsa-project.org/db/?f=337df0f01083cb7f654edecc34498164b358fbc3")

Minus the sound blasters, I removed them to make life simpler. =D

---

### Post by ERRRIMMAD on 2011-06-19
Sorry I posted this, I got it working, I should work a little harder and I would not have to ask. LOL

---

### Post by treacl on 2011-12-27
What did you do to get it working?

I am trying to get Aeolus 0.8.2 working with Virtual Keyboard 1.9 on Ubuntu (not studio) 10.04 64-bit. Following the quick-start guide [here]("http://www.64studio.com/quickstart_aeolus"), I:

[LIST=1]
[*]Start jackd, vkeybd, and aeolus.
[*]Set vkeybd to use MIDI-0.
[*]In jackd, under ALSA, set up a connection between vkeybd and aeolus.
[*]In aeolus, map MIDI-1 to keyboard I.
[*]Select a stop for test.
[/LIST]
Note that there is one difference vs. the quickstart. In step #3, in the jackd control panel, Virtual Keyboard doesn't appear at all on the MIDI tab (aeolus does). Both the keyboard and aeolus appear on the ALSA tab, and that is where I am making the connection.

I know zilch about Ubuntu audio and don't even know where to begin troubleshooting this one. Any suggestions much appreciated.

treacl

---

### Post by treacl on 2011-12-27
Got it working. As it says in the quickstart guide, in jackd you also have to connect aeolus to the sound card. (Displaying my ignorance of Ubuntu sound and my inability to read instructions all at once.)

---

