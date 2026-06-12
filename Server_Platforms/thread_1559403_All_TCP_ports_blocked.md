---
title: "All TCP ports blocked?"
date: 2010-08-23
forum: Server Platforms
---

### Post by gregburnham on 2010-08-23
I'm having intermittent problems with a server (10.04, running on a generic Intel box).

As seemingly random times, for a couple of hours or so at a time, the server is non-responsive to TCP requests (web, imap, pop3, smtp, ssh, etc., etc.) but I can still ping it during these times.

I'm fairly certain that the box is not the subject of some external attack (it's in a University server room and I would be altered if that were the case) and ntop reports that there's only been 3 Gigs of traffic over the past 5 days.

Any ideas what could be the cause of this?  Or where I can start to look to find out?

Thanks,
Greg

---

### Post by brsaylor on 2010-08-23
I'm having a similar mysterious problem.  HTTPS on 443 and 8443 as well as SSH connections from machines that aren't on the same subnet are refused.  However, I can SSH in from a machine on the same subnet, and without doing anything more than logging in, everything is suddenly back to normal.  This has happened 3 times, with the same strange solution.  I've never found a clue in the log files.  I have UFW enabled and it is logging blocked connections, but it does not logged these refused connections.  I'd be grateful if anyone could shed some light on this problem.

Ben

---

### Post by craigp84 on 2010-08-24
Hi,

In both your cases i wouldn't be surprised to find out it's something external to your boxes causing the problems.

The only way to make sensible progress diagnosing these issues is with a packet sniffer. Load up a laptop with knoppix or something and plug it into your server's switch. Enable port mirroring on the switch so you can see the server traffic duplicated via the laptop's port.

Take it from there.

---

