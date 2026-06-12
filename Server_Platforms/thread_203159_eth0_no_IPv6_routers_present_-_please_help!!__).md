---
title: "eth0: no IPv6 routers present - please help!!  :)"
date: 2006-06-24
forum: Server Platforms
---

### Post by ShawnHunt on 2006-06-24
I've installed the latest server version and configured it as a lamp server.  Everything is working great, except for one recurring problem.  I get the error:

eth0: no IPv6 routers present

I get this error anywhere from 20 seconds to 40 minutes after restarting the network.  Right after I get that error, I am no longer able to access that machine over the net or the domains that it's hosting until I reset the network.  Any suggestions?

---

### Post by Iowan on 2006-06-26
[http://www.ubuntuforums.org/showthread.php?t=199249&highlight=disable+ipv6]("http://www.ubuntuforums.org/showthread.php?t=199249&highlight=disable+ipv6")
[http://ubuntuforums.org/showthread.php?t=87798&highlight=IPV6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=IPV6")

Here's a couple of threads dealing with similar (if not the same) problem.  Hope they help...

---

### Post by ShawnHunt on 2006-06-26
Well, I was able to disable IPv6, thinking that was the problem, but it's not.  Every 40 seconds or so, my machine just refuses to accept incoming traffic.  I'll try to access the hosted domain through it, and it will just time out.  Other times, it will connect without an issue.  This is both in my home network and over the web.  Heard of anything like this?

---

### Post by LordHunter317 on 2006-06-26
Yes, but we'd need some more details on what you're running, your bandwidth utilization, what hardware you have.

The message in question is purely informative and should be considered as such.  You don't need to disable IPv6 (and shouldn't).

---

