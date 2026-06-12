---
title: "Suspend or hibernate or equivalent?"
date: 2010-12-01
forum: Server Platforms
---

### Post by Veovis Muad'dib on 2010-12-01
I'm trying to get my server to either shut off or go into a low power mode when not in use.  I need to access it through SMB, SSH, and eventually VNC, and I would like it to wake up when I try to do that.  If I have to I can send magic packets to wake it, but I'm the only one who will use that, others will just complain to me that the server is down.

---

### Post by miegiel on 2010-12-01
> **Veovis Muad'dib said:**
> I'm trying to get my server to either shut off or go into a low power mode when not in use.  I need to access it through SMB, SSH, and eventually VNC, and I would like it to wake up when I try to do that.  If I have to I can send magic packets to wake it, but I'm the only one who will use that, others will just complain to me that the server is down.

Never used wake on lan, but it seems (if your card suports wol) you can use ethtool to make your network card wake on almost anything. See wol in [http://manpages.ubuntu.com/manpages/maverick/man8/ethtool.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/ethtool.8.html)

---

### Post by egpetrich on 2010-12-01
There's a giant thread discussing how to get wake-on-lan working:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

PowerNap is supposed to suspend/hibernate your system automatically, depending on the activity of specified processes. It's described in this thread, I think, but I gather that documentation is sparse:

[http://ubuntuforums.org/showthread.php?t=1335400](http://ubuntuforums.org/showthread.php?t=1335400)

If your motherboard and CPU support it, "cpufreqd" is supposed to assist in setting appropriate clock frequencies and voltage levels. My CPU is a bit too old to benefit from this, so I haven't had any success using it.

---

