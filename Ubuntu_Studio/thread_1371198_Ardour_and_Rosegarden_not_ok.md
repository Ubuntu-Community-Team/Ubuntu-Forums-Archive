---
title: "Ardour and Rosegarden not ok"
date: 2010-01-03
forum: Ubuntu Studio
---

### Post by nilsonchagas on 2010-01-03
Hello,

Well, a have the desktop, and I could play MIDI files, so, I installed ubuntustudio, all function.

Now I buy Dell notebook Inspiron 1440 with ubuntu 9.10.

After update, install ubuntustudio, like desktop, but Rosgarden and Ardour (The program my use) not function.

Timidy play the files MIDI.

When run "sudo qjackctl" the jack run ok.

Help me please

---

### Post by raboofje on 2010-01-03
> **nilsonchagas said:**
> Timidy play the files MIDI.

When run "sudo qjackctl" the jack run ok.

I understand your problem is JACK does no longer start as a normal user, but it does start with sudo?

When you start JACK with qjackctl, do you see errors in the 'Messages' window? Perhaps the error documented at [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting) ?

---

### Post by nilsonchagas on 2010-01-03
> **raboofje said:**
> I understand your problem is JACK does no longer start as a normal user, but it does start with sudo?

When you start JACK with qjackctl, do you see errors in the 'Messages' window? Perhaps the error documented at [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting) ?

Well, I run qjackctl with my user its ok.

But I didnt to try run ardour after to open qjackctl, if I run qjackctl before ardour, its ok. 

Rosegarden still wrong. I open qjackctl, open Rosegarden play project, but no sound.

Idea???

---

### Post by raboofje on 2010-01-03
> **nilsonchagas said:**
> Well, I run qjackctl with my user its ok.

But I didnt to try run ardour after to open qjackctl, if I run qjackctl before ardour, its ok.

ok

> Rosegarden still wrong. I open qjackctl, open Rosegarden play project, but no sound. Idea???

Do you get any error messages? Does Rosegarden show up in the 'Connections' window of QJackctl?

---

### Post by nilsonchagas on 2010-01-03
> **raboofje said:**
> ok



Do you get any error messages? Does Rosegarden show up in the 'Connections' window of QJackctl?

No error messages, the Rosegarden show up in the 'Connections'.
When Qjackctl open, the message "Failed to connect to Jack audio server" not show in the Rosegarden.

