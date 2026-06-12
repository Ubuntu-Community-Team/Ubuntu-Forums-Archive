---
title: "MIDI Keyboard?"
date: 2009-09-02
forum: Ubuntu Studio
---

### Post by jayjay960 on 2009-09-02
Hi,

I have an Evolution ekeys 49 MIDI keyboard that I use a lot with windows. Recently I've been trying to get it to work with Ubuntu 9.04, just so I can play at least. Unfortunately I've discovered I haven't got a clue ho MIDI works in Linux. Can anyone tell me what I need to download just to be able to hear sound from playing my MIDI keyboard? So far the MIDI-related applications I've downloaded are jackd, qsynth and midish. But
a. I have no idea how to use these programs
b. I'm pretty sure I need more/different programs


Can someone help?

---

### Post by Megatron3000 on 2009-09-02
same here, i have an m-audio oxygen 8v2 keyboard, and it is recognized in the alsa sequencer, but that's it. no idea so far about how to have it just work.

---

### Post by thisllub on 2009-09-02
> **jayjay960 said:**
> Hi,

I have an Evolution ekeys 49 MIDI keyboard that I use a lot with windows. Recently I've been trying to get it to work with Ubuntu 9.04, just so I can play at least. Unfortunately I've discovered I haven't got a clue ho MIDI works in Linux. Can anyone tell me what I need to download just to be able to hear sound from playing my MIDI keyboard? So far the MIDI-related applications I've downloaded are jackd, qsynth and midish. But
a. I have no idea how to use these programs
b. I'm pretty sure I need more/different programs


Can someone help?

Try qjackctl and patch the inputs to a soft synth.

It does take a lot more fiddling to work it out than Windows.
Once you get it worked out it isn't too bad.

---

### Post by rjawad on 2009-09-02
Hello, 

I'm having trouble with my midi keyboard in linux too.

I'm running ubuntu studio 9.04.  I have a yamaha p-140 keyboard with the ux16 usb-midi adaptor.  

from what i've read, ubuntu should just detect the keyboard, but nowhere do i see it showing up.  

jackd is running fine, as far as i can tell.  the midi tab under the connections doesn't show anything.

when i do cat /dev/sndstat, i get:
midi devices:  NOT ENABLED IN CONFIG

i read somewhere that i should run modprobe snd-usb-audio
but when i do that, i get an error:
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-3-rt/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-3-rt/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-3-rt/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.28-3-rt/kernel/sound/usb/snd-usb-audio.ko): Unknown symbol in module, or unknown parameter (see dmesg)

so, i'm stuck.
the piano works fine in vista.

any help would be appreciated.

oh, i should mention that i have a x-fi soundblaster card which i got working following this wiki
[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)
i followed it exactly and so unloaded some alsa stuff, which might have something to do with my usb-midi problem.


Thanks, 
Ryan

---

### Post by Megatron3000 on 2009-09-03
the howto about setting up and connecting jack will tell you all about this, luckily: 
  [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) 
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections) 
 
i still am very far away from a working audio station, but i got some notes out of a synth with my keyboard

---

### Post by jayjay960 on 2009-09-06
Ok, well I think I understand linux MIDI a bit better now, but it's still not working for me. Using qjackctl, I've managed to connect vkeybd to zynaddsubfx, and zynaddsubfx to system, which works, and I get playback from the virtual keyboard. However, I tried to connect my MIDI keyboard to zynaddsubfx, but it wouldn't connect. Upon further research, I read that you needed to connect external MIDI keyboards to seq24, then connect that to zynaddsubfx. So I ran seq24, but it didin't even appear in the qjackctl connections window. After a lot of fiddling around, I've managed to get it to appear. However, I still can't connect my MIDI keyboard to it (vkeybd works). Does anyone know why?

---

### Post by xyclo on 2011-02-04
Hey, I see this has long been abandoned, but I have answers that might serve you or others... I am so excited  about this finally working, that I decided to share. 

About the original question, just running Jack and ZynAddSub, and connecting them in the Connections>Midi window, allows you to play ZynAddSub with your keyboard (connected through Jack).  
The other question, about connecting to Seq24, is what got me here, since I had the same problem. The solution (which I got from my (new) buddy [lsd] on freenode...) is  running:

j2amidi_bridge

, which is part of the package a2jmidid. It brings up a bridge in the  "midi" connections window of jack, to which you can connect the midi  input your keyboard is connected to. Then in the "alsa" window  connect to "midi through 0", which is a "midi input" option in seq24. I  am still figuring out how it all works but I can already record in seq24  with the external midi keyboard connected through jack!

For reference, I did all this in Ubuntu-Studio 10.04, using Jack 1.9.7, Seq24 0.9.2, and a2jmidid version 6-0ubuntu2.

Cheers.;)

By the way, [lsd] has some nice tutorials on using seq24 at:
[http://wootangent.net/2010/10/linux-music-tutorial-seq24-part-1/](http://wootangent.net/2010/10/linux-music-tutorial-seq24-part-1/)

---

