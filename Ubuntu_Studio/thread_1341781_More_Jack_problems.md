---
title: "More Jack problems"
date: 2009-11-30
forum: Ubuntu Studio
---

### Post by RenBlangle on 2009-11-30
Hello everyone, and sorry to post yet another Jack thread. 

I've just moved to Ubuntu 9.04 from XP, and am trying to get Jack and alsa to produce sound. I've read through the many Jack threads here but can't find an answer - so perhaps there's someone out there who is isn't as sick to death of Jack configuration as I am who can help me out?

Here's the problem, and my current set-up ...

- Jack starts without reporting any errors (ie no server error messages) but doesn't actually output any sound
- I'm using the alsa driver, 44100hz, real-time kernel (but must have tried every possible combination of settings)
- The connections tab has lines between 'System' and whatever apps I have running.
- MIDI (in the alsa tab of connections) works fine
- Pure Data and Audacity both start the Jack driver without reporting errors, but still no sound output.
- I'm using 9.04 with a few of the Ubuntu Studio packages installed
- Jack is started via qjackctl, then start the audio app
- The sound card is just the mobo on-board sound. Works fine without Jack running (ie choosing just plain alsa driver in PD or whatever, or just playing mp3s)

So far I have ...

- installed an RT kernel, Ubuntu Studio Controls, and some of the Ubuntu Studio audio packages
- created an audio group, added myself to it, edited /etc/security/limits.conf
- made sure that the mixer levels aren't turned down or muted
- followed these instructions: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)
- purged and re-installed alsa and jack
- started Jack and audio apps as root
- completely removed pulseaudio - this actually worked for about a minute, but when I changed the latency settings Jack crashed. After re-starting and changing the settings back, the problem returned.
- probably other stuff over the past few weeks which I've forgotten

Does anyone have any other ideas?

---

### Post by VertexPusher on 2009-11-30
Which ALSA device is Jack connecting to? Are you sure it's the correct one?

---

### Post by RenBlangle on 2009-11-30
Hi, thanks for your quick response! I'm not sure which device it's connecting to - in the Jack setup panel I'm just selecting 'alsa' as the driver. Is there a way I can finding out more info?

Or do you mean the input and output devices? In that case I'm using hw:0, but have tried the others as well with no luck.

---

