---
title: "EMU 1212m nearly working"
date: 2009-01-12
forum: Ubuntu Studio
---

### Post by dontiego on 2009-01-12
Hi!

I'm trying to make my EMU 1212m work on ubuntu studio 8.04.

I followed this stuff: [http://ubuntuforums.org/showthread.php?t=715755](http://ubuntuforums.org/showthread.php?t=715755)
and ran into several problems.

1. 
```
gauthier@ubuntu:~$ asoundconf list
Names of available sound cards:
Intel
EMU1010
gauthier@ubuntu:~$ asoundconf set-default-card EMU1010
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 429, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 354, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack
gauthier@ubuntu:~$ 

```
Setting the default card does not seem to work (I have an embedded soundcard on my motherboard. This one plays music).
I don't know how to switch to EMU1010!

2. alsamixer gives me the following display:
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: E-mu 1010 [4001]                                                       &#9474;
&#9474; Chip: SB Audigy                                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-3.20]                                                 &#9474;
&#9474;

```
It seems to display IOs for both the EMU1010 and the Intel embedded soundcard. I'm not sure about that "Card" and "Chip" stuff... an SB chip on an EMU card??


3.
JACK has worked once, but now when I fire it up I get the following:
```
22:29:35.336 Patchbay deactivated.
22:29:35.445 Statistics reset.
22:29:35.499 ALSA connection graph change.
22:29:35.672 ALSA connection change.
22:29:37.044 Startup script...
22:29:37.044 artsshell -q terminate
22:29:37.613 Startup script terminated with exit status=256.
22:29:37.613 JACK is starting...
22:29:37.614 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
22:29:37.616 JACK was started with PID=6103.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM hw:0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
22:29:37.636 JACK was stopped successfully.
22:29:37.637 Post-shutdown script...
22:29:37.637 killall jackd
jackd: no process killed
22:29:38.061 Post-shutdown script terminated with exit status=256.
```

Is this ringing any bell to anyone?

Thanks in advance!

---

### Post by dontiego on 2009-01-14
1. For the record, about the asoundconf problem.

It was a bug and seemd to have been corrected. 
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/271899](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/271899)

The thing is that I have alsa-utils that is newer than the bug fix (If I didn't screw up installing it).

I solved this issue by editing /usr/bin/asoundconf by hand, according to [http://launchpadlibrarian.net/17736911/asoundconf.diff](http://launchpadlibrarian.net/17736911/asoundconf.diff)


2. not an issue


3. i got jack running without errors or XRuns, but without sound either.
I had to test nearly all compbinations of input / output devices. 
So, still no sound into rosegarden :(

---

### Post by Jormeliini on 2009-01-15
> **dontiego said:**
> 
3. i got jack running without errors or XRuns, but without sound either.
I had to test nearly all compbinations of input / output devices. 
So, still no sound into rosegarden :(

Did you get sound out of Rosegarden? How about getting sound into other software i.e. Ardour? If yes to either there's probably a simple problem with Alsamixer or JACK settings.

I can't help more. Sorry.

---

### Post by dontiego on 2009-01-17
Hey thanks for the reply.

Now I don't have sound at all anymore. It seems I'm a victim of the asoundconf complexity again. I'll post my issue in another post, just now I'm getting crazy :confused:

---

### Post by dontiego on 2009-02-07
Alright!
Sound in, sound out, Rosegarden seems to be working!

I'm not sure how to setup all these DSP 0 to F in alsamixer, I supposed these were like internal channels, but they work in a weird way in that case.

I have in playback:
0202 DAC Left as DSP 0
0202 DAC Right as DSP 1
All other inputs as Silence.

In Capture:
DSP 0 as 0202 ADC Left
DSP 1 as 0202 ADC Right

I expected the sound to get in the soundcard, to internal channel DSP 0 and 1, then directly to the DAC left and right, but it didn't work.

What did work (clipping, however) was to set DSP 10 and 11 to 0202 ADC Left and Right in capture.

I guess it could be that some application is using these DSP10 and 11, but how could I know who's doing what?

---

