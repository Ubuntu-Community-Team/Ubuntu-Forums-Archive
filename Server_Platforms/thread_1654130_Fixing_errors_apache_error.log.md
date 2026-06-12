---
title: "Fixing errors apache error.log"
date: 2010-12-27
forum: Server Platforms
---

### Post by vparanoia on 2010-12-27
I have been tackling all the errors the keep poping up in my apache error.log
I have searched for information but all i get is matches to people with other problems that i am not having but have this in ther error log.
 
```
 
[Mon Dec 27 20:59:10 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations

```
 
This is my error I get. I'm not sure what is really causing it. At this moment I have no errors with anything that i am doing on my server. aka nothing appears to be broke.
 
I'm just attempting to fix a potential problem before it arises.
 
Thanks for your time
Paranoia

---

### Post by SeijiSensei on 2010-12-28
That's a normal confirmation that Apache was restarted. 

The [notice] at the beginning of the entry means that it's not an error, just information.

---

### Post by Calimo on 2010-12-29
It is triggered by logrotate (normally weekly but your config may differ) after rotating the logs.

---

