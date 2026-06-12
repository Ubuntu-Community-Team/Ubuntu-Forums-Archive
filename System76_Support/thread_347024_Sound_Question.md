---
title: "Sound Question"
date: 2007-01-26
forum: System76 Support
---

### Post by aay on 2007-01-26
I don't know how, but my .asoundrc and .asoundrc.asoundconf files are gone for my Gazelle Performance.  Without these I have no sound of course.

Could someone with the Gazelle Performance please paste in their .asoundrc.asoundconf file?

Thanks,

Adam

---

### Post by aay on 2007-01-26
Ok I was able to get these files back by running:

asoundconf set-default-card Intel

Here's my current .asoundrc.asoundconf

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Intel
defaults.ctl.card Intel
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix_max_periods 0
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0

What's weird is that apps are playing sound files w/o any problem, but I get no sound.  Yes, I checked the volume levels.

Adam

---

### Post by aay on 2007-01-26
Ok, seems that after a reboot sound is working with the above mentioned .asoundrc and .asoundrc.asoundconf files.

I wonder what happened though.

Adam

---

### Post by rpadhikari on 2007-01-27
I have question about my sound card. I am using Dell OptiPlex 620 Desktop Computer using Ubuntu 6.1. I could not listen any audio from my pc. The specification of my sound card ad I obtained from 'lspci -v' command is as follows:

00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01ad
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at ec00 [size=256]
        I/O ports at e8c0 [size=64]
        Memory at feabfa00 (32-bit, non-prefetchable) [size=512]
        Memory at feabf900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

Please suggest me in detail how can I install this sound card properly.
-Raj

---

### Post by crichell on 2007-01-29
If sound isn't working you may want to download and install the latest alsa-driver.  First check which codec you are using and do some searching based on that.

Right click on the speaker by the clock and choose "Open Volume Control"
Click File > Change Device
The second device in the list is your chipset.  Do some searches based on that to find info.  You can also find additional information about your card with the command

cat /proc/asound/card0/codec#0

---

