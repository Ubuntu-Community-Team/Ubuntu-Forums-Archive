---
title: "Updated ubuntu 17.10 daily lost networking and graphics?"
date: 2017-09-19
forum: Ubuntu, Linux and OS Chat
---

### Post by dankegel on 2017-09-19
Just kvetching here.  This isn't especially surprising before beta 2,
but my Ubuntu 17.10 system (installed from daily a
few weeks ago) lost its networking and graphics this weekend.  

I can get networking back if I boot in recovery mode, enable networking,
and continue.
I can't get graphics to work (startx fails, or does something very strange).

Trying to troubleshoot made me realize that I now have zero idea
how current Ubuntu starts up networking.  A flowchart
would be helpful.  There are layers upon layers upon layers,
and stale documentation everywhere.

Doing a fresh reinstall from today's daily now, because that's
the only way to make sure I didn't break something myself.
If the problem persists, I'll post real info.

(Well, trying to; graphics broke on my main Ubuntu 16.04 system recently,
and device names are so strange these days I'm not sure
I'm confident to figure out how to write a startup image to
a usb drive via the commandline anymore!  Ah, the future.
I think I have a system with working desktop somewhere, so I'm not stuck, but geez.)

---

### Post by dankegel on 2017-09-19
Fresh install made the networking problem go away.
Graphics ok now too, though I haven't tried proprietary drivers yet (nvidia gtx 750).

---

### Post by hic3456 on 2017-10-22
I think I've hit a similar issue with graphics failing, possibly due to the use of proprietary Nvidia drivers, or something similar.

TL;DR: I've installed 17.10 on a perfectly working desktop running 16.04LTS (via 17.04, as they don't let you "jump") and then it all went pear-shape, I can't even boot into the thing.

Would you know how to get 17.10 to boot into recovery mode? Hitting the Left-shift key while booting does not seem to do anything.
Also suggestions as to how to remove the proprietary drivers from the command line (once I get into recovery mode) would be great, thanks.

---