Messages Qjackctl:
 p, li { white-space: pre-wrap; }  [COLOR=Black][COLOR=#999999]23:37:42.930 Patchbay deactivated.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:43.008 Statistics reset.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:43.115 Startup script...[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#990099]23:37:43.116 artsshell -q terminate[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#66CC99]23:37:43.119 ALSA connection graph change.[/COLOR][/COLOR]
 [COLOR=Black]sh: artsshell: not found[/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:43.765 Startup script terminated with exit status=32512.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:43.765 JACK is starting...[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#990099]23:37:43.765 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR][/COLOR]
 [COLOR=Black]no message buffer overruns[/COLOR]
 [COLOR=Black]jackd 0.116.1[/COLOR]
 [COLOR=Black]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=Black]jackd comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=Black]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=Black]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=Black]JACK compiled with System V SHM support.[/COLOR]
 [COLOR=Black]loading driver ..[/COLOR]
 [COLOR=Black]apparent rate = 44100[/COLOR]
 [COLOR=Black]creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=Black]control device hw:0[/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:43.806 JACK was started with PID=3314.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CCCC99]23:37:43.985 ALSA connection change.[/COLOR][/COLOR]
 [COLOR=Black]configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=Black]ALSA: final selected sample format for capture: 32bit integer little-endian[/COLOR]
 [COLOR=Black]ALSA: use 2 periods for capture[/COLOR]
 [COLOR=Black]ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
 [COLOR=Black]ALSA: use 2 periods for playback[/COLOR]
 [COLOR=Black][COLOR=#999933]23:37:45.996 Server configuration saved to "/home/nilson/.jackdrc".[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:45.998 Statistics reset.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#999999]23:37:46.062 Client activated.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#9999CC]23:37:46.064 JACK connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CC9966]23:37:46.068 JACK connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CC9966]23:37:46.593 JACK connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CC9966]23:37:46.731 JACK connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#9999CC]23:37:46.887 JACK connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#66CC99]23:37:47.352 ALSA connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CCCC99]23:37:47.512 ALSA connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CCCC99]23:37:47.713 ALSA connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CC9966]23:37:49.000 JACK connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#9999CC]23:37:49.171 JACK connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#66CC99]23:37:57.589 ALSA connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CCCC99]23:37:57.788 ALSA connection change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#66CC99]23:37:57.882 ALSA connection graph change.[/COLOR][/COLOR]
 [COLOR=Black][COLOR=#CCCC99]23:37:57.990 ALSA connection change.[/COLOR][/COLOR]

---

### Post by raboofje on 2010-01-04
> **nilsonchagas said:**
> Rosegarden still wrong. I open qjackctl, open Rosegarden play project, but no sound.

What kind of project are you trying to play in Rosegarden? Midi or audio (or both?)

For audio: have you connected rosegarden to your soundcard in the qjackctl 'connections' window?

For midi: have you connected rosegarden to a synth to play the audio?

---

### Post by nilsonchagas on 2010-01-05
> **raboofje said:**
> What kind of project are you trying to play in Rosegarden? Midi or audio (or both?)

For audio: have you connected rosegarden to your soundcard in the qjackctl 'connections' window?

For midi: have you connected rosegarden to a synth to play the audio?

Look the images, Rosegarden show in Audio, but not in midi.

For midi: How connected rosegard to my soundcard???

---

### Post by thorgal on 2010-01-05
look in the ALSA tab. Rosegarden is not using jack-MIDI. 

QjackCtl is confusing for newbies when it comes to the MIDI connectivity. Unless you start jackd with the "-X seq" option, you will have nothing in the MIDI tab. For convenience Rui included the ALSA MIDI layer as well in qjackctl, in the absence of jack-midi. So when you connect things in the ALSA tab, you actually are not using jack ;)

By the way, rosegarden has some auto-connection capability (not always optimal but that's another story). So chances are your MIDI controller is already connected to rosegarden. You can always check inside rosegarden what MIDI devices it detected (little menu icon in main menu bar that looks like a PCI card with a tiny keyboard on top). You will see a window popping up with a list of devices (software and hardware, writable and readable, etc).

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> look in the ALSA tab. Rosegarden is not using jack-MIDI. 

QjackCtl is confusing for newbies when it comes to the MIDI connectivity. Unless you start jackd with the "-X seq" option, you will have nothing in the MIDI tab. For convenience Rui included the ALSA MIDI layer as well in qjackctl, in the absence of jack-midi. So when you connect things in the ALSA tab, you actually are not using jack ;)

By the way, rosegarden has some auto-connection capability (not always optimal but that's another story). So chances are your MIDI controller is already connected to rosegarden. You can always check inside rosegarden what MIDI devices it detected (little menu icon in main menu bar that looks like a PCI card with a tiny keyboard on top). You will see a window popping up with a list of devices (software and hardware, writable and readable, etc).

When you say audio and midi, I understood that was the midi file type. 

I'm not using devices, I just want to edit the notation, hear what I'm Editant and export to a midi file.

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> look in the ALSA tab. Rosegarden is not using jack-MIDI. 

QjackCtl is confusing for newbies when it comes to the MIDI connectivity. Unless you start jackd with the "-X seq" option, you will have nothing in the MIDI tab. For convenience Rui included the ALSA MIDI layer as well in qjackctl, in the absence of jack-midi. So when you connect things in the ALSA tab, you actually are not using jack ;)

By the way, rosegarden has some auto-connection capability (not always optimal but that's another story). So chances are your MIDI controller is already connected to rosegarden. You can always check inside rosegarden what MIDI devices it detected (little menu icon in main menu bar that looks like a PCI card with a tiny keyboard on top). You will see a window popping up with a list of devices (software and hardware, writable and readable, etc).

Look Alsa tab.

---

### Post by thorgal on 2010-01-05
OK, so you want your rosegarden MIDI tracks to produce sound.

For that, you will need to connect a soft synth to your tracks. Either you open a soft synth internally in rosegarden, or you fire up an external soft synth (zynaddsubfx, qsynth, etc) and connect them to rosegarden. Only then will you be able to hear some sound triggered by the rosegarden tracks during active transport.

In case you choose external soft synths, make sure they are jack compatible on the audio side, otherwise, no sound ;)

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> OK, so you want your rosegarden MIDI tracks to produce sound.

For that, you will need to connect a soft synth to your tracks. Either you open a soft synth internally in rosegarden, or you fire up an external soft synth (zynaddsubfx, qsynth, etc) and connect them to rosegarden. Only then will you be able to hear some sound triggered by the rosegarden tracks during active transport.

In case you choose external soft synths, make sure they are jack compatible on the audio side, otherwise, no sound ;)

Can you to explain, how open soft synth internally in rosegarden???

I did to try, open jack, in terminal typed  timidity -iA -Oj -B2,8, and open Rosegarden, and thats ok.

But not easy. rsrsrsrsrsrs

---

### Post by thorgal on 2010-01-05
> **nilsonchagas said:**
> Can you to explain, how open soft synth internally in rosegarden???

synth plugins :) rosegarden can use plugins (DSSI technology). If you have some installed, then rosegarden can use them internally.

Just what I said but better : [http://www.rosegardenmusic.com/tour/synths/](http://www.rosegardenmusic.com/tour/synths/)

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> synth plugins :) rosegarden can use plugins (DSSI technology). If you have some installed, then rosegarden can use them internally.

