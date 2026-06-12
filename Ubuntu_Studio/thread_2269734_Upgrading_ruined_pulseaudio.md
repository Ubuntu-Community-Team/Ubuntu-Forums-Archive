---
title: "Upgrading ruined pulseaudio"
date: 2015-03-17
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-03-17
So I took all the security updates, and upgraded to the new kernel and [systemd]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2015-March/001130.html"), etc. ... and now pulseaudio is acting flaky again. 

It's confused by the various sinks, and so I'm back to disabling onboard audio. Unfortunately, I also had to manually edit default.pa and make jack sinks load on boot. If I forget to turn on the audio interface before boot, pulseaudio's server never connects. So basically, jackd is always running.


After bad experiences, I avoid purging ALSA, and trying to get rid of pulseaudio almost always leads to disaster. So there's got to be a better fix. 


Any ideas?


Oh... and I almost forgot. The bluetooth sinks fail at boot. Although they can find and pair with speaker output... the connection fails. I have to manually load it at the command line with pactl.

---

