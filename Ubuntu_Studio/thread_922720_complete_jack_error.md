---
title: "complete jack error"
date: 2008-09-17
forum: Ubuntu Studio
---

### Post by bodysnatcher on 2008-09-17
my system tells me that i have JACK installed.
when i switch to the JACK driver on Hydrogen, i get the following message:

"error starting audio driver".

if i use the basic driver on my Hydrogen, or my Ardour GTK2, all i get is crumpled loggy messy shattered playback broken into bits.. if you know what i mean.

i'm on hardy heron.


please help meh?



(edit: i just reinstalled JACK from the synaptic manager. it has made no difference.)



Matt

---

### Post by Stochastic on 2008-09-17
Jack needs to be started manually (or configured to start up on boot if you're really skilled with things) before you start jack-dependent apps.  You should also uncheck the option in Hydrogen's preferences to "auto-connect" and go into qjackctl's patchbay to connect Hydrogen.

You may want to take a read through the community docs for UbuntuStudio: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

