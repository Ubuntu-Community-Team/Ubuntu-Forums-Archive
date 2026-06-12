---
title: "I've made this Python script to make this Conky theme Plug-n-Play. What do you think?"
date: 2012-05-19
forum: The Cafe
---

### Post by pkkid on 2012-05-19
I put a lot of work into it, and I really hope to make it something super easy to install and setup. In short, it's a Python script you can run to detect your hardware setup auto-create a conkyrc file with the theme shown in the attached screenshot. Some highlights are:

SCREENSHOT: [http://imgur.com/1IrIn](http://imgur.com/1IrIn)
CODE & INSTALL: [https://bitbucket.org/mjs7231/conky-pkmeter](https://bitbucket.org/mjs7231/conky-pkmeter)

SYSTEM / MEMORY / PROCESSES / NVIDIA / NETWORK
* Auto detect number of CPUs and how many are have temp sensors.
* Easy configuration of what drives to display checks weather hddtemp will work on them.
* NVidia display will only show if you have NVidia (I don't have an ATI card, but I would like to add some ATI things in there too).
* Auto detects network devices.
* Easily add, remove, or reorder items.

WEATHER UNDERGROUND
Just plug in your Weather Underground APIKey and it will use autoip to locate you and display the temp.  You can easily set your location if it chooses incorrectly for some reason.  You can also add or remove the Astronomy section to your liking.

NOW PLAYING
This is probably the coolest meter on there right now.  It will detect if music is playing many of the popular music players, extract the song information, download album art form LastFM, and display it all.  It currently works with: Spotify, Rhythmbox, Banshee, Audacious, Clementine, MPD, MOC.  No need to configure what player you use, it'll check whats running and go.

Contribute:  So far it's been pretty much only me working on this. But I would enjoy a minor bit of help for things I can't do, like ATI card display, etc.

---

### Post by Bandit on 2012-05-19
Looks pretty good. Havent had a chance to run it but looks very promising. Good job.

---

