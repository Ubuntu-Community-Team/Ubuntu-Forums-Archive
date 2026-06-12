---
title: "slow responses if left alone for awhile..."
date: 2006-06-29
forum: Server Platforms
---

### Post by fizgig on 2006-06-29
I notice that the server I've installed wont respond to requests promptly if I haven't used it for awhile (hour or so).  I'm talking about requests to connect to the ssh service or to browse to a wiki that's hosted on it or even an ldap request.

If I retry connecting to it (refresh...refresh...refresh...) the web server service will eventually get going.  Same with putty (reconnect....reconnect...reconnect...)

I'm thinking it might have to do with hard drive spindown but that's a guess.

Anyone have any suggestions?

---

### Post by houstonbofh on 2006-06-30
[QUOTE=fizgig]I'm thinking it might have to do with hard drive spindown but that's a guess.[/QUOTE]
That was my guess too.  Change your power management.

---

### Post by MJN on 2006-06-30
If you think it's a HDD spindown issue have you tried upping the sleep timer, or disabling it altogether (man hdparm if you don't know how).
 
Mathew

---

### Post by fizgig on 2006-06-30
Turns out it was an IP address conflict!! It wasn't anything to do with linux!

Although, it would have been nice to see something in one of the log files that would suggest that to me.  I didn't see mention of that anywhere and found out through luck.

---

