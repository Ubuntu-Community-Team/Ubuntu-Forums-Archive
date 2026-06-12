---
title: "midi foot controller"
date: 2010-10-01
forum: Ubuntu Studio
---

### Post by mdiaczyk on 2010-10-01
Hi I have a midi foot controller a Digitech Mc7.  What I want it to do is start loops in seq24 and Hydrogen.   I plugged the pedal into the midi in.  What do I need to do to make this work.  Thanks Mike

---

### Post by sgx on 2010-10-02
Hi, this topic relates to other Digi gear, perhaps a start?
Cheers

[http://ubuntuforums.org/showthread.php?t=1494277](http://ubuntuforums.org/showthread.php?t=1494277)

---

### Post by AutoStatic on 2010-10-02
> **mdiaczyk said:**
> Hi I have a midi foot controller a Digitech Mc7.  What I want it to do is start loops in seq24 and Hydrogen.   I plugged the pedal into the midi in.  What do I need to do to make this work.  Thanks MikeTell Hydrogen and Seq24 to react on incoming CC messages from your controller. No idea about Seq24, I don't use it, but with Hydrogen it's perfectly possible. You do need at least Hydrogen 0.9.5 beta 2 for this to work afaik. It has MIDI learn functionality in the Preferences - Midi window.
And what kind of MIDI-in port are you referring to?

---

### Post by mdiaczyk on 2010-10-03
I made some progress; here is what I did.  I setup my Yamaha Qy 100 to make sure my usb midi adapter is working.  I had hydrogen record the midi event when I pressed a key on the Qy 100.  I could start and stop hydrogen with this.  I want to test the foot controller to make sure it works.  Mike

---

### Post by mdiaczyk on 2010-10-03
Okay the foot controller works great for Rakanack which is very interesting.  The foot controller works.

---

### Post by mdiaczyk on 2010-10-04
Okay it works in sooper looper.  I even tried Qmidiroute.  What happens, when a pedal is pushed it says program change.  Program change is not there with Hydrogen.  This was designed for guitar amps and effects pedals.  Maybe learning how to reroute the signal from program change to something else will fix it. Mike

---

### Post by AutoStatic on 2010-10-04
> **mdiaczyk said:**
> Maybe learning how to reroute the signal from program change to something else will fix it. MikeCool that it works! You can use QMidiRoute to route incoming program changes to notes or CC messages. But isn't it possible to program the QY100 so it outputs CC messages when you use the footswitch?

---

### Post by mdiaczyk on 2010-10-04
It probably is possible to program the Qy 100 to do this.  I have not had any time to look at it.  I think this has more to do with Hydrogen than Ubuntu.  If Hydrogen had a program change message it would work.  I am going work with Qmidiroute.  I will post to the Hydrogen forum about this.  Consider it solved. Thanks for all the help.

---

