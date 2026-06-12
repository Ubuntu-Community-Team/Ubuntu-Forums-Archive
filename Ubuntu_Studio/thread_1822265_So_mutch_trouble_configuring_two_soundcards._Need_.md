---
title: "So mutch trouble configuring two soundcards. Need Help!!!!"
date: 2011-08-10
forum: Ubuntu Studio
---

### Post by jotagallo on 2011-08-10
Hi folks, i'm new in the ubuntu studio word and i'm having a lot of trouble to configure it correctly.
First of all, i'm using a Dell Inspiron 1525 running Ubuntu lucid 10.04, and a few weeks ago i decided to upgrade to ubuntu studio to record my own music. Upgrading success, jack and ardour did working well with my onboard soundcard (hda-intel), i was recording little pieces of sound on ardour with applications like hydrogen, pure data and sound captured by my onboard soundcard. Until here, everything was working fine, no problems!
So i decided to purchase a sound interface to record guitars, bass and other things with a good quality. I choosed M-audio Fast Track Ultra, after a huge research to witch soundcard had a good compartibility with linuxes systems.
I connected the interface in my system and it was recognazing the interface well, but no inputs was available in jack connections (only the MIDI channel in ALSA tab). I had read so many solutions that did not worked in my case, so i decided to compile the drivers following this guide:[http://forum.masterdrive.it/blogs/master85/ubuntu-9-10-compilare-alsa-driver-55/](http://forum.masterdrive.it/blogs/master85/ubuntu-9-10-compilare-alsa-driver-55/). After all the steps and running alsaconfig, the result is: No device running. Yes, i lost the driver of my onboard soundcard this way. alsaconfig says that the driver is well-configured, but it don't work. My hardware list is empty (System->Preferences->Sound->hardware) and 'aplay -l' tells me that no sound device was found.
For now on, i want my onboard device back, to listen my music while i'm working, it's very important to me. After this, i need some help to configure Fast Track Ultra and Jack/ALSA. Can anyone help me please ??

Sorry the bad english, i'm from brazil and there's no documentation for this subject in portuguese. I expect you guys from the community to help me with this lot of trouble.

---

