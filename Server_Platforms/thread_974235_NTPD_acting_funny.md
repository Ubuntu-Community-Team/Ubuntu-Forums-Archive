---
title: "NTPD acting funny?"
date: 2008-11-07
forum: Server Platforms
---

### Post by Krupski on 2008-11-07
Hi all,

After tons of research and experimenting, I finally figured out how to make my 8.10 64 bit home file server provide NTP time to the rest of my home intranet.

Strange thing is, it takes a good 15 to 20 seconds to get a time sync from my server.

The server is sync'd to several Stratum 1 NIST servers (no problem there).

But, if I run a time client to get time FROM my server, it's slow.

Example: Timesync an XP machine to "time-a.nist.gov" and it gets the time almost instantly (1 second or less).

Example: Timesync an XP machine to my file server - it takes 15 to 20 seconds, then it succeeds.

Any ideas why this is and how I can fix it?

Thanks!

-- Roger

---

### Post by CrucifiedEgo on 2008-11-07
Anything in the server or client logs?  Without any information, it's hard to guess what the problem might be.

---

### Post by MJN on 2008-11-07
You could try a packet trace (e.g. using Ethereal) and capture the UDP port 123 packets - this will reveal which side is hanging around and possibly anything else out of the ordinary. 

Of course, if it is your ntp daemon then these delays will be internal in which case stop the service and restart it in the foreground (ntpd -n) with increasing levels of debugging (-d, -dd ... see the man page)

All that said, is this really a problem that needs fixing? Time updates should be done in the background hence aside from your manual testing you should never be aware that it is taking 20 seconds to set the clock.

Mathew

---

