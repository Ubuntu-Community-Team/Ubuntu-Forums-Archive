---
title: "Ubuntu Server, Squid and filedescriptors"
date: 2007-11-14
forum: Server Platforms
---

### Post by johnnyBgone on 2007-11-14
I am using Ubuntu 6.06 LTS (since upgraded to 7.10 but that comes later) to run a web caching service on a university campus. The migration to Ubuntu was recent and up until then I was using Fedora Core to perform this function flawlessly.

The problem I am experiencing is that once starting the Squid process within minutes I start getting errors in the cache.log file:

WARNING! Your cache is running out of filedescriptors

I had never experienced this previously with Fedora Core and am quite puzzled why this would occur in Ubnutu...

What I have done (unsuccessfully)
Changes to squid.conf:
half_closed clients  off
pconn_timeout 30 seconds
server_persistent_connections off
max_filedesc 8192 <- unrecognized but tried anyway

I read somewhere in the archives regarding increasing filedescriptors in /etc/security/limit.conf (this was due to problems with ntop though) on a per user basis. I increased the limits for user proxy to no avail.

As a last restort tactic I upgraded 6.06 to 7.10 (newer squid... STABLE14 in stead of STABLE5 if memory serves). Which had no effect except to kill vi and vim, but that is a problem for another day.

Anyone with suggestions, kind words or (God forbid) a new Fedora Core disk?

---

### Post by pete.dawgg on 2007-11-14
because squid uses millions of very small files your system may run out of fds - that's the warning. before you start squid you have to increase this number OR lower the number squid uses - what u did was just the opposite (may adversely affect squid's performance)


straight from the squid-mailinglist:

> infos about actually used file handles in:
/proc/sys/fs/file-nr

To increase maximum of file handles:
echo yourincreasednummberoffileshandles > /proc/sys/fs/file-max

For persistent entries edit:
/etc/sysctl.conf

Have a look at:
/usr/src/linux-yourkernelversion/Documentation/sysctl/kernel.txt
(pls check before u do anything like that)

if you have to run a reliable service for a univesity i suggest you get  and read the book  "squid: the definitive guide" by duane wessels.
i'm too lazy to look up ur problem there right now but i know there's a solution.

---

### Post by johnnyBgone on 2007-11-21
Althought the problem is not resolved I seem to have tracked down the culprit(s). Anyone using Skype!

With Skype's persistent connection (for availabiltiy etc.) the file descriptors get eaten up faster than a Big Mac at fat camp! The resolution? Well I guess a recompile of Squid is the only resort (as suggested in Squid: The definitive guide) or a old PC, similar setup just for Skype users... much easier and quicker and the bonus is I can still take advantage of apt-get updates...

To block Skype on the proxy I set an ACL to match IP addresses that don't resolve (as tailing the access.log proves that this is a Skype symptom) and denying access. The bonus of this is it seems to prevent most http tunneling as well :D

Now it may sound that I might be a BOFH but anyone living in South Africa will know that bandwidth here is a precious commodity...

---

### Post by pete.dawgg on 2007-11-26
rather than banning stuff you know is bad you could configure squid to accept only stuff that is acceptable, eg allow the conect method ONLY for ssl and have a list of ports that can be used or useragents that are acceptable.
skype ist extremely tricky, though, since it is intended to get thru firewalls (udp-holepunching).
or you could allow only a certain number of connections per ip/user...
i haven't tested it with recent skype-versions but "my" squid doesn't let skype-calls get thru.

---

