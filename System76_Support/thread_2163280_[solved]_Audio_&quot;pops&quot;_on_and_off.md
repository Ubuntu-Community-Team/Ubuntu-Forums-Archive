---
title: "[solved] Audio &quot;pops&quot; on and off"
date: 2013-07-17
forum: System76 Support
---

### Post by rorschachwalter on 2013-07-17
When the laptop starts playing media, the audio makes an audible "pop" as it turns on. Likewise, when media playback stops for a few seconds, the audio "pops" back off. It's annoying in speakers and painful in headphones.

Is this something that a software update can fix, or is this just the quality of the machine?

---

### Post by screaminj3sus on 2013-07-17
Does your machine have intel audio? Does this only happen on battery? If so this is probably because of the audio power saving in the driver. When the audio card is idle the controller is turned off, and when you start playing audio and it comes back on you can hear a pop. By default ubuntu has this power saving enabled via a pm-utils script in /usr/lib/pm-utils/power.d/intel-audio-powersave. Try disabling it by doing the following in the terminal:

```
cd /etc/pm/power.d
sudo touch intel-audio-powersave

```

This should override the intel audio power saving script with that blank file so power saving does not get enabled.

---

### Post by rorschachwalter on 2013-07-17
Thanks, that seems to have fixed it. Although now I'm wondering how one might go about restoring the power saving script?

---

### Post by screaminj3sus on 2013-07-18
> **rorschachwalter said:**
> Thanks, that seems to have fixed it. Although now I'm wondering how one might go about restoring the power saving script?

Simply deleting the "dummy script" you created in /etc/pm/power.d will 'restore' the original script :)

---

