---
title: "Jack 2, Ardour and Multiple Sound Cards"
date: 2010-02-12
forum: Ubuntu Studio
---

### Post by Nuyen on 2010-02-12
Hey everyone.
I've been on an extensive search all day now, through the bowels of google and various forums.  Like many, I'm a Windows convert and musician, trying to get up and running in Ubuntu Studio (Karmic).

However, I've hit a pretty significant snag:
I've got an M-Audio Audiophile 2496 that I want to use to record in Ardour, whilst monitoring through my on board card.

I've installed Jack2, but can still only achieve either listening or recording in Ardour, not both.  I'm thinking this has come down to my ignorance of the Terminal and not knowing how to specify which audio device  does what.

Gracias for any help.

---

### Post by RaumTrug on 2010-02-13
it's a bit hidden and little documented, but to use multiple devices with jack, you need to load the second device (and I suggest to use the recording device as primary, and the monitoring device as secondary, as with additional devices the sound quality isn't 100% pure) with either "alsa_in / alsa_out" or "jack_load audioadapter ... " into jack. I've not used ardour yet, so someone else could probably assist with infos on how to create monitoring output ports from ardour, for example.

anyway, you've installed jack2 so I guess you've got alsa_in and alsa_out around (the standard jack version installed in ubuntu doesn't, what a shame!). how those work is described here: [http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut](http://trac.jackaudio.org/wiki/WalkThrough/User/AlsaInOut)

you fire up the jack server, start it, and then open a terminal and issue your alsa_out command with correct parameters there. the soundcard ports should appear in qjackcontrol then. to monitor the input from the other soundcard directly, just connect those inputs with the alsa_out outputs; with fx from ardour directly I can't help (see above), I guess you just connect the arodour outs to the additionally loaded with alsa_out.

the audioadapter is something else I've used with success to monitor an usb mic on a soundcard; it is basically a combo of alsa_in and alsa_out, you can see a little about it here: [http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack2](http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack2); see point 6. for basic usage - the plugin is from the looks of its sourcecode not really finished & foolproof yet, but I got it to work neatly at times. you'll get some xtra latency with those tools, though.

---

