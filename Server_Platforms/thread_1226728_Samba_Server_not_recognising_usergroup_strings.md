---
title: "Samba Server not recognising user/group strings"
date: 2009-07-29
forum: Server Platforms
---

### Post by Fallen_Demon on 2009-07-29
Hi people,

Very strange samba issue going on at the office here on an Ubuntu hardy server running Samba 3.0.28a. We have it on a Win2K3 domain as a NAS, and periodically it will change the user/group permissions to something random rather than the user/group access we want it to.

We fix this by:
[LIST=1]
[*]Leaving the domain
[*]Joining the domain
[*]chown'ing the files to 'administrator'
[*]chmod'ing group access to the appropriate entry
[/LIST]

There is a cron job set to do the ch'ing we need, but obviously this is a quick workaround. Is there any ideas on how to fix this permanently?

Thanks in advance

---

