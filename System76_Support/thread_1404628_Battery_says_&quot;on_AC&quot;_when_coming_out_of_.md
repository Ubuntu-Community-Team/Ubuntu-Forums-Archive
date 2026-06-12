---
title: "Battery says &quot;on AC&quot; when coming out of stand-by on battery"
date: 2010-02-11
forum: System76 Support
---

### Post by miniyak on 2010-02-11
I know there was a similar issue here somewhere on the forums but i cant seem to find it.

This was non-existing issue until I did a full install of karmic a few weeks ago, Normally I have my panp5 on ac power and sometimes I put it into stand-by then come back unplug then take my computing power to go. When the session resumes the power notification applet would normally notice that that the power source has change to on battery power and tell me what percent of the battery was left. Now It just seems to always think its on battery power so I can't tell whether the battery is going to die until the led on that chassis starts blinking.

Is there a quick fix to this? I can live w/ it, but seems kinda odd it was working before and not now. Is this similar to the issue of also missing the estimated discard time from the applet?

---

### Post by tlroche on 2010-02-14
> **miniyak said:**
> I did a full install of karmic a few weeks ago

Me too, via `sudo do-release-upgrade`. I also have a PanP5.

> **miniyak said:**
>  Normally I have my panp5 on ac power and sometimes I put it into stand-by then come back unplug then take my computing power to go. 

Me too. (This seems like a pretty standard mode of operation.)

> **miniyak said:**
>  When the session resumes the power notification applet would normally notice that that the power source has change to on battery power and tell me what percent of the battery was left. Now It just seems to always think its on battery power so I can't tell whether the battery is going to die until the led on that chassis starts blinking. 

I have also started observing this recently (past few days). What's the fix?

---

### Post by thomasaaron on 2010-02-15
Not sure. I'll have to do some testing. But it sounds like Ubuntu isn't polling the battery after suspend.

It probably is related to the previous battery polling issue. If so, here's the bug report for it...
[http://bugs.launchpad.net/ubuntu/+source/linux/+bug/412499](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/412499)

(I wouldn't recommend the nVidia driver fix mentioned in that report. I think that is a red herring, and it may cause issues with Synaptic Package Manager.) Recompiling the kernel is the ultimate fix for that particular issue. Why Ubuntu doesn't compile it right in the first place is beyond me.

If it's the same bug, the fix posted here by HotShotDJ...
[http://ubuntuforums.org/showthread.php?t=1290840&highlight=pangolin+power+management](http://ubuntuforums.org/showthread.php?t=1290840&highlight=pangolin+power+management)
...most likely would fix it.

But I'll have to do some testing to know for sure.

---

