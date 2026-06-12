---
title: "problems using m-audio keyboard with ubuntu"
date: 2009-07-23
forum: Ubuntu Studio
---

### Post by jimmyjazzstl on 2009-07-23
Hey folks. I just got an m-audio oxygen 8. I felt like a small child on Christmas morning opening that box, but then when I couldn't get any sound out of it through my computer I felt like the same child realizing that mom and dad forgot the batteries and there's nowhere to buy them. Needless to say I'm a little bummed.  Nevertheless, I have tried using this keyboard through rosegarden with qsynth running by going through the steps here [http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/)   However, I can only hear the metronome and no keyboard. They yellow bar starts and says its recording (while no sounds from the keyboard are being produced), when I hit stop it disappears.  I have tried ardour unsuccessfully. I really didn't know where to start with it and gave up very quickly.   I would really appreciate any advice. Thanks a lot for looking over my problem.  -James

---

### Post by Genius314 on 2009-07-23
It might be a problem with MIDI. I've had problems trying to get sounds out of Rosegarden, even just playing a MIDI file.

Maybe try a program like LMMS, and see if you have better luck?

By the way, how's the quality of the keyboard? I'm looking for a MIDI keyboard right now, and some reviews say M-audio feels cheap and plastic-y.

---

### Post by sgx on 2009-07-23
Hi, if O8 is a midi controller, it has no sounds, sends only midi data, so you need a midi softsynth/sampler to provide the various sounds. Rosegarden can sequence those sounds once you have some, so install zynaddsubfx, and qjackctl, and their dependancies using synaptic. Now assuming your O8 shows up in qjackctl, and you are familiar with it, connect zynaddsubfx and your O8 in the alsa tab, and in the audio tab, connect zynaddsubfx to system, and you should have some sounds.

The zyn menu Instrument --> Show Instrument Bank, opens a panel, click the triangle widget at the top to open a list of sound categories, over a
hundred excellent sounds to get going! 
Cheers

---

### Post by sgx on 2009-07-25
Hi, try this, has support for oxygen, radium, and keystation keyboards from made by maudio

sudo apt-get install midisport-firmware


its a firmware pack that mentions the Oxygen in the list of
midi products it provides for. less than 200k to install it.
Cheers

---

### Post by mrowl on 2009-09-12
Thanks sgx,

I followed your directions and had my borrowed midi keyboard up and running in no time.
Very simple, precise instructions that worked for me.

---

