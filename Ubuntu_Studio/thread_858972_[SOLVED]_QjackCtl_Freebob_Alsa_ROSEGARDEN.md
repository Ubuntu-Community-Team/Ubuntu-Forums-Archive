---
title: "[SOLVED] QjackCtl Freebob Alsa ROSEGARDEN"
date: 2008-07-14
forum: Ubuntu Studio
---

### Post by DARKAD on 2008-07-14
I'm trying to play a midi file with the 'general midi' pattern within ROSEGARDEN.

I've got a firewire audio device, actually it is possible for me to record and play audio with ubuntu studio 8 Hardy Heron, jack and freebob, but it's still impossible to hear any sound from midi files.

Please, if you see something wrong, suggest me how to correct settings.

Thanks in advance,
 Darkad

jackd:
00:27:46.323 Patchbay activated.
00:27:46.508 Statistics reset.
00:27:46.758 ALSA connection graph change.
00:27:46.886 MIDI active patchbay scan...
00:27:46.889 ALSA connection change.
00:27:47.091 MIDI active patchbay scan...
00:28:17.346 Startup script...
00:28:17.347 artsshell -q terminate
sound server terminated
00:28:17.794 Startup script terminated successfully.
00:28:17.796 JACK is starting...
00:28:17.797 /usr/bin/jackd -R -t2000 -dfreebob -dhw:0 -r44100 -p512 -n3 -D
00:28:17.817 JACK was started with PID=6224.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
00:28:18.369 ALSA connection graph change.
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
00:28:18.421 MIDI active patchbay scan...
00:28:18.426 ALSA connection change.
00:28:18.628 MIDI active patchbay scan...
00:28:19.855 Server configuration saved to "/home/darkad/.jackdrc".
00:28:19.859 Statistics reset.
00:28:19.967 Client activated.
00:28:19.979 JACK connection change.
00:28:19.988 JACK connection graph change.
00:28:20.183 Audio active patchbay scan...
00:28:31.586 Transport start.
00:28:31.668 Transport start.
00:28:50.420 JACK connection graph change.
00:28:50.531 Audio active patchbay scan...
........
........
00:29:54.705 MIDI active patchbay scan...
00:32:09.586 ALSA connection graph change.
00:32:09.734 MIDI active patchbay scan...
00:32:09.739 patchbayMidi: 130:3 rosegarden -> 129:1 FreeBoB Jack MIDI connected.
00:32:09.744 patchbayMidi: 130:3 rosegarden -> 14:0 Midi Through checked.
00:32:09.752 ALSA connection change.
00:32:10.076 ALSA connection graph change.
00:32:10.139 MIDI active patchbay scan...
00:32:10.148 patchbayMidi: 130:3 rosegarden -> 129:1 FreeBoB Jack MIDI checked.
00:32:10.157 patchbayMidi: 130:3 rosegarden -> 14:0 Midi Through checked.
00:32:10.175 ALSA connection change.
00:32:10.387 MIDI active patchbay scan...
00:32:10.390 patchbayMidi: 130:3 rosegarden -> 129:1 FreeBoB Jack MIDI checked.
00:32:10.393 patchbayMidi: 130:3 rosegarden -> 14:0 Midi Through checked.

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/QJackSetup.png[/IMG]

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/AlsaSetting_JackConnectionKit(Audio).png[/IMG]

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/JackConnectionKit(Midi).png[/IMG]

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/JackConnectionKit(Alsa).png[/IMG]

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/RosegardenPlayMidi.png[/IMG]

[IMG]http://web.tiscali.it/connessionegratuita/firefly302/RosegardenDevices.png[/IMG]

---

### Post by thorgal on 2008-07-14
what's the sampler or synth plugin ?
you need to associate a software synth or sound sampler to your tracks, otherwise rosegarden will not output any sound. You have two ways :

either apply a plugin to a track or open a software synth outside rosegarden (like amsynth, fluidsynth, whatever else), load a soundfont, connect rosegarden to it either via qjackctl or in the Manage MIDI Device section in rosegarden. Then apply the software instrument to the tracks. Rosegarden will not output any audio by itself, unless you also handle audio data in it (rosegarden has very limited audio editing by itself). 

If you have a hardware MIDI device the sounds of which you like, you can also use it as the MIDI receiver instead of using a software sampler. Rosegarden can handle whatever device (s/w or h/w) that understands MIDI events and produces sound.

---

### Post by Capoeira on 2008-07-14
that internal soundcard instruments doesnt work. u have to use instruments to output the midi.
use for example the ZynAddSubFX (for testing):

a) Midi-output has to be conected to ZynAddSubFX-input ;you can do this or in Jack-ALSA-tab or in Rosegarden-manage midi devices
make sure that the midi-track is conected to the correct chanel on the midi device

b) the ZynAddSubFX-output has to be conected to system-playback OR (go back) to rosegarden in Jack-AUDIO-tab

EDIT: thorgal was faster :-)

---

### Post by DARKAD on 2008-07-14
'that internal soundcard instruments doesnt work' yes that's the matter!

I tried with a synth on ROSEGARDEN and it was possible to hear sound from midi.

I think that the PHONIC firefly 302 has got its internal general midi compatible instruments.

Any suggestion about how to make internal instrument work?

I'm reading from this page ([http://freebob.sourceforge.net/index.php/FAQ](http://freebob.sourceforge.net/index.php/FAQ) ) these things about freebob:

The current driver status:
- MIDI support through ALSA sequencer
- Only 'one device on the bus' case supported

So it means that only if alsa manage to recognize a firewire soundcard, it will play its midi instruments!

Isn't it?

---

### Post by Capoeira on 2008-07-14
my internal instruments never worked - as i have only a cheap soundcard i never tried to get them working

but have a look at this (Page 4): [http://www.eugenecormier.com/pdfs/Tutorial-Rosegarden-and-external-internal-MIDI.pdf](http://www.eugenecormier.com/pdfs/Tutorial-Rosegarden-and-external-internal-MIDI.pdf)
EDIT: Page5: •
If you start Rosegarden with the command:
•
“rosegarden”: it will have only external MIDI enabled
•
“rosegarden+timidity”: it will have both external and internal MIDI enabled

só i think you will have to install timidity and run those 2 together.

as for your ALSA-question: rosegarden uses the alsa-driver

---

