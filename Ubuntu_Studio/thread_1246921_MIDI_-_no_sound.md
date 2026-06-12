---
title: "MIDI - no sound"
date: 2009-08-22
forum: Ubuntu Studio
---

### Post by minimustangs on 2009-08-22
I downloaded some General MIDI drum maps. They play when double clicked in the default player ( Movie Player). That would be fine if I just wanted to listen to them, which I don't...I want to be able to edit them and speed up / slow down as required.

I have installed a variety of Multimendia s/w, LMMS, Audacity, Muse, and even Hydrogen.

None will play the MIDI files. Some will allow me to import or open, but when  I play it, I get no sound. Audacity seems to allow me to import even though it doesn't allow creation of MIDI tracks, unless I missed something somewhere. When I point the import window to a known location of .MID file, it doesn't see them. I do get a MIDI error from one of the s/w packages...which leads me to think I haven't started a service or somthing similar. I am very familiar with the ins and outs ( pun intended) of audio recording under WinXP, but not so much with Linux.

Really all I want is a quick and dirty drum machine - something I can load MIDI drum tracks into. I don't want a second recording environment, I already have that setup in my studio.

Thanks...

UPDATE:
When I look at JACK - CONNECTIONS and look under MIDI I see nothing, but under the ALSA TAB I see MIDI THROUGH and Timidity. Don't know what they are, but I think there is my problem. How do I make a Midi file play ?

---

### Post by Addiction2Code on 2009-08-22
I don't know too much about your problem or MIDIs for any case, however; you must have Timidity INSTALLED and working! You have to have the MIDIs playing through Timidity, else you will get no sound. Can you play the MIDIs at all? Could you ever play any other MIDI file on your computer?

---

### Post by minimustangs on 2009-08-22
Welll I turns out TImidity wasn't installed, but that didn't solve my issue. Since installing Timidity, Hydrogen stopped working.

Jack may not be running. How do I check?

is there anyone with mutlimedia/multirack/midi experience

---

### Post by Jormeliini on 2009-08-23
> **minimustangs said:**
> 
Jack may not be running. How do I check?

You can start Jack with qjackctl if it is installed. Qjackctl is graphical interface for jack.

And if you want to check if jackd is running try following. If it does not output anything jackd is not running.
```

ps -A | grep jackd

```

---

