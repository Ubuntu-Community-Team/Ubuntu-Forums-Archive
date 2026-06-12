---
title: "A quick tip for those with older ati cards!"
date: 2014-02-04
forum: Ubuntu, Linux and OS Chat
---

### Post by dave2001 on 2014-02-04
So I recently upgraded my Thinkpad T500 from 12.04 to 13.10. I was disappointed to discover that the proprietary drivers no longer support my discrete graphics card, a an ati Mobility HD 3650. 

 BUT, As Prof. Farnsworth might say "Good News Everyone!" ... reading through some of the community documentation, I discovered the open source "radeon" group of drivers now provide support dynamic power management! In 13.10 this option is not enabled by default, if you want it turned on you need to edit your /etc/default/grub file and add "radeon.dpm=1" so that the edited line looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"
```

Here's the great part: According to my temp sensors, my graphics card is now running an average of at least 10 degrees cooler than before I enabled this option, which is helping the whole laptop stay a bit cooler.
It's even running cooler than in 12.04 when I was using proprietary fglrx driver instead of the open source one. I've not had enough time to test it out yet, but I'm guessing this means a substantial increase in battery time.
This may be old news for most people since 13.10 has been out for a  while, but maybe some other late-adopters out there, like myself, will see  this post and get some benefit from it.

---

### Post by SurfaceUnits on 2014-02-04
[URL="http://ubuntuforums.org/showthread.php?t=2201671"]More info

http://ubuntuforums.org/showthread.php?t=2201671[/URL]

---

