---
title: "Setting up MIDI"
date: 2010-11-28
forum: Ubuntu Studio
---

### Post by suddentwigs on 2010-11-28
Hi. I have been using Ardour for about 6 months on Lucid, using the  M-Audio Delta 1010LT audio interface. I recently added a controller  keyboard to my setup. I am fairly new to MIDI and am having a lot of  trouble routing - can anybody explain it to me from the top?

---

### Post by Pablo_F on 2010-11-28
Hi, 

What controller?

Cheers, Pablo

---

### Post by suddentwigs on 2010-11-29
The controller is an ancient Korg X5, which connects to the interface via a MIDI cable rather than USB. The update is that I've now managed to route the controller through the interface and into ZynAddSubFX, with which I have successfully generated sound, which I have routed into Ardour and recorded as audio. However I have yet to conquer midi arrangement - I tried using Rosegarden, it records the midi but without any sound, and runs very sluggishly. What is the best alternative, and do I need to use a seperate soft synth and arranger? If so, how should they be routed?

---

### Post by cchhrriiss121212 on 2010-11-29
Qtractor handles MIDI and audio. Ardour has planned MIDI support in the next version I think.

---

### Post by suddentwigs on 2010-11-29
Just had a quick look at Qtractor. Looks good. Will I be able to route to it straight from my interface, or would I need to go via a softsynth? And is its experimental status likely to cause difficulty for the midi novice?

---

### Post by cchhrriiss121212 on 2010-11-29
Qtractor has been more stable than Ardour in my experience, I have had it running for hours without issue. 
To record midi you just add a new track and select MIDI instead of Audio. You connect your device MIDI output straight to the MIDI input for the track, then connect a synth afterwards. To edit you can double click on the recorded sequence.

---

### Post by suddentwigs on 2010-11-29
So the chain goes: Controller keyboard -> audio interface -> (via Jack) Qtractor? Where does the softsynth come in the chain? Does it have a separate connection to Qtractor, or is it involved in the aforementioned chain?

---

### Post by cchhrriiss121212 on 2010-11-29
> So the chain goes: Controller keyboard -> audio interface -> (via Jack) Qtractor?Yes that's right. When you add a new MIDI track you will see a tab called Plugins, click Add and you will see a list of all your LV2, DSSI and LAPSDA plugins, some of which will be synths and some will be effects. Some synths are available as plugins and some are not. 

This is one way to do it, another is to connect the midi stream manually with jack to an external synth, then record the synth live via audio as you explained earlier. It is up to you.

**Edit**: LV2 plugins actually do not work very well with qtractor, it seems they cause crashes for some GTK related reason.

---

