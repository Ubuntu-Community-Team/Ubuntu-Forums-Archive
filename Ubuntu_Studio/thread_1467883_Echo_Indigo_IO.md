---
title: "Echo Indigo IO"
date: 2010-05-01
forum: Ubuntu Studio
---

### Post by occurrence on 2010-05-01
Have any of you guys got the Echo Indigo IO to work in 10.4? It founds my soundcard, but there is no audio output.

---

### Post by imrazor on 2010-08-15
> **occurrence said:**
> Have any of you guys got the Echo Indigo IO to work in 10.4? It founds my soundcard, but there is no audio output.

This is a few months late, but maybe it will help someone else. The Echo Indigo needs firmware loaded first. This "firmware" is actually a binary file on your ubuntu laptop that needs to be loaded into memory before the OS can produce sound. In Lucid Lynx, the simplest way to get the firmware is to download it straight from the ALSA project ( [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) )The ALSA version in Lucid is 1.0.22, and I couldn't find a 1.0.22 version of the firmware. So i just downloaded the 1.0.23 version and built that. Download the firmware into an empty directory, or one without critical files, then run these commands in a terminal as follows:

$ bunzip2 alsa-firmware-1.0.23.tar.bz2
$ tar -vxf alsa-firmware-1.0.23.tar
$ cd alsa-firmware-1.0.23
$ ./configure
$ make
$ sudo make install

Then reboot and cross your fingers. Or at least, the above worked for me. Good luck!

On reboot, your internal audio will probably still be the default audio device. If you're using pulseaudio, you can probably disable internal audio from the GNOME menu System>Preferences>Sound. I removed pulseaudio because it was eating my old laptop's CPU alive. If you're using ALSA like me, you can either disable your onboard audio in BIOS, or use something like VLC to output audio to a secondary sound card.

---

