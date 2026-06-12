---
title: "[IDEA] Create 'Speakers and sound' GUI"
date: 2008-02-07
forum: Ubuntu Brainstorm
---

### Post by oponek on 2008-02-07
Summary

Create a simple 'Speakers and sound' graphical configuration tool using gtk (analogous to the Screens and Graphics existing in Ubuntu).

There have been complaints that Ubuntu lacks a speakers and sound configuration utility, which forces newbies to manually edit .asoundrc and /etc/modules.d/alsa files if they want to use surround sound or another soundcard. Manually editing the files is difficult and frustrating to them, and not an ideal way to handle the issue on the long run. 

The 'Speakers and sound' tool should be able to configure: * default soundcard used by Ubuntu * speakers configuration (from 2.0/2.1 to surround 5.1, 7.1, etc.)

To find out more:

[https://blueprints.launchpad.net/ubuntu/+spec/speakers-and-sound-gtk](https://blueprints.launchpad.net/ubuntu/+spec/speakers-and-sound-gtk)
[https://wiki.ubuntu.com/SpeakersAndSound](https://wiki.ubuntu.com/SpeakersAndSound)

---

### Post by steeleyuk on 2008-02-07
If this was going to be included, I'd suggest putting it in the Sound Preferences window under a new tab, rather than creating a seperate GUI.

Edit: 

> Bill have 2 sound cards installed and would like to use the 2nd instead of the first.

Doesn't the PulseAudio GUI allow for this?

---

### Post by gnomeuser on 2008-02-07
The PulseAudio lead developer claims he is working on integrating much of this functionality into the Pulseaudio control GUI. Our Red Hat overlords are paying him so expect work to progress swiftly..

---

### Post by oponek on 2008-02-07
The Pulseaudio control GUI has a lot of advanced options but we need simply 2 options integrated with gnome-sound-properties. Speakers and default sound card configuration. Or maybe Pulseaudio control will be installed with next ubuntu release by default?

---

### Post by gnomeuser on 2008-02-07
> **oponek said:**
> The Pulseaudio control GUI has a lot of advanced options but we need simply 2 options integrated with gnome-sound-properties. Speakers and default sound card configuration. Or maybe Pulseaudio control will be installed with next ubuntu release by default?

I think Lennart means to integrate it into the volume control application, so you can select your output and input by say right clicking the interface.. I am sorry if I was unclear

---

### Post by oponek on 2008-02-29
Brainstorm shows that users need that tool: [http://brainstorm.ubuntu.com/idea/129/](http://brainstorm.ubuntu.com/idea/129/) .

---

### Post by mixmatch on 2008-09-23
I totally agree. It really feels like audio device configuration is a nightmare.

---

### Post by TrojanSkin on 2008-09-23
Am I being rubbish? I'm using Ubuntu Studio but don't have a speaker icon at the top. I've managed to get everything working on my T30, even the wireless, but I can't turn the sound up!!! It's REALLY quiet! Tried Google etc., but no luck!

---

### Post by gnomeuser on 2008-09-23
openSUSE carries a patch for paprefs to allow this I think. I am unsure if it has been included in trunk.

---

### Post by markbuntu on 2008-10-16
We really need a one stop shop gui for configuring sound. The current situation is far too confusing and probably the single biggest reason why people abandon Ubuntu after they install it. 

If pavucontrol ends up doing all that Lennart is hoping for it, then it should just replace System/Preferences/Sound, the Volume Control, Sound mixers, everything. If it cannot replace all these it should be incorporated into something that can.

People are plugging all sorts of audio gear into their computers.  Even if this stuff is autodetected the user is often not informed or asked what they want to do with it. Nothing asks them what they want to do with their ipod or setup thier new  usb headest to get their skype calls or use their surround sound or the digital output and they are completely lost figuring out how to do any of that.

We really need a Control Center for Sound. I could then happily toss my 10,000 page guide to sound in Ubuntu onto the trash heap.

---

