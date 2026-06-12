---
title: "No audio device in Windows XP using VirtualBox"
date: 2009-06-10
forum: Virtualisation
---

### Post by nemodot on 2009-06-10
Hi there!

I have installed the guest additions and checked the Audio configuration on VirtualBox but the sound still doesn't work. Take a look at the attached file (screenshot).

---

### Post by YldGuy on 2009-06-10
> **nemodot said:**
> Hi there!

I have installed the guest additions and checked the Audio configuration on VirtualBox but the sound still doesn't work. Take a look at the attached file (screenshot).

On my machine (running Jaunty) i kept the default pulseaudio settings and it worked fine. On another machine running Intrepid, I had to set system sound and vbox sound to ALSA and it worked fine only then.

---

### Post by nemodot on 2009-06-10
tried that, didn't work.

---

### Post by nemodot on 2009-06-12
Should I search for my chipset drivers?

---

### Post by Solrac924 on 2009-08-12
try this:

double-click Volume Control
Change Device to Playback: ALSA PCM...via DMA (**PulseAudio Mixer**)

launch VirtualBox
when the "machine" is powered off, click Settings
click Audio
uncheck "Enable Audio" & check it again to enable it
select PulseAudio
click OK

---

