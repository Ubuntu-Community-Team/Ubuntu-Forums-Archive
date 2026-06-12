---
title: "QjackCtl and linuxband"
date: 2013-10-27
forum: Ubuntu Studio
---

### Post by msaether on 2013-10-27
Having problems with the sound from linuxband. I managed to install linuxband and mma. I can make midi files and play them from mma. I start up jack nad start linuxband. Seems to work but no sound. When I click at the connections tab in qjackctl I see three more tabs. Audio, Midi and Alsa. I can see Linuxband in the Midi tab output ports but I have no iput port options. Is this why I don't have sound? and how can I fix it?
I have tried different settings. interface, input ports, hw:0, hw:1 etc.

---

### Post by su:bhatta on 2013-10-27
Hi, this is what you have to do.

 1)Start up Jack, using QjackCtl, then start up Qsynth. In the Connections tab of Jack you will see Qsynth in the Midi tab , Input Ports. 
 2)Then start Linuxband, it will show up in the Connections Tab under Midi , Output Ports. Now connect it to Qsynth using Jack Connections tab. 

Then play mma files and you will get sound.

**Note**: One more thing, you have to do:  go to 'Set Up' in Qsynth and choose under Midi Tab, Midi driver: Jack and under Soundfonts Tab /usr/share/sounds/sf2/FluidR3_GM. Restart Qsynth.

You can use Patchage to do the connections it provides a nice UI.

P.S.: Basically, Linuxband can read and play mma files but you need a sound generator like Qsynth (UI for Fluidsynth) or ZynJackU to get the sound file played.

---

### Post by msaether on 2013-10-27
Thanks a lot! Using qsynth did the trick of course.

---

### Post by su:bhatta on 2013-10-27
Welcome to Linux for Creative Humans.

 Glad to help. It had to, I regularly use it, though now more with ZynJackU.

Try ZynJAckU and Patchage, both are great  programs.

Please mark the Thread as 'Solved' using 'Thread Tools' at the top right of Page.

---

