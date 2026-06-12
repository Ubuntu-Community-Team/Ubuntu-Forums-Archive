---
title: "Qemu_audio_timer_period"
date: 2016-07-01
forum: Virtualisation
---

### Post by T.J. on 2016-07-01
Just a heads up!  This is not a problem to be resolved.  I already know the reason.  This is just in the hope of saving someone else many hours of problems. 

Some HowTos suggest using: QEMU_AUDIO_TIMER_PERIOD=0.  After much annoyance, I discovered that under certain conditions changing the timer period can cause a VM to freeze up. 

The idea is that it will help resolve certain sound issues.  I recommend that you use that with caution, especially since the default driver for qemu/kvm in most Debian style pre-built binaries  is Pulseaudio.  It appears to work with ALSA when forced, but I have not tested ALSA to any extent. I have far too much that software requires PA to really disable it.  (You probably shouldn't unless you know what you are doing.  ALSA is hard to configure, and generally speaking non-portable - that is - Linux only. PA is used so that programs are easier to port.)

If you use: QEMU_AUDIO_DRV=pa with QEMU_AUDIO_TIMER_PERIOD=0,  you will receive a console message: "WARNING: I/O thread spun for 1000 iterations" on Debian Jessie and Ubuntu 16.04.  After that, the virtual machine will become completely unresponsive. 

I do not believe that Pulseaudio is responsible for this behaviour.

---

### Post by MAFoElffen on 2016-07-02
Thank you very much for the tip.

---

