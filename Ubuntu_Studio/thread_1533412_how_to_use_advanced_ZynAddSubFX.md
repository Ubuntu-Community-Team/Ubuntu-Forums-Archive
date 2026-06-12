---
title: "how to use advanced ZynAddSubFX"
date: 2010-07-17
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-17
Finally got Rosegarden to do what I wanted, it is really great.  Playing around with ZynAddSubFX I discovered there is a LOT of stuff available for making instruments if one chooses the advanced display, as opposed to the beginner display.  Are there any help files, instructions, tutorials etc. for this software?  It sure is interesting.

---

### Post by Pablo_F on 2010-07-18
Hi!

I don't use zynaddsubfx but I suggest you google for "youtube zynaddsubfx". There is even a youtube channel by the author himself, Paul Nasca.

[http://www.youtube.com/user/zynaddsubfx](http://www.youtube.com/user/zynaddsubfx)

On the other hand, you should know that there is a rewrite of zynaddsubfx, called yoshimi, which is more "jack-friendly" but it is the same synth basically. See:

[http://yoshimi.sourceforge.net/](http://yoshimi.sourceforge.net/)

You can get yoshimi easilly and reliably from autostatic PPA, if you are in lucid or karmic.

[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

If you go for yoshimi, as it uses jack midi (it shows up in the MIDI tab of qjackctl) you will need to launch a2jmidid (alsa midi to jack midi bridge daemon) so you can make the MIDI connections.

Cheers! Pablo

---

### Post by sgx on 2010-07-18
> **raymondvillain said:**
> Finally got Rosegarden to do what I wanted, it is really great.  Playing around with ZynAddSubFX I discovered there is a LOT of stuff available for making instruments if one chooses the advanced display, as opposed to the beginner display.  Are there any help files, instructions, tutorials etc. for this software?  It sure is interesting.
at this link are many fine tutorials:

[http://www.soundonsound.com/sos/allsynthsecrets.htm](http://www.soundonsound.com/sos/allsynthsecrets.htm)

Dig in!

for the additive part,

[http://emusician.com/tutorials/additive_synthesis/](http://emusician.com/tutorials/additive_synthesis/)

[http://www.soundonsound.com/sos/jun00/articles/synthsec.htm](http://www.soundonsound.com/sos/jun00/articles/synthsec.htm)

In general, check out sounds you like, carefully adjust filters, resonance, misc controls, and take notes. Deconstruct, and rebuils new ones. Use the ADSR envelope controls to shape sounds

attack
delay
sustain
release

from beginning to end. 
There is a 'load all parameters' menu option in zyn, use it to access the extra soundbanks found on the net, or at the zyn website, they contain files with a .xmz extension, made using zyns save functions. Other zyn presets have .xiz extensions.

Cheers

---

### Post by techx4 on 2010-07-21
> **Pablo_F said:**
> Hi!

I don't use zynaddsubfx but I suggest .......

Great links and suggestions, I did not know about yoshimi

 thanks!

---

### Post by hardcopy on 2010-07-22
> **sgx said:**
> 
attack
delay
sustain
release

actually the D in ADSR stands for Decay; the time in which the envelope goes from the attack peak to the sustain level. if the sustain level is the same as the attack peak it can be considered a Hold period, as a delay would generally describe a pause before starting an enevelope.

---

### Post by sgx on 2010-07-24
the difference between typo and braino is greater than
the distance between the l key and the c key  ;) thanks for
reminding folks the proper definition. :)

---

### Post by hardcopy on 2010-07-26
ahhh phew good to hear theres not some misconception going around about that

sorry for the somewhat overzealous pedantry :D

---

