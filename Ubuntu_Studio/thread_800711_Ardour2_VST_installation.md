---
title: "Ardour2 VST installation"
date: 2008-05-20
forum: Ubuntu Studio
---

### Post by drumanart on 2008-05-20
Hello folks.
I use **(UBUNTU 7.10 GUTSY)** and I started to edit an audio recording.
How can I put reverb (or any other effect) to an audio track in Ardour.
Do I need to install Ardour from scratch and remove the allready existing version, or is there a way to just put the VST plugins to an existing installation?
Thks

---

### Post by Stochastic on 2008-05-20
The Audacity team have built a [VST Enabler]("http://audacityteam.org/vst/") that can be used in ardour if you follow instructions in the [discussion at ardour forums]("http://ardour.org/node/816") on the topic.  Then your vst plugins can be used as if they were ladspa plugins, but be warned some random crashes may occur as a result of the use of this plugin.

Edit: I just noticed you also asked about how to put effects in general into an ardour recording.  First step is to install the LADSPA set with ```
sudo apt-get install ubuntustudio-audio-plugins
``` then take a read through the Plugins section here: [http://www.out-of-order.ca/tutorials/ardour/#plugins](http://www.out-of-order.ca/tutorials/ardour/#plugins)

---

### Post by drumanart on 2008-05-20
Fantastic, thks a lot, I got wat I needed.
saludos

---

