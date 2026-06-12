---
title: "[SOLVED] Audacity fails to start"
date: 2009-01-09
forum: Ubuntu Studio
---

### Post by wd5gnr on 2009-01-09
I've used Audacity before. Went to fire it up this morning and nothing happened. Process just froze. Tried running from the command line. No messages... just hangs.

Here's what I have tried:
> Removed audacity configuration files
> Tried as another user
> Reinstalled audacity
> Purged audacity and reinstalled
> Installed older version of audacity
> Built audacity from source!
> Removed .asoundrc temporarily
> Tried to go down to the 1.2 version but even though I have older wx libs present, configure can't find it even with a prefix so that didn't work.

None of the above made any difference at all

This is on 8.10 Kubuntu 64-bit.

Hard to troubleshoot with absolutely no messages. 

Any ideas?

---

### Post by Stochastic on 2009-01-09
Have you been starting it from command line to see what the last message is before it hangs?

---

### Post by wd5gnr on 2009-01-09
Yes as I mentioned there are no messages at all. Once I kill the configuration files I get the dialog box that asks me what language I want to use and then it freezes with no further GUI or console messages.

Update:
I found it. Something about the bluetooth audio (which I have never got to work anyway) was hanging it. I recompiled with debugging on and ran under a debugger to figure that out. Had to remove the dongle and then kill all the alsa bluetooth stuff (removed all of it since it doesn't work well anyway).

---

