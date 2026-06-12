---
title: "Disable Console Screen Shutoff"
date: 2010-03-06
forum: Server Platforms
---

### Post by Dr Small on 2010-03-06
Hey guys,

I have my headless server, and just plugged a spare monitor into it, opened up screen, ran htop on it, so I can see the system status, but the screen keeps shutting off after so long. The only way to "wake it up", is to use a local keypress (which means I have to hook a keyboard back up to it).

I have already tried `setterm -powersave off -powerdown 0`, but it didn't affect it any.

Is there any way to disable this powersaving mode?

Thanks,
Dr Small

---

### Post by Dr Small on 2010-03-06
I added the following line to my /etc/rc.local, and it fixed my problem:
```
sh -c 'setterm -blank 0 -powersave off -powerdown 0 < /dev/console > /dev/console 2>&1'
```

Cheers,
Dr Small

---

### Post by KiLaHuRtZ on 2010-03-06
> **Dr Small said:**
> I added the following line to my /etc/rc.local, and it fixed my problem:
```
sh -c 'setterm -blank 0 -powersave off -powerdown 0 < /dev/console > /dev/console 2>&1'
```

Cheers,
Dr Small

This worked on my test server running Lucid, however I have also been trying to fix this on Hardy and it seems it did not work on that server.  I even tried this...

```
sh -c 'setterm -blank 0 -powersave off -powerdown 0 < /dev/tty1 > /dev/tty1 2>&1'
```

...and still no dice.  Any ideas?

---

### Post by KiLaHuRtZ on 2010-03-26
I stand corrected, before I added the line to rc.local and then tried to manually implement it; which did not work.  I just rebooted my server for an update and it now works as it should!  Thanks!

---

