---
title: "Terratec sound cards"
date: 2010-04-11
forum: Ubuntu Studio
---

### Post by brianmc on 2010-04-11
I've just ordered a replacement sound card for my system - a Terratec DMX 6, if that means anything to people.

This fl-ebay auction has a pic of the card...

[http://cgi.ebay.co.uk/Terratec-DMX-6-Fire-Audio-Interface-Card_W0QQitemZ150430640403QQcmdZViewItemQQptZMidi_Controllers?hash=item23065d6913](http://cgi.ebay.co.uk/Terratec-DMX-6-Fire-Audio-Interface-Card_W0QQitemZ150430640403QQcmdZViewItemQQptZMidi_Controllers?hash=item23065d6913)

A musician friend who's been doing music stuff for years on Windows has one, is partway through tweaking Ubuntu to work properly with one, but the big issue is making it work with the realtime kernel.

Does anyone have one of these babies, and care to share JACK settings and such?

I'm working from a 32 bit setup, installed the vanilla 9.10, added Medibuntu stuff, installed the realtime kernel and several ubuntu studio packages. My friend has ended up totally removing pulseaudio from a similar setup and adding ALSA for 'normal' use of the card.

So, while getting details of his settings might be possible, any tips or tricks greatly appreciated. Do people use - as I'm trying - different user accounts when in realtime/non-realtime kernels? How do you set up your ~/.asoundrc? What JACK settings do you use? Any tips on dealing with systems with a couple of sets of audio hardware? (Mobo audio stuff, plus dedicated card).

I should get the new toy middle of this week, I'd love to hit the ground running with it.

---

### Post by Pablo_F on 2010-04-11
If I am not wrong that card uses the snd_ice1712 alsa module (check with "cat /proc/asound/modules"), the same as mine, which is a m-audio audiophile 2496. 

That card is reported to work flawlessly in Linux. Just google for it.

I don't use different accounts for my user. I can do music and desktop (internet, office...) use with the rt kernel but for a session in which I won't do audio work, I normally launch the generic kernel. However, I think it could be an option having an "audio user" and a "Desktop user", but that is up to you and it depends on your workflow.

My jack setup, in case it helps:

[http://imagebin.ca/view/nllDjQnX.html](http://imagebin.ca/view/nllDjQnX.html)

I don't have a .asoundrc file. In a normal setup I don't think it is needed at all.

Yes, you might need to uninstall pulseaudio, I am not sure.

You have to look here:

zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

Module snd-ice1712
------------------

Module for Envy24 (ICE1712) based PCI sound cards.

* MidiMan M Audio Delta 1010
* MidiMan M Audio Delta 1010LT
* MidiMan M Audio Delta DiO 2496
* MidiMan M Audio Delta 66
* MidiMan M Audio Delta 44
* MidiMan M Audio Delta 410
* MidiMan M Audio Audiophile 2496
* TerraTec EWS 88MT
* TerraTec EWS 88D
* TerraTec EWX 24/96
* TerraTec DMX 6Fire
* TerraTec Phase 88
* Hoontech SoundTrack DSP 24
* Hoontech SoundTrack DSP 24 Value
* Hoontech SoundTrack DSP 24 Media 7.1
* Event Electronics, EZ8
* Digigram VX442
* Lionstracs, Mediastaton
* Terrasoniq TS 88

Below that:

model (between others): dmx6fire

Now you have to edit:

$gksudo gedit /etc/modprobe.d/alsa-base.conf

Add at the end of the file this line:

options snd-ice1712 model=dmx6fire

Reload the alsa modules:

$sudo alsa force-reload

Use envy24control to set the levels of the card. (Analog volume tab)

You need 

$sudo apt-get install alsa-tools-gui

$envy24control

Check [www.linuxmusicians.com](www.linuxmusicians.com) for lots of useful information

I hope this helps, Pablo

---

