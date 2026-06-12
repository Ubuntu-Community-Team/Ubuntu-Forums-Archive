---
title: "[SOLVED] Alsa setting for firewire soundcard"
date: 2008-10-13
forum: Ubuntu Studio
---

### Post by DARKAD on 2008-10-13
I saw many posts of people with firewire soundcards playing with linux and dealing with many differents matters.

Now if one uses a pc with only one soundboard, firewire kind; which is the right configuration for alsa?

p.s. At the moment I'm using jack with freebob, pulseaudio and jack sink pulse module; everything seems to work fine, but I'm not sure if there is something to take care about alsa.

---

### Post by robeast on 2008-10-13
You don't need to worry about alsa, freebob is driving your firewire hardware.

---

### Post by DARKAD on 2008-10-30
Ok you are right!

There was a little thing to do for my sys configuration:

I add these next lines from: 

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

ALSA Sequencer

If you can not have midi sequencing enabled, or if you have midi error message, the Alsa midi sequencer module of the kernel may not be loaded. Try that:

 sudo modprobe snd-seq

If it works, to have your system load it at bootup, you have to add it to the /etc/modules file, do:

 sudo su -c 'echo snd-seq >> /etc/modules'

---

