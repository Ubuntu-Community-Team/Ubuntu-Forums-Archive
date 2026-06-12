---
title: "Virtual Keyboard Jack, Qsynth, qjackctl No sound"
date: 2011-01-27
forum: Ubuntu Studio
---

### Post by hwttdz on 2011-01-27
I'd love to get a physical musical keyboard and connect it to my cpu, but before doing this I'm trying to get all the software set up to make sure it's possible. I've followed a few different tutorials, and it seems that between zynaddsubfx and qsynth (or at least from what I've read), I can get more realistic sounds from the latter so that's what I'm working on at the moment. I followed this tutorial [http://ubuntuforums.org/showthread.php?t=1003466](http://ubuntuforums.org/showthread.php?t=1003466) (and needed to do this [http://ubuntuforums.org/showthread.php?t=276499](http://ubuntuforums.org/showthread.php?t=276499) to get a snd-seq issue ironed).

So where I stand now is that I can start qsynth, vkeyboard, and qjackctl. I can successfully link the virtual keyboard with the synth input in qjackctl. A soundfont (fluid-soundfont-gm) is loaded. And when I click on keys on the virtual keyboard the little light in qsynth lights up (I suppose implying that it's doing something). Of course now we get to the issue which is that despite things appearing that they're working well, there is no sound. And yes speakers are on, volume is up and sound works in every other way (I'm listening to music as I write).

So any suggestions? I don't see much in the way of error messages,

qsynth complains that:
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
Cannot lock down memory area (Cannot allocate memory)

This is despite me giving the audio group realtime privileges during the jack install (but I didn't add me to audio), didn't read any mention of this anywhere.

---

### Post by sgx on 2011-01-28
start qjackctl, by command, menu, or icon, and click its setup button, and on the panel that opens, at the middle-far-right,

Input Device >
Output Device >

click the > widgets, to see your soundcards/chips. 

Now run the lsmod command to see the list of kernel modules, its output should include something similar to what appears in those > dropdown lists.
Choose one, and then restart qjackctl. Zynaddsubfx has a virtual keyboard button on its gui, and requires a connection in the audio and alsa sections of the connections tabs in qjackctl.

It helps to post your soundcard and motherboard details, as there are lots
of variables to consider!

If you google for hydrogen ardour youtube, many of the videos will cover qjackctl.

Cheers

---

### Post by Pablo_F on 2011-01-28
Hi, 

You should add your user to the audio group and restart the computer. rtprio and memlock privileges are given to the members of the audio group.

As for the sound, check that qsynth (fluidsynth) outputs are connected to the system: playbacks in the audio tab of qjackctl's connections window (in adition to the alsa midi connection from vkeyboard to fluidsynth). And make sure that jack is using the soundcard that you want to get sound from.

Note that you can have sound through pulseaudio but jack is another beast. I suggest you install aqualung (a jack-aware audio player) and try to play a song when jack is running. 

You can give us the terminal output of aplay -l so we can see your soundcard(s) and playback devices and try to give better help.

BTW, a much better virtual midi keyboard is called vmpk. You can load your own keymaps and all. I think you will find it in the software center.  [http://vmpk.sourceforge.net/](http://vmpk.sourceforge.net/)

Cheers, Pablo

---

