---
title: "UMX610 Midi Controller"
date: 2011-11-15
forum: Ubuntu Studio
---

### Post by Brachamul on 2011-11-15
I have acquired a UMX610 Midi Controller.   I'd like to play some music with it. It's really that simple.   I don't understand why it's so complicated to get something so basic to work. It's a keyboard, i press buttons, nothing happens. I spend hours and hours and hours trying to understand, i don't.   So this is my last resort, trying to get someone to help me. I've downloaded dozens of packages and my basic problem is that the computer doesn't seem to even notice the existence of my keyboard. I'm also clueless as to what software to use for the actual rendering of the sound.   When working, the power led should stay red after i turn on the keyboard. When not working, the power led only flashes red once.  If someone would be willing to help me out, i'd be a million times grateful.   It may be relevant to point out i'm using Ubuntu (latest version 11.10 i think), and not Ubuntu Studio, but i'm assuming i will find more expertise here. (Sorry about the wall of text, the forum seems to destroy my &quot;enters&quot; every time i edit).

---

### Post by sgx on 2011-11-16
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Hi, use the 4th and 8 links in the list at the wiki,
for screenshots and the info to set up and use your
controller. You'll see that connections are presented
for hardware and software, inputs on one side, outputs
on the other, select one on each side, and press the
connect button.

Once you have the sound i/o, 
you can install and use timemachine as an easy recording software,
and audacity to edit and convert its .w64 sound files.

The zynaddsubfx synthesizer example from the wiki has soundbanks,
Use the menu Instrument -->Show instrument bank. An empty panel
will appear, so at the top, by the Refresh Bank List button, click
the little black triangle, and the list of banks will appear.
You can experiment using midi learn on the various synth controls,
and behringer controller devices.
(don't hesitate to ask, there is a lot of linux audio that is obvious the third time through, but almost invisible the first time :guitar:

Cheers

---

