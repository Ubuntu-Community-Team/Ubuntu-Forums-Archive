---
title: "Qmidiroute/Qmidiarp"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by Ouoertheo on 2008-05-20
Has anyone got Qmidiroute or Qmidiarp to work? I have them showing up in jack. But when I connect my midi kb to them, then connect them to  zynaddsubfx or anything else, neither of the two programs output any midi signals. When I look at the log pages, there is signal going in. Any feedback from people who have got this working would be greatly appreciated.

---

### Post by rfs13286 on 2008-06-03
Hello
I can get QmidiArp to work just fine. My only problem is that I don't understand how to use it yet :)

Anyway you can test it if you load up an example demo.

Try to rig up your connections with qjackctl so that: in the Audio tab your synths (ZynAdd or other) audio go directly to the system outputs and in the ALSA tab the midi connection goes like this:

yourKeyboard out -> QMidiarp
QMidi-arp1 -> zynaddsubFX

that should take care of connections. Now in QMidiArp load the file demo_up_down.qma that is located in /usr/share/qmidiarp

Hopefully you can now play on the keyboard and have an arpeggio effect.
I Hope this helps.

---

