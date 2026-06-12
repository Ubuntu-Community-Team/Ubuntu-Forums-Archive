---
title: "Recording midi from external midi keyboard"
date: 2011-10-02
forum: Ubuntu Studio
---

### Post by deepesh on 2011-10-02
Hi,

How do I record midi played on connected midi keyboard.
I am able to play midi files on the keyboard but not able to record from it.

$pmidi -l
 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
 20:0     DigitalKBD                        DigitalKBD MIDI 1
128:0     TiMidity                          TiMidity port 0
128:1     TiMidity                          TiMidity port 1
128:2     TiMidity                          TiMidity port 2
128:3     TiMidity                          TiMidity port 3

$pmidi -p 20:0 some-midi-file.mid #works fine


But how do I record anything played on DigialKBD?

kmidimon shows midi events when external midi keyboard key is pressed.

Thanks,
Deepesh

---

### Post by jejeman on 2011-10-02
To record midi you need to use midi sequencer.
To name a few: Muse, Seq24
You need to connect keyboard to sequencer inside the sequencer application in order to recive notes.
Each application has its own ways.

---

