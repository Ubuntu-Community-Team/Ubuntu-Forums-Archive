---
title: "Hacking attempt??"
date: 2007-11-24
forum: Server Platforms
---

### Post by twill30 on 2007-11-24
Just checked my logwatch files and saw the following:

Requests with error response codes                                                                                                                              
    400 Bad Request                                                                                                                                              
       /w00tw00t.at.ISC.SANS.DFind:): 4 Time(s)                                                                                                                  
       /w00tw00t.at.ISC.SANS.MSlog:): 1 Time(s)

I've googled it but can't find a coherent response. Is it something I should be wary of?

Also, when I run a Tripwire scan I have been getting (for a couple of days):

modified:  /root

but no files shown as having been added or removed.

---

### Post by MJN on 2007-11-24
Those log entries are very common - they are signs that a bot (likely a compromised machine) is scanning for susceptible machines to infect. In your case it didn't find what it was after (as the URL was malformed - the : ) suffix is wrong) but a vulnerable may have reacted (in terms of becoming compromised). Alternatively, it could just be a bot run by someone with a grudge against ISC/SANS. Either way you need not be concerned (your server reacted 'correctly').

Regarding your Tripwire output I don't use it so cannot comment authoritatively however I assume it is advising you that /root has been modified since you last scanned. If you use the root user I assume this is entirely to be expected. Perhaps even a timestamp change (e.g. last access) could trigger this 'warning' however, as I say, I'm not familiar with exactly how Tripwire works.

Mathew

---

