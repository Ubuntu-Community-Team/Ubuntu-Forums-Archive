---
title: "Kubuntu 21.04 Hirsute no sound"
date: 2021-03-03
forum: Ubuntu Development Version
---

### Post by gus_zernial on 2021-03-03
I have AMD X570 mobo, 5600X CPU, Kubuntu 21.04 development latest with all updates, kernel 5.10.0-14-generic, Nvidia GTX 1650 graphics card. Generally working well, but no sound.

Card 0 is NVidia HDA HDMI (I've turned off NVIDIA HDMI in System Settings audio settings)
Card 1 is Generic [HD-Audio Generic], device 0: Realtek ALCS1200A Analog

The ACLS1200A uses snd_hda_intel and snd_hda_codec_realtek, the correct sound modules seem to be loaded, and the Card 1 sound device shows up in System Settings

"journalctl -b|grep -i -e alsa -e sound -e snd" messages seem to indicate sound card(s) identified and Sound Service started, and the only mesage I can find that looks vaguely amiss is:
"systemd-sysv-generator: SysV service '/etc/init.d/alsa-utils' lacks a native systemd unit file. Automatically generating a unit file for compatibility. Please update package to include a native systemd unit file, in order to make it more safe and robust."

The sound works using my Windows 10 "Win2go" (live image) USB stick, but not on my original Kubuntu 21.04 live USB install stick, or the installed 21.04 with updates.

I've set the volumes in alsamixer and I've tried "lots of things" to fix, no joy. I can provide more information, but I'd like to ask first if sound is tested/working in 21.04 development?

Thx, Gus

---

### Post by guiverc on 2021-03-03
> **gus_zernial said:**
> I'd like to ask first if sound is tested/working in 21.04 development?


I'm replying on my primary desktop, which was *bumped* to *hirsute* about 30 hours after *groovy* was released as 20.10.

I'm listed currently as running 131 QA-tests using *hirsute* on various devices too.

It's a *development* release, so problems can occur on the odd occasion, with them fixed usually in a few days, however I don't recall seeing or hearing of any *audio* issues, but your hardware differs to the ~26 devices I test on.

If I have issues, I usually resolve in `pavucontrol` (*pulse audio volume control*) though, not alsa.

---

