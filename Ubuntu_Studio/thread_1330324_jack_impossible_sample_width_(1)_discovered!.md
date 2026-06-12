---
title: "jack: impossible sample width (1) discovered!"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by gorgon on 2009-11-18
Hello,

Im trying to get my RME Multiface to work with jack in 9.04. Im using qjackctl, and setting it up for playback only works fine but trying to set up jack with capture (inputs) gives the message "impossible sample width (1) discovered!".

theres only one result of this when I google it.. anyone familiar with this?

Here are my settings:
```
realtime= yes
frames/period= 256
sample rate= 44100
periods/buffers= 2
port max= 512
input latency= (default)
dither= none
audio= capture only

```

..though I think I've tried every possible combination of settings now

and the error message:
```
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... -|hw:1,0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x8e0e9a8 fd = -1
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
impossible sample width (1) discovered!
15:58:16.421 JACK was stopped with exit status=1.
```

any thoughts on this is greatly appreciated as I was to have a recording session right now... :icon_frown:

cheers,
g

---

### Post by VertexPusher on 2009-11-18
Are you sure that card #1 is the RME interface? Sometimes the number assignments change between sessions, so hw:1,0 may actually point to something else, e.g. a MIDI interface that doesn't have audio PCMs at all. So the same Jack settings that worked for the previous session may fail for the current one.

Run "aplay -l" or "arecord -l" for a list of playback/recording devices. You'll see that each card has a number and a name. The good thing about the names is that they never change, and they can be used instead of card numbers anywhere. So if you enter "hw:NAME,0" instead of "hw:1,0" in Jack's configuration, any future changes of the card numbers won't affect you any more.

---

### Post by gorgon on 2009-11-18
@VertexPusher
yea, I'm familiar with that and it is set right. Thanks though!

---

