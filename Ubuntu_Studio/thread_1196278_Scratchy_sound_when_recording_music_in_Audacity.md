---
title: "Scratchy sound when recording music in Audacity"
date: 2009-06-24
forum: Ubuntu Studio
---

### Post by sethtriggs on 2009-06-24
On top of this, using certain voices in the ZynAddSubFX synthesizer (such as the Fantasy/Long Space Choir) will cause the scratchiness. This doesn't seem to happen with "sharper" sounds. I am using an M-Audio KeyStudio 49-note keyboard (the included USB sound interface has no effect in Linux apparently).

The scratching almost always happens when recording though—I do suspect that maybe the realtime processing isn't working.

I don't think it's even fully connecting with Jack. Does anyone have a working setup? How did you arrange things to get the music operational without scratch? Right now my Jack control is up, the connection is fine, but the transport apparently does not work. It says:

```
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.
```

In the setup under parameters, I have realtime checked at a priority of 75, but apparently this does not work.

I am hoping there's a different way to make this happen where it won't be scratchy.

This machine has a Soundblaster Audigy sound card. 

Oh, here's my Jack output when I try to get things started:

```

19:49:58.118 JACK is starting...
19:49:58.119 /usr/bin/jackd -R -P75 -dalsa -r44100 -p1024 -n2 -D -Chw:0,2 -Phw:0,3 -Xraw
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210095952, from thread -1210095952] (1: Operation not permitted)
cannot create engine
19:49:58.143 JACK was started with PID=15707.
19:49:58.167 JACK was stopped successfully.
19:49:58.168 Post-shutdown script...
19:49:58.168 killall jackd
jackd: no process killed
19:49:58.577 Post-shutdown script terminated with exit status=256.
19:50:00.235 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

Thanks in advance!

-Seth

---

### Post by kayosiii on 2009-06-25
Keep Jack Control (qjackctl) open and watch the CPU usage as you are working... Chances are your CPU is being maxed out -- Zynaddsubfx is a bit of a pig that way - some patches are worse than others.

Some things you can do.
1) go into Zynaddsubfx's dialog and set it's internal sample rate to match the one you are using to what jack is using. This will cut down a whole bunch of calculations you don't need to be doing.

2) Set up Jack realtime - As it stands giving user applications the ability to run with realtime privileges does have some security implications so you have to give yourself permission to do it - a search on these forums for /etc/security/limits and you will find plenty of good instructions on doing this.

3) Set up a realtime kernel - this is different to and often confused with the above. Currently there isn't a good one in the apt repos for Jaunty or Intrepid. (there is for karmic though). So try this if all else fails...

4) trade some latency for stability .... Up your frames/period setting in jack.

---

### Post by sethtriggs on 2009-06-25
> **kayosiii said:**
> Keep Jack Control (qjackctl) open and watch the CPU usage as you are working... Chances are your CPU is being maxed out -- Zynaddsubfx is a bit of a pig that way - some patches are worse than others.

Some things you can do.
1) go into Zynaddsubfx's dialog and set it's internal sample rate to match the one you are using to what jack is using. This will cut down a whole bunch of calculations you don't need to be doing.

2) Set up Jack realtime - As it stands giving user applications the ability to run with realtime privileges does have some security implications so you have to give yourself permission to do it - a search on these forums for /etc/security/limits and you will find plenty of good instructions on doing this.

3) Set up a realtime kernel - this is different to and often confused with the above. Currently there isn't a good one in the apt repos for Jaunty or Intrepid. (there is for karmic though). So try this if all else fails...

4) trade some latency for stability .... Up your frames/period setting in jack.

Thanks much, I'll give those a try in turn! By the way, do you have a rough idea of the optimal way to connect items in the Jack connection dialog, to make sure that the synthesizer is working through Jack properly?

My items would be the KeyStudio, the Audigy:0 (the soundcard), the Timidity, the Midi-port and the ZynAddSubFX. The Key Studio seems to work without being patched through the sound card; it works with just the KeyStudio connected to ZynAddSubFX.

-Seth

---

### Post by kayosiii on 2009-06-25
First of all install and use patchage...
It is much nicer to set connections up in than Jack Control.

for Zynsubaddfx

you really need two connections
the midi input (green in patchage) to the midi input for Zynaddsubfx.

Make sure that Zynaddsubfx's audio out connections (blue in patchage) are connected to the main outs on your soundcard... (timidity is not used in this chain at all - and Zyn will probably do this second connection by default).

---

### Post by sethtriggs on 2009-06-26
> **kayosiii said:**
> First of all install and use patchage...
It is much nicer to set connections up in than Jack Control.

for Zynsubaddfx

you really need two connections
the midi input (green in patchage) to the midi input for Zynaddsubfx.

Make sure that Zynaddsubfx's audio out connections (blue in patchage) are connected to the main outs on your soundcard... (timidity is not used in this chain at all - and Zyn will probably do this second connection by default).

The second connection is happening, but I am not getting the first to work at all. At least it seems to connect visibly in Jack Control. All the time I try to connect the midi input (well, there is nothing that explicitly says Midi Input) to ZynAddSubFX, it is rejected.

I put in a screenshot of my Patchage panel.

-Seth


Apparently Patchage , if you try to disconnect (I was trying to connect the Midi-through to the Midi-through, since that seemed to actually let me do it, in an attempt to find the path through the puzzle, and the Jack daemon locked up. Yikes.

I also can't start Patchage on its own; I must start Jack first.

---

### Post by kayosiii on 2009-06-26
That's right the version of Patchage in Jaunty needs jack to be started first... ( I should have mentioned that). It only really replaces the connecting stuff.

The connection that should be being made is below and slightly to the right of the Zynaddsubfx midi input...

if this doesn't work I would suggest typing the dmesg into a terminal after trying to connect an see if anything is complaining.

---

### Post by Arcturus691 on 2009-10-13
I was getting the scratchy noise too.  In my case it was caused by the sample rate being set to 44000hz which my sound card does not support.  I changed it to 48000hz which the card does support and all of the sounds are scratch free.  Go to File->Settings and click on the Sample Rate pull down to change.

---

