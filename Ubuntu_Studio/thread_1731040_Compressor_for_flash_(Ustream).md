---
title: "Compressor for flash (Ustream)"
date: 2011-04-16
forum: Ubuntu Studio
---

### Post by FlyFire on 2011-04-16
Im quite new to Ubuntu Studio, but as far as i've read, it should be able to do what i want it to do.

What I'm looking for, is to capture sound from the soundcard, compress volume and then send it to Ustream. I've looked around a bit in JACK and the JACK patchbay and connections, but I have not understood how to connect the capture to flash, and between them put the compressor from JACK Rack.

Any suggestions? Other methods?

---

### Post by Pablo_F on 2011-04-17
You could download the video (or even without downloading it could be somewhere in /tmp) and play it through a jack audio aware video player such as "mplayer -ao jack" or vlc with the jack output plugin, etc.

You can also "jackify" the flash player but note that, if you do it, flash will only work if jack is up and running. Here you can find how:

[http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323](http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323)

---

### Post by FlyFire on 2011-04-17
I think you misunderstood me. I'm not gonna watch youtube or anything like that. I want to stream radio over Ustream, and compress the sound. But maybe thats possible as well with that flashplugin?

---

### Post by Pablo_F on 2011-04-17
Yes, I misunderstood you, sorry. I have never tried sending audio over ustream and I don't know if it works with jack. 

Neither do I know if there is a simple ladspa host similar to jack-rack that works directly with pulseaudio. 

Maybe use the pulseaudio-module-jack and connect jack-rack outputs to pulseaudio source ports? 

(assuming that ustream works with pulseaudio which I don't know either).

---

### Post by FlyFire on 2011-04-17
Probably not. I'll simply have to put a computer running JACK, and compress the captured audio, send it to the line-out and connect that lineout to the linein on the stream computer.

Thank you anyways! :)

---

### Post by Pablo_F on 2011-04-18
Ahm, so it is easier than I thought!

When you start jack, you will see a client called "system". This is the audio hardware jack is using. The capture ports on the left column in Jack Control's connections represent the audio card's inputs and the playback ports, the outputs. 

So you have to make the physical connections and then the virtual jack connections from system captures to jack-rack inputs and from jack-rack outputs to system playbacks.

Normally, the interface (default) should be enough but depending on your audio card, it could be more than one "device" in it which can have only capture ports, only playback ports or duplex ports. The command:

arecord -l && aplay -l

will tell you, so you can set up jack correctly. 

Also, take a look (and tweak if needed) the internal mixer of the card by means of alsamixer (rather than Sound Preferences, which is a pulseaudio frontend). 

Cheers! Pablo

---

### Post by rusk911 on 2011-04-21
I have captured flash from pulse-jack. But this way you will compress all Ubuntu sounds including skype, system sounds etc..

---

