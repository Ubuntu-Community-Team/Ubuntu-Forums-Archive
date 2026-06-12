---
title: "gazp6 headphones not working after 12.04 upgrade"
date: 2012-07-04
forum: System76 Support
---

### Post by sflicht on 2012-07-04
Hi,

I have a gazp6, about 1 year old. After some issues with the automatic upgrade, I did a clean install of 12.04 last week; everything seemed to work fine (although there are some minor issues here and there). However, I cannot use my headphones: in the new sound settings menu (which has had a facelift), the headphone jack no longer appears as a possible output method. However, sound is played through my headphones when they are plugged in, but the main speakers do not mute. (I had the same issue in 11.10, but manually switching the output from speakers to headphones in the sound settings menu muted the speakers. This workaround is no longer available.) Currently the only way to mute my speakers is to turn the gain down to zero in alsamixer (while keeping the headphone gain positive so I can hear out of them). This works but is annoying. I want the main speakers to auto-mute/unmute when I insert or remove the headphones from the jack! This used to work fine. I don't remember exactly when it broke, but I would guess it was when I moved from 11.04 (which came with the machine) to 11.10.

I've installed the 3.0 system76 driver, but I am wondering if I need to install a special driver for the headphone jack on my machine.

Web search also suggests that manually editing alsa-base.conf could be helpful, but I am not certain what to add to that file to make everything work properly with my hardware.

Thanks,
Sam

---

### Post by CrocoDuck on 2012-07-08
Hi. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1979884](http://ubuntuforums.org/showthread.php?t=1979884)

---

