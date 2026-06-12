---
title: "sound system parameter being reset after rc.local, resume from suspend"
date: 2022-01-24
forum: Ubuntu Development Version
---

### Post by sgage on 2022-01-24
I have a new issue with my sound stack in Jammy. I have Intel Display Audio and the Realtek High Definition Audio. By default the stack is set up such that the 'auto power saving' mode is on, which results in loud 'blip' or 'pop' sounds as power save kicks in or if sound is needed while power save is engaged. For years I have worked around this by putting the following in /etc/rc.local:

echo 0 > /sys/module/snd_hda_intel/parameters/power_save

It has worked fine since I got this computer in 2018. In Jammy, this parameter is being set back to 1 some time after rc.local runs (I can confirm that rc.local successfully sets it to 0). I have also tried putting this code on an @reboot line in crontab, and also in alsa-base.conf. No joy. Even after I set it back to 0, it is set to 1 again upon resuming from suspend. 

Does anyone else experience this? Any ideas for a workaround? Any idea of what package to file a bug report against? I searched, but could not find anything similar.

TIA...

---

### Post by corradoventu on 2022-01-25
May be related tho this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052)

---

### Post by sgage on 2022-01-25
> **corradoventu said:**
> May be related tho this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1953052)

Yes, I actually replied to your thread on this issue, wondering if it was related. I've also added a 'me too' to the bug report. 

Curiously, Debian Bookworm, while it has the volume reset bug, does NOT have this issue. And Mint Una has this issue, but not the volume reset issue! So I think they are two different problems...

[edit: Also, the volume reset bug doesn't happen upon resume from suspend. I am suspecting some systemd plumbing funniness.]

---

### Post by Smask on 2022-01-25
I commented out the power-save line in **/etc/pulse/default.pa** The offending line:[I]
```
load-module module-suspend-on-idle
```[/I]

---

### Post by sgage on 2022-01-25
> **Smask said:**
> I commented out the power-save line in **/etc/pulse/default.pa** The offending line:[I]
```
load-module module-suspend-on-idle
```[/I]

Well, that sure seems to take care of it, and right at the source. Thank you very much! The modern Linux sound stack is a complicated thing...

---

