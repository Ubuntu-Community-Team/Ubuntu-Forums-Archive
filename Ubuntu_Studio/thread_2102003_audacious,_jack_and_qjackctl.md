---
title: "audacious, jack and qjackctl"
date: 2013-01-06
forum: Ubuntu Studio
---

### Post by ceverett on 2013-01-06
I use audacious to play music at my parties.  Recently my EMU 0404 died, so I am trying to switch over to an Echo Audiofire 2 I have sitting around.

The configuration I am trying to achieve is 

Audacious --> Jamin --> Audiofire channels 1 and 2

I wasn't using Jamin before, but having a multiband compressor and a limiter would help me a lot.  Also, I'd like to use the headphone output to preselect tracks, so I need to just use 2 channels on the Audiofire for Audacious.

I actually have this configuration working, using the audacious jack output plugin.  My issue is that on every song change, audacious disconnects from Jamin.  Then depending on how I set the port_connection_mode parameter in the audacious config file to, it connects promiscuously to all the physical output ports (CONNECT_ALL, the default), or just 2 ports (CONNECT_OUTPUT), or none at all (CONNECT_NONE).

I understand that the qjackctl patchbay widget is supposed to make connections persistent, but for some reason when audacious starts a new track, it does not reconnect audacious to Jamin as I would expect.

What am I doing wrong here?

---

### Post by CrocoDuck on 2013-01-06
Hi. So sorry, but the only suggestion I can make is to have a look at Mixxx, probably the most comfortable program to use with jack at parties\\:D/. [http://mixxx.org/](http://mixxx.org/)

---

