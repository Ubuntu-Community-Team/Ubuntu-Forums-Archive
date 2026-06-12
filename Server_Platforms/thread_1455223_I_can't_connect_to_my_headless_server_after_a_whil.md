---
title: "I can't connect to my headless server after a while"
date: 2010-04-15
forum: Server Platforms
---

### Post by Adric on 2010-04-15
I would like to start by making clear that I am not a systems administrator. I am a poweruser who used an old machine to set up a home server.

The problem is that everything works just fine after bootup for aproximately ten minutes. Then the server disappears from the network and there's no way of reaching it. It has a static IP, outside the range of DHCP leases, is connected directly to a home DSL/Wireless router and has a keyboard attached but no monitor.

The other day I booted it up with a monitor attached trying to find out what was wrong. Not being able to find anything, I disconnected the monitor. The server stood up for hours until I rebooted it —don't ask me why I rebooted it, I keep asking myself— but then it went back to its usual behaviour.

Any ideas?

---

### Post by Iowan on 2010-04-15
There are a couple of other threads about this - I'll see if I can find one/them. For some reason, all works well until monitor/keyboard are disconnected.
[Here]("http://ubuntuforums.org/showthread.php?p=9125919#post9125919") is one - not far away...

---

### Post by Adric on 2010-04-16
Well, my case isn't exactly the same because it does boot, but only stays up for ~10 min. But I'll check the BIOS in case there's sth wrong there (Energy Star I'm looking at you).

---

### Post by volkswagner on 2010-04-16
You don't have any log information?

I had a similar issue, but it would last several hours after boot, then become unresponsive.  I found tons of I/O errors.  I was able to dd the drive to a new drive and all was well.

My 2 cents...

If the serve wont stay up long enough to check logs, perhaps you can boot it with a live CD to read the logs, or copy them elsewhere.

---

### Post by Adric on 2010-04-16
I have checked the logs and didn't find anything remarkable.

The strange thing is that if there is a monitor attached during bootup it does stay up indefinitely. It becomes unresponsive only when there is no monitor while booting. So I guess the fix is just leave it running and don't reboot, which is a good idea for a server anyway...

---

