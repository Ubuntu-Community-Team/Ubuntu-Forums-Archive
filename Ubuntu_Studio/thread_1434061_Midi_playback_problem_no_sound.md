---
title: "Midi playback problem :no sound"
date: 2010-03-19
forum: Ubuntu Studio
---

### Post by RED666 on 2010-03-19
Hi all,
I just installed Ubuntu 9.10 (c.q. Linux) for the first time ever and I am impressed. But for Ubuntu to work for me I need to be able to score music. To be very clear I'm an Ubuntu larva (exp=0).

My problem:
I run Ubuntu from a pc with an  ASUS P5G41-M LX motherboard with an onboard ALC662-VC1 soundcard. I tried NTedit an Muse to play some of my midi files, I can read the score but I don't get any sound (normal audio is ok), in NTedit the notes do get played (i.e. notes turn red etc) but no sound. But if I play** the same file** on Totem mediaplayer I do get sound!

Can anybody tell me how to solve this. Ik keep reading everywhere that you need to have a combination of software to run for instance Rosegarden or Muse (I liked these editors best). But I get lost in all those packages.

 Yelp..

P.S. Could it be hardware related? How would I find out, there is no appearant problem reported by Ubuntu.

---

### Post by gordintoronto on 2010-03-19
If Totem plays the MIDs, your difficulty is in configuring NTedit or Muse. You might also look at Volume Control to see if any "source" is muted. (Click on the speaker icon near the top-right of the screen and select "volume control.")

---

### Post by RED666 on 2010-03-19
No nothing muted... Good to know 4 sure that it isn't a harware problem, thanks.

Anymore ideas ?

---

### Post by raboofje on 2010-03-20
> **RED666 said:**
> I tried NTedit an Muse to play some of my midi files, I can read the score but I don't get any sound (normal audio is ok), in NTedit the notes do get played (i.e. notes turn red etc) but no sound. But if I play** the same file** on Totem mediaplayer I do get sound!

ntedit does not have an embedded synthesizer, it registers itself as an ALSA MIDI source and you'll have to connect it to some synth yourself. Timidity or QSynth with the fluid-soundfont-gm should be good choices.

See [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo) for more on softsynths.

MuseScore worked out-of-the-box for me. Under 'Preferences'->'I/O', 'Use internal synthesier' is checked, the soundfont is /usr/share/sounds/sf2/FluidR3_GM.sf2

---

### Post by RED666 on 2010-03-21
Hi Raboofje, I'm halting my own research on this subject for the moment( on my pc). But I was trying to find out how it works for a friend (on his pc).

Could you maybe give him a hand? I submitted my topic here because his topic on the Dutch forum didn't get any (helpfull) replies.

His topic [http://forum.ubuntu-nl.org/software-en-configuratie/muziek-software-52689](http://forum.ubuntu-nl.org/software-en-configuratie/muziek-software-52689)

Thnks

p.s. A little bird told me you're Dutch

---

### Post by raboofje on 2010-03-21
> **RED666 said:**
> I submitted my topic here because his topic on the Dutch forum didn't get any (helpfull) replies.

His topic [http://forum.ubuntu-nl.org/software-en-configuratie/muziek-software-52689](http://forum.ubuntu-nl.org/software-en-configuratie/muziek-software-52689)

Perhaps you could point him to this thread? I'm not a member of ubuntu-nl.

---

### Post by RED666 on 2010-03-21
Will do, actually....  I'll tell him to create a new thread for his problem. I will keep this thread open to adress my problem (eventually) ! 


By the way I was following the link J send me to get Jack working: [https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support")

But when I get to the heading[SIZE=2] "Configuration of more than one pci/usb sound/midi card"[/SIZE], I couldn't find the name of one of my soundcards (onboard Realtek ALC859) anywhere, in fact in the "alsa matrix" there isn't an entry for Realtek.

Any idea's?

---

### Post by RED666 on 2010-03-21
I already found it. 


**** Lijst van CAPTURE hardware-apparaten ****
kaart 0: CK804 [NVidia CK804], apparaat 0: Intel ICH [NVidia CK804]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: CK804 [NVidia CK804], apparaat 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 1: SAA7134 [SAA7134], apparaat 0: SAA7134 PCM [SAA7134 PCM]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 2: M2496 [M Audio Audiophile 24/96], apparaat 0: ICE1712 multi [ICE1712 multi]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: CK804 [NVidia CK804], apparaat 0: Intel ICH [NVidia CK804]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: CK804 [NVidia CK804], apparaat 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 2: M2496 [M Audio Audiophile 24/96], apparaat 0: ICE1712 multi [ICE1712 multi]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

---

