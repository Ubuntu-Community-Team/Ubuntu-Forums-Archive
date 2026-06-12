---
title: "Real-time plug-ins"
date: 2011-11-26
forum: Ubuntu Studio
---

### Post by Eiji Takanaka on 2011-11-26
Yo dudes/dudettes,   A few questions for those who may be able to help, if i may...  I've recently been experimenting with audacity a bit and as far as i can tell there are no real-time plug-ins. Which is a real shame considering the real-time kernel available, not to have real-time plug-ins.   Does anyone know if there are any current sound 'platforms' i.e audacity that allow the use of real-time plug ins?   Or would you need a particular module fired perhaps into jack and then output into the required program?  I haven't experimented properly with jack yet, but im assuming its somewhat akin to a patchbay? Audio stream in's and out's ;)  The mini-adventure/experiment i'm hoping to conduct is this.  Using a vocoder (tried audacity it has them although not real-time! (bah-humbug) to prank call my brother with a robot voice.   Now firstly i suppose i would need an external module or vocoder program correct? Then i would assume that i would pipe the output of that program into jack which can then throughput the signal to say skype (although saying that would you need to specify the input path in skypes programming?). Resulting in hopefully a crazy sounding voice over skype.   I'm guessing this should be able to be done, but think it may take modification perhaps in the programming of one or more programs? I.e defining input/output audio stream paths.   Any thoughts/ideas would be greatly appreciated,  Cheers!  - dan

---

### Post by jejeman on 2011-11-26
For real time effects you need to use jack.
Now it depends what you want to achive, but to alter voice on Skype, for example, you would need stand alone aplication.
You can use rakarrack or lv2rack to utilise lv2 plugins, or calf's plugins for jack.
To do realtime effects on audio files, you can use DAW, and insert plugins on track where audio file is imported.

---

### Post by sgx on 2011-11-26
> **Eiji Takanaka said:**
> Yo dudes/dudettes,   A few questions for those who may be able to help, if i may...  I've recently been experimenting with audacity a bit and as far as i can tell there are no real-time plug-ins. Which is a real shame considering the real-time kernel available, not to have real-time plug-ins.   Does anyone know if there are any current sound 'platforms' i.e audacity that allow the use of real-time plug ins?   Or would you need a particular module fired perhaps into jack and then output into the required program?  I haven't experimented properly with jack yet, but im assuming its somewhat akin to a patchbay? Audio stream in's and out's ;)  The mini-adventure/experiment i'm hoping to conduct is this.  Using a vocoder (tried audacity it has them although not real-time! (bah-humbug) to prank call my brother with a robot voice.   Now firstly i suppose i would need an external module or vocoder program correct? Then i would assume that i would pipe the output of that program into jack which can then throughput the signal to say skype (although saying that would you need to specify the input path in skypes programming?). Resulting in hopefully a crazy sounding voice over skype.   I'm guessing this should be able to be done, but think it may take modification perhaps in the programming of one or more programs? I.e defining input/output audio stream paths.   Any thoughts/ideas would be greatly appreciated,  Cheers!  - danHi, read up at links 4 and 8 at the wiki, with screenshots
and docs for the jackd connections gui:

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

More details are here

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

If you make a live sound source during the connections process,
you'll hear when successful, something heavy on a midi keyboard,
a CD playing, connected to soundcard line-in etc
Cheers

---

### Post by Eiji Takanaka on 2011-11-28
cheers dudes =)

---

