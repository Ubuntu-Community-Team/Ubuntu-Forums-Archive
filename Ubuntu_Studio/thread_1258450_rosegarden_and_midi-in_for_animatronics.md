---
title: "rosegarden and midi-in for animatronics"
date: 2009-09-05
forum: Ubuntu Studio
---

### Post by dwavo on 2009-09-05
[CENTER]**A MIDI-OPERATED PNEUMATIC HAUNTED HOUSE**[/CENTER]
I'm interested in using the rosegarden sequencer for controlling not only midi sound, but lighting, and some pneumatics; both of which are yet another output device to MIDI. I am using an Opto22 relay board to convert from 5vdc to 24vdc power relays.
 
I plan to base my design on tom scarff's miduino, which is a midi card that accepts 4 analog inputs, and provides 12 analog outputs (5vdc). the midi-out seems straight forward. I can lay down a drum beat - for example - and control the lights.
 
The issue is handling the midi-inputs. We tested a number of sequencers and unfortunately the MIDI Start, Stop and Continue do NOT work. It seems that when you put sequencers into external Sync mode they also need an external clock signal. Unfortunately the miduino will not accomodate this function in its design. 
 
A corrollary in music would be using an input (pedal) switch to start different (drum) tracks. I'm just trying to use an external analog device (pedal, or trip switch) to start a series of events. (sounds, lights, and other 24volt gizmos). 
 
I've seen midi used instead of DMX for controlling lights. So I know the output side will work. Any advise on interfacing with an input device using something like the midiuno would be greatly appreciated.

---

