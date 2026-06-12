---
title: "Audio problems after upgrade to Karmic on starling"
date: 2010-01-16
forum: System76 Support
---

### Post by thunderbolt16 on 2010-01-16
I've been able to successfully upgrade to to Karmic from Jaunty on my starling netbook. However, I'm having some audio problems.

I'm not getting notifications pings from Pidgin and occasionally getting getting issues with multiple pieces of sound running. Specifically popping when sounds are being played.

I remember a dialog coming up about switching some audio config file. I don't know if that caused the problem.

Does anyone have a clue on what direction I should head to fix this problem? I think it has to do with the audio mixer being used, how should I try to tweak those settings?

Under the System -> Preferences -> Audio dialog, it shows applications playing sound even when no sound comes out of the speakers.

Thanks,
Ryan

**Update!**

I was able to fix it by using this procedure:

1. Edit the file /etc/modprobe.d/alsa-base.conf and comment the last line :
#options snd-hda-intel power_save=10 power_save_controller=N

As seen in this post. [http://ubuntuforums.org/showpost.php?p=8227063&postcount=14](http://ubuntuforums.org/showpost.php?p=8227063&postcount=14)

---

