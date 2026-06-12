---
title: "LTSP client frozen"
date: 2009-09-08
forum: Server Platforms
---

### Post by map7 on 2009-09-08
I'm running Ubuntu 904 32bit desktop with the LTSP packages configured.  I have two clients so far running off the server and these clients are brand new.  The clients are ASUS Eee BOX B202 and an ASUS Eee BOX B204.

The client has frozen a couple of times in one month.  When one client freezes neither the server or the other client freeze.  I have had the B202 freeze, but then I upgraded that workspace with the B204 and it started freezing.

When it freezes the screen and everything on it is frozen and I cannot use the keyboard and mouse to change to a Virtual Terminal or anything.  All that is on the screen is the applications I was working in.  The client still has an IP assigned to it and I can ping that IP.  I can disconnect that IP through the 'thin client manager' software.  At the time of the latest freeze I was using the Openoffice spreadsheet 3.0.

I've been looking in the /var/log files on the server but I don't think this is the right place to look for logs for a client, is there another spot for the client related errors?

What possible causes could this be?  Is it network related as it seems to only be happening in that one room so far.  Could it be the network drivers for the chipset in these ASUS Eee BOX 20x's are failing sometimes?

---

