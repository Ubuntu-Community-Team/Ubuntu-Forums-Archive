---
title: "Simple software for MIDI keyboard?"
date: 2011-05-14
forum: Ubuntu Studio
---

### Post by edea on 2011-05-14
I have an old MIDI keyboard, and I just wanted to check if it still works. Back in the day it worked with Midisoft Studio for Windows, you played a key on the keyboard and the note appeared on the stave in the program:

[IMG]http://physics.uwb.edu.pl/ptf/echa/w_siwak/audiosfera/technol/Studio42.jpg[/IMG]

Is there anything similar for Ubuntu? Something easy to set up and easy to use.
Thanks.

---

### Post by sgx on 2011-05-14
Hi, you can test midi i/o by installing phasex synth,
and qjackctl connections gui. Start qjackctl, then phasex,
(which has a smaller gui available in its view menu, called netbook)
Press the connect button on qjackctl lower left.

In the 3-tab panel that opens, click the alsa tab, then on the right half of the window that opens, select your midi device, on the left half, select phasex, then press this panels 'connect' button, and play your keyboard.

In the audio tab of the connections panel, you should see phasex-01
connected to system (your soundcard i/o )
Cheers

---

### Post by Pablo_F on 2011-05-14
To see if it is recognised by alsa, look at the terminal output of:

arecordmidi -l

For a notation software, I suggest musescore. 

Cheers, Pablo

---

### Post by edea on 2011-06-08
First, thanks for the answers.
My keyboard (Goldstar GMK-49) came with a MIDI port connector, but I don't have a MIDI port on my PC, so I bought a MIDI to USB cable and it just arrived.
I tried the keyboard and the USB cable under Windows and everything works.

But I can't make it work in Ubuntu 10.10... :(
I can hear MIDI files when played with Totem for example (I couldn't before, but after installing the "bad" plugins, I can now), but I can't hear the keyboard.

Here is what I do:

-I open ZynAddSubFX
-Then I open JACK Audio Connection Kit
-Under "ALSA" tab, I connect the USB MIDI Interface with ZynAddSubFX
-Apparently it works, because every time I press a key on the keyboard, a blue line (circled in red in the image attached) appears.
-But I can't hear a sound!
-Under sound preferences, it says that no application is playing or recording sound.

Where is the problem?

Here is the log of JACK:

```
00:05:34.984 Patchbay desactivada.
00:05:35.043 Reiniciar estadísticas.
00:05:35.142 Script de inicio...
00:05:35.143 artsshell -q terminate
00:05:35.152 Cambió el gráfico de conexiones ALSA.
sh: artsshell: not found
00:05:35.599 El script de inicio finalizó con estado 32512.
00:05:35.600 JACK está iniciándose...
00:05:35.600 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2
00:05:35.608 JACK se inició con PID=3767.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
00:05:35.804 Cambios en las conexiones ALSA.
00:05:37.817 Reiniciar estadísticas.
00:05:37.818 Cliente activado.
00:05:37.820 Cambios en las conexiones JACK.
00:05:37.826 Cambió el gráfico de conexiones de JACK.
00:05:37.897 XRUN callback (1).
00:05:39.828 XRUN callback (19 omitidos).
00:05:41.833 XRUN callback (19 omitidos).
00:05:44.041 XRUN callback (21 omitidos).
00:05:44.978 Cambios en las conexiones ALSA.
00:05:46.045 XRUN callback (19 omitidos).
00:05:48.049 XRUN callback (19 omitidos).
00:05:50.054 XRUN callback (19 omitidos).
00:05:52.059 XRUN callback (19 omitidos).
00:05:54.062 XRUN callback (19 omitidos).
00:05:56.066 XRUN callback (19 omitidos). (and many more messages like these)
```


```
~$ arecordmidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 24:0    USB MIDI Interface               USB MIDI Interface  MIDI 1

```

---

### Post by Pablo_F on 2011-06-08
First of all, you need to set up jack properly. You have tons of xruns. Not surprisingly as you are running jack in non realtime mode. Enable realtime mode. 

Note that you need to give your user realtime and memlock privileges. You do so by running this command

sudo dpkg-reconfigure -p high jackd  (or probably, jackd1)

Choose YES (use TAB key). Then use this command:

sudo adduser your_user_name audio

Reboot the computer and start jack in realtime mode.

Now, you don't need the sound preferences as that is a pulseaudio front-end. Pulseaudio is the default audio server, but you are using jack, which is another audio server. So don't bother with sound preferences.

You need to check that the soft synth audio output is connected to the system playbacks, which represent the output ports of the card that jack is using. Needless to say, make sure that jack is using the right audio card (interface field in qjackctl's setup).

Start jack before anything else. If zynaddsubfx throws many xruns, try yoshimi. But then you need a2jmidid, because yoshimi does jack MIDI instead of alsa MIDI. You can also use qsynth to play soundfonts. Whatever, be patient.

Cheers, Pablo

---

### Post by edea on 2011-06-08
Acabo de ver que eres de 800 km al norte :D
Muchas gracias, ya lo pruebo todo "mañana". 

I found a "solution" [here]("http://www.khattam.info/solved-cant-open-devdsp-in-ubuntu-10-10-maverick-meerkat-2010-06-09.html#disqus_thread"), consisting on executing ZynaddsubFX like this:

```
:~$ padsp zynaddsubfx
```
Which opens Zyn... with OSS emulation. Now I can hear the sounds but with a very poor quality, with too much noise.
So I'll try Pablo's instructions tomorrow, que ahora me voy al catre.

EDIT: The method above wasn't crappy, the problem seemed to be the realtime mode. After enabling it, like Pablo said, it works properly, with good quality sound, but only with the "**padsp** zynaddsubfx" command.
I still can't make it sound if I open Zynaddsubfx normally...

---

### Post by Pablo_F on 2011-06-09
Hola!

Try yoshimi. Or qsynth... Time to learn.

Cheers, Pablo

---

### Post by prokoudine on 2011-06-11
> **edea said:**
> 
Here is what I do:

-I open ZynAddSubFX
-Then I open JACK Audio Connection Kit
-Under "ALSA" tab, I connect the USB MIDI Interface with ZynAddSubFX
-Apparently it works, because every time I press a key on the keyboard, a blue line (circled in red in the image attached) appears.
-But I can't hear a sound!
-Under sound preferences, it says that no application is playing or recording sound.

Did you connect audio outputs of ZynAddSubFX to audio output? Otherwise MIDI will go into the synth, but the sound will never reach ya :)

---