Just what I said but better : [http://www.rosegardenmusic.com/tour/synths/](http://www.rosegardenmusic.com/tour/synths/)


It is a problem, my synth plugins is empty, and I cant to get.

---

### Post by thorgal on 2010-01-05
open synaptic (package manager) and make a search on dssi.

(From a terminal equivalent, this is what I get:

```

~$ apt-cache search dssi
dssi-dev - Header file for compiling DSSI plugins and hosts
dssi-example-plugins - Example DSSI plugins
dssi-host-jack - An example DSSI host
dssi-utils - Command-line utilities for sending commands to DSSI plugins
fluidsynth-dssi - DSSI wrapper for the FluidSynth SoundFont-playing software synthesizer
hexter - Yamaha DX7 modeling DSSI plugin
ll-scope - an oscilloscope DSSI plugin
nekobee - Simple single-oscillator DSSI plugin
sineshaper - Monophonic synth plugin with two oscillators and waveshapers
whysynth - DSSI Soft Synth Interface
wsynth-dssi - hack on Xsynth-DSSI to allow wavetable synthesis
xsynth-dssi - classic-analog (VCOs-VCF-VCA) style software synthesizer

```

install the synth plugins via synaptic, restart rosegarden. See what you get :)

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> open synaptic (package manager) and make a search on dssi.

(From a terminal equivalent, this is what I get:

```

~$ apt-cache search dssi
dssi-dev - Header file for compiling DSSI plugins and hosts
dssi-example-plugins - Example DSSI plugins
dssi-host-jack - An example DSSI host
dssi-utils - Command-line utilities for sending commands to DSSI plugins
fluidsynth-dssi - DSSI wrapper for the FluidSynth SoundFont-playing software synthesizer
hexter - Yamaha DX7 modeling DSSI plugin
ll-scope - an oscilloscope DSSI plugin
nekobee - Simple single-oscillator DSSI plugin
sineshaper - Monophonic synth plugin with two oscillators and waveshapers
whysynth - DSSI Soft Synth Interface
wsynth-dssi - hack on Xsynth-DSSI to allow wavetable synthesis
xsynth-dssi - classic-analog (VCOs-VCF-VCA) style software synthesizer

```install the synth plugins via synaptic, restart rosegarden. See what you get :)


I think is installed, look:
```

nilson@nilson-laptop:~$ apt-cache search dssi
dssi-dev - Header file for compiling DSSI plugins and hosts
dssi-example-plugins - Example DSSI plugins
dssi-host-jack - An example DSSI host
dssi-utils - Command-line utilities for sending commands to DSSI plugins
fluidsynth-dssi - DSSI wrapper for the FluidSynth SoundFont-playing software synthesizer
hexter - Yamaha DX7 modeling DSSI plugin
ll-scope - an oscilloscope DSSI plugin
nekobee - Simple single-oscillator DSSI plugin
sineshaper - Monophonic synth plugin with two oscillators and waveshapers
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
whysynth - DSSI Soft Synth Interface
wsynth-dssi - hack on Xsynth-DSSI to allow wavetable synthesis
xsynth-dssi - classic-analog (VCOs-VCF-VCA) style software synthesizer
dssi-vst - Steinberg VST compability layer for DSSI

```

---

### Post by thorgal on 2010-01-05
the command "apt-cache search something" does not tell you whether the packages are installed, but whether some packages are matching your search string. Your package database does not only contain info about installed packages but also all others. The idea of this command is to look up potential packages that have something to do with the search string. In this case (search on dssi), you see that you can install a bunch of dssi soft synth since the search find some matchings.

---

### Post by nilsonchagas on 2010-01-05
> **thorgal said:**
> the command "apt-cache search something" does not tell you whether the packages are installed, but whether some packages are matching your search string. Your package database does not only contain info about installed packages but also all others. The idea of this command is to look up potential packages that have something to do with the search string. In this case (search on dssi), you see that you can install a bunch of dssi soft synth since the search find some matchings.

Sorry, now understood.

The plugins show, but nothing the sound.

But if I type "timidity -iA -Oj -B2,8" the sound ok.

I dont know how onfigure jack and the soft syth to run together.

---

### Post by thorgal on 2010-01-06
works fine from my DAW:

opened rosegarden, created a dummy track, connected to dssi organ plugin (from the Calf plugin suite), edited a track segment with random notes, played back through jack and heard stuff. No problem.
Don't know why you need timidity.

I am using rosegarden 10.02 svn (not 1.7.3)

---

### Post by nilsonchagas on 2010-01-06
> **thorgal said:**
> works fine from my DAW:

opened rosegarden, created a dummy track, connected to dssi organ plugin (from the Calf plugin suite), edited a track segment with random notes, played back through jack and heard stuff. No problem.
Don't know why you need timidity.

I am using rosegarden 10.02 svn (not 1.7.3)

Well, with Calf organ plugin not sound, but the Calf Monosyth DSSI is OK.

My project I has do in desktop use General Midi device, Intrument Eletric Piano e Violin.

In my laptop, General Midi device play sound only type timidy in terminal.

If I tried another plugins, a noise play, I need stop the jack.

---

### Post by raboofje on 2010-01-06
> **thorgal said:**
> QjackCtl is confusing for newbies when it comes to the MIDI connectivity.

[http://sourceforge.net/tracker/?func=detail&aid=2906105&group_id=86211&atid=578829](http://sourceforge.net/tracker/?func=detail&aid=2906105&group_id=86211&atid=578829) :)

---

