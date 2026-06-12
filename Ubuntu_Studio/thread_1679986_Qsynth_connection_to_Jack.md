---
title: "Qsynth connection to Jack"
date: 2011-02-01
forum: Ubuntu Studio
---

### Post by piovezan on 2011-02-01
Hi all,

After a previous [Jack startup]("http://art.ubuntuforums.org/showthread.php?t=1679365") issue having been solved, I'm now trying to make Fluidsynth (Qsynth) work. The Qsynth MIDI Driver is being set to alsa_seq and the Audio Driver to jack, however Jack Control reports something when I start Qsynth. What could be possibly  happening?


[COLOR=#999999]22:33:20.856 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:33:20.904 Statistics reset.[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]22:33:20.919 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]22:33:21.114 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:33:22.018 Startup script...[/COLOR]
 [COLOR=#990099]22:33:22.018 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]22:33:22.419 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:33:22.419 JACK is starting...[/COLOR]
 [COLOR=#990099]22:33:22.419 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p1024 -n2 -P[/COLOR]
 [COLOR=#999999]22:33:22.421 JACK was started with PID=2743.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|-|1024|2|48000|0|0|nomon|swmeter|-|32bit
 Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfe978000 irq 44
 configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]22:33:24.563 Server configuration saved to "/home/piovezan/.jackdrc".[/COLOR]
 [COLOR=#999999]22:33:24.564 Statistics reset.[/COLOR]
 [COLOR=#999999]22:33:24.585 Client activated.[/COLOR]
 [COLOR=#9999cc]22:33:24.586 JACK connection change.[/COLOR]
 [COLOR=#cc9966]22:33:24.611 JACK connection graph change.[/COLOR]
 [COLOR=#cc9966]22:33:31.751 JACK connection graph change.[/COLOR]
 [COLOR=#66cc99]22:33:31.780 ALSA connection graph change.[/COLOR]
 [COLOR=#9999cc]22:33:31.815 JACK connection change.[/COLOR]
 [COLOR=#cccc99]22:33:31.816 ALSA connection change.[/COLOR]
 [COLOR=#cc9966]22:33:31.817 JACK connection graph change.[/COLOR]
 [COLOR=#cc66cc]22:33:31.823 XRUN callback (1).[/COLOR]
 JackEngine::XRun: client = qsynth was not run: state = 2
 JackAudioDriver::ProcessAsync Process error
 JackPosixMutex::Unlock res = 1


Please let me know if further info is needed.

Thanks!

---

### Post by piovezan on 2011-02-01
Well, strangely enough the issue is gone in my system. I tried various things, including removing pulseaudio-module-jack and physically reconnecting the MIDI cable, either of which seems to have done the trick.[FONT=monospace]
[/FONT]

---

### Post by AutoStatic on 2011-02-02
Well, Qsynth can be quite a bit unstable. Try the FluidSynth DSSI plugin, works a lot more stable. You can run it standalone: **jack-dssi-host fluidsynth-dssi.so**

Best,

Jeremy

---

### Post by piovezan on 2011-02-02
That's cool, thanks. However the GUI won't show up, any idea why? This is the log. Google found me some possibilities but I don't think any of them is my case.


jack-dssi-host: Warning: DSSI path not set
jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/piovezan/.dssi"

Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|-|512|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfe978000 irq 44
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

jack-dssi-host: OSC URL is:
osc.udp://ubuntu:18912/dssi/fluidsynth-dssi/FluidSynth-DSSI/chan00

host: Ready
fsd-gui starting (pid 2368)...
JackEngine::XRun: client = FluidSynth DSSI plugin was not run: state = 2
JackAudioDriver::ProcessAsync Process error
JackActivationCount::Signal value = 0 ref = 2
JackActivationCount::Signal value = 0 ref = 2

---

### Post by AutoStatic on 2011-02-03
> **piovezan said:**
> ```
JackEngine::XRun: client = FluidSynth DSSI plugin was not run: state = 2
```The GUI probably didn't start because of an xrun. And I now see Qsynth had the exact same issue. Try running JACK with the -S option (so set Server path to */usr/bin/jackd -S* in the QjackCtl setup window).

---

### Post by piovezan on 2011-02-04
I'm confused about this -S option. According to [HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration") it makes JACK run in synchronous mode, which causes less xruns. According to the jackd manual page (man jackd) it is an ALSA driver-specific option which is equivalent to --shorts and tries to configure card for 16-bit samples first, only trying 32-bits if unsuccessful (default is to prefer 32-bit samples). Still according to the manual there is a -s option (lowercase) which means soft mode and ignores xruns reported by the ALSA driver (not the same thing as synchronous mode, from what I've read somewhere). Is the manual outdated?

By the way the GUI still won't show up :( Qsynth on the other hand seems quite stable in my system.

---

### Post by Pablo_F on 2011-02-04
According to the jackd manual page, -S (force 16 bits) is an option for the alsa backend. However, as a general option and only for jackd2, it is equivalent to --sync (synchronous mode). 

The same happens with other letters. For example, -P means priority as a general option, but means "playback only" for the alsa backend.

Admittedly, it is a bit confusing that the default behaviour of jackd2 is asynchronous mode, while jackd1 is only synchronous. Moreover because sync mode seems to perform better in jackd2.

---

### Post by AutoStatic on 2011-02-04
> **piovezan said:**
> Is the manual outdated?No. -S is both an option for jackd directly (Synchronous) and for the alsa backend. You can even set them both:
```
jackd -S -dalsa -S
```

> **piovezan said:**
> By the way the GUI still won't show up :( Qsynth on the other hand seems quite stable in my system.That's weird, but if Qsynth works just use that one :)

---

### Post by piovezan on 2011-02-04
> **AutoStatic said:**
> No. -S is both an option for jackd directly (Synchronous) and for the alsa backend. You can even set them both:
```
jackd -S -dalsa -S
```

So actually the man page *IS* outdated in a sense, right? I mean, I can't find an entry for -S in the general option list, only in the alsa option list, at least for jackd2 v1.9.6. Perhaps I've got the wrong manual installed after moving to and from jackd1? Or perhaps the synchronous option has been left undocumented intentionally by the developers (for 'beta testing' or something)? Anyway thank you both AutoStatic and Pablo_F for clarifying how it works, it was a very clear explanation.

> **AutoStatic said:**
> That's weird, but if Qsynth works just use that one :)

Yeah guess I'll have to stick to it :D but I'll keep your FluidSynth DSSI recommendation in mind ;)

Thanks again!

---

