---
title: "Can get MIDI working in Muse"
date: 2009-11-21
forum: Ubuntu Studio
---

### Post by mendota on 2009-11-21
Hi,
I recently installed Ubuntu Studio, in hopes that it would work better for audio/midi production than Mandriva. Well, it has, as jackd is running perfectly, Muse records audio, and Linux Multimedia Studio is smoothly working with midi. Unfortunately, midi will not play in Muse. I have successfully inserted notes and I think the patch set, channels, and volume/velocity settings are set properly, but it wont make a peep. 

Something tells me that LMMS is working too easily to be true. Looking through all the settings for midi, I am completely confused. Any help would be greatly appreciated. As a workaround, I can transfer my audio to LMMS and create the midi pieces there, then export the midi to Muse, perhaps? Actually, it would make no sense if Muse could play an imported midi file. I would try that if I had a midi file, but it doesnt look like LMMS can export as a midi file.

---

### Post by sgx on 2009-11-22
Hydrogen drum machine can export midi files, and there are lots of free midi files to download after a brief google. You have to have a soundsource to play back the midi data, and it will likely need to be chosen in the various preferences/defaults dialogues. Timidity is a common software playback source that you can install, and the FluidR3 general midi soundfont can be selected as an alternate sound source in the file
/etc/alternatives/timidity.cfg

Maybe the midi sound source also needs connecting in qjackctl, not sure about that, but midi input devices will be in the alsa tab of qjackctl,
and need to be connected.

Cheers

---

### Post by mendota on 2009-11-22
I found a midi file and just as I expected, Muse cant play it. I will have to work on this some more, but in the meantime, thanks for your help!

---

### Post by sgx on 2009-11-23
> **mendota said:**
> I found a midi file and just as I expected, Muse cant play it. I will have to work on this some more, but in the meantime, thanks for your help!
Just started a realtime kernel, installed Muse, connected to my XG keyboard, loaded a midi file, began configuring...heres what I chose

menu Settings --> Midi Port/Softsynth

for Instrument -I chose XG, from the dropdownlist opened from clicking the black triangle widget by each channel.  Your choice depends on your soundsource, but you get silence without one. 

For Device, choose your midi sound source, mine is the souncard, connected to the XG keyboard. What is yours? Timidity++
or zynaddsubfx might work, and you might have to choose qjackctl here,
and then make connections there. The midi files I have play fine. Muse connected itself to my soundcard, and shows in qjackctl

Does your midi file display properly, and respond to the transport controls?

Cheers

---

