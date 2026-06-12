---
title: "Battery Monitor Applet probleem"
date: 2007-11-20
forum: System76 Support
---

### Post by bretthall on 2007-11-20
Yesterday my battery monitor applet quit working.  By this I mean that instead of showing a battery and telling me how much charge I have the applet just displays an electrical cord and tells me if I'm plugged in or not.  I dug around in /proc/acpi and the battery directory is empty, I'm guessing that this is the issue.  I know that the battery is connected and charged because I'm writing this on battery power right now.  Any idea how to get my battery status back?  I'm running feisty on a gazv4.

---

### Post by thomasaaron on 2007-11-20
Does it happen after hibernating? See this post. If it does, let's consolidate.

[http://ubuntuforums.org/showthread.php?t=614793](http://ubuntuforums.org/showthread.php?t=614793)

---

### Post by bretthall on 2007-11-20
> **thomasaaron said:**
> Does it happen after hibernating? See this post. If it does, let's consolidate.

[http://ubuntuforums.org/showthread.php?t=614793](http://ubuntuforums.org/showthread.php?t=614793)

Unfortunately it is happening all the time.  I haven't been using hibernate or suspend  because battery status has always been lost after using them.  Now I don't get battery status at all even after a full reboot.

One thing I forgot to mention in my initial post was that I had to do a hard-reboot(hold down the power button until the machine shuts off) yesterday due to vmware acting up.  I had battery status after the reboot.  Later that night when I got home my battery was dead and the machine wouldn't boot without being plugged in.  This happened even though when I shut it down I'm pretty sure that the battery still had more than 20% charge.

---

### Post by bretthall on 2007-11-20
I must have knocked something loose carrying the laptop back and forth to work yesterday.  I removed and then put the battery back in and now the battery monitor works fine.

---

