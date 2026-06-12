---
title: "pure-ftpd DontResolve being ignored?"
date: 2011-04-12
forum: Server Platforms
---

### Post by bulldog5046 on 2011-04-12
Hi,
 
I'm really confused with this one. Yesterday our FTP cluster went down, i havent yet tracked the reason but i suspect a security update killed it as automatic updates are enabled (i will be turning those off now!).
 
Anyway, FTP connections were receiving a 425 Sorry, Unable to resovle error message, i sound the solution to be to disable dns lookups with the DontResolve > yes option.
 
but for some unknown reason this is only working on my failover box! when i restart pure-ftpd on the primary box the command switch -H is missing?
 
i've done the same thing on both boxes by creating a file in /etc/pure-ftpd/conf called DontResolve and editing it to just read the word 'yes', been over it and checked for spelling mistakes and i cant find any reason why its ignoring the option?
 
does anyone have any ideas to help me get this box back online?
 
Thanks,
Ryan

---

### Post by bulldog5046 on 2011-04-12
DontResovle still not working but i have discovered why this happened and resolved the issue.
 
unfortunately, it was me being stupid yesterday and making a firewall change, i believed i was correcting an error, instead i created one and blocked DNS for the FTP cluster.
 
Oops.....

---

### Post by Fred71 on 2011-04-30
> **bulldog5046 said:**
>  DontResolve and editing it to just read the word 'yes', been over it and checked for spelling mistakes 

instead "yes" put "1" in there

---

