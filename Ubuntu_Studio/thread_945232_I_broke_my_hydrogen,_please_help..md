---
title: "I broke my hydrogen, please help."
date: 2008-10-12
forum: Ubuntu Studio
---

### Post by cino on 2008-10-12
I have been fiddling with quite a lot of software lately, and can't seem to load hydrogen. 

james@james-desktop:~$ hydrogen:
**************************************************************************
lash_init: Not attempting to start daemon server automatically
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_AU.UTF-8
Warning: error loading locale: /usr/share/hydrogen/data/i18n/hydrogen.en_AU.UTF-8.qm

Hydrogen 0.9.3 [Jan  6 2008]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (LASH) (Jack) (Alsa) (OSS) (LRDF)

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[WARNING]   SongReader   	[readSong] Trying to load a song created with a different version of hydrogen.
[WARNING]   SongReader   	[readSong] Song [/usr/share/hydrogen/data/demo_songs/GM_kit_Jazzy.h2song] saved with version 0.9.0
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
[LadspaFX::getLadspaFXGroup]
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
[ERROR]     AlsaMidiDriver   	[midi_action] Skipping midi event! Audio engine 
*and then a lot more of the [error]
segmentation fault.[/SIZE][/SIZE]
***************************************************************************

Does anyone know what I have done?

Also I removed timidity. Do I need this for anything these days?
--James

---

### Post by Dave_Connor on 2008-10-12
You could try reinstalling. "sudo apt-get --purge remove hydrogen && sudo apt-get install hydrogen"

---

### Post by cino on 2008-10-12
I have already done this, via the synaptic package manager.
Thanks anyway.

---

### Post by Stochastic on 2008-10-13
I'd say delete this file: /usr/share/hydrogen/data/demo_songs/GM_kit_Jazzy.h2song
or at lease rename it, so that Hydrogen doesn't try to load it on startup.

It looks to be the initiator of the errors and it was created on a very old version of hydrogen.  In theory things should be backwards compatible, but that may be triggering whatever issue you're having.

---

### Post by cino on 2008-10-15
> **Stochastic said:**
> I'd say delete this file: /usr/share/hydrogen/data/demo_songs/GM_kit_Jazzy.h2song
or at lease rename it, so that Hydrogen doesn't try to load it on startup.

It looks to be the initiator of the errors and it was created on a very old version of hydrogen.  In theory things should be backwards compatible, but that may be triggering whatever issue you're having.

I have not deleted the file yet, as at the moment hydrogen will open without jack control, however, cannot when jack is running.

[ERROR]     AlsaMidiDriver   	[midi_action] Skipping midi event! Audio engine not ready.

???
 erm, how do become owner in the giu? Or how do I delete this file as a command? Forgive my ignorance.

---

### Post by Stochastic on 2008-10-15
Oh it does run, but has issues with jack control... that's an entirely different ballgame.  It's not the file's fault, its the fact that jack takes control over the alsa driver so hydrogen can't access it.  Hydrogen needs to be set - in its preferences - to use the jack audio driver.  You should also uncheck the option in hydrogen's prefereces to 'auto-connect' to jack as this causes many headaches in some setups.

If you've already done this, and you still are having troubles with hydrogen, then maybe that file is to blame (it's just a guess on my part).  The safe thing to do is to rename it rather than delete it as that way you can always name it back if things break more...  just do ```
sudo mv /usr/share/hydrogen/data/demo_songs/GM_kit_Jazzy.h2song /usr/share/hydrogen/data/demo_songs/_GM_kit_Jazzy.h2song
```
that extra underscore infront of the filename is all that's needed to keep hydrogen from finding that song (and it's an easy way of remembering what it was originally called, should you need to put it back).

But most likely it's just a driver issue.

---

