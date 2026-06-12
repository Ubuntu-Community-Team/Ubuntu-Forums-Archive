---
title: "help getting mailman properly integrated with postfix"
date: 2009-05-24
forum: Server Platforms
---

### Post by whosmatt on 2009-05-24
I've installed mailman from the repositories and have it working mostly fine; trying to finish out the integration with postfix by following section 6.1 of the mailman install guide about how to integrate with postfix, except I skipped the step about chown /var/lib/mailman/data/aliases and instead gave 0666 to that file.  All seems to have gone fine but when I try to create a list from the web interface, I get an error. When i go to the logs i see this:

```
May 24 15:13:13 2009 mailmanctl(8187): PID unreadable in: /var/run/mailman/mailman.pid
May 24 15:13:13 2009 mailmanctl(8187): [Errno 2] No such file or directory: '/var/run/mailman/mailman.pid'
May 24 15:13:13 2009 mailmanctl(8187): Is qrunner even running?
May 24 17:38:34 2009 (5991) command failed: /usr/sbin/postalias /var/lib/mailman/data/aliases (status: 1, Operation not permitted)

```

FYI it worked ok before I followed the integration steps but i was trying to get it to update postfix aliases when new list was created.  perhaps i need ubuntu-specific documentation?

I am running on very little sleep right now so forgive me if i'm just being stupid but not sure where to go.

thanks,

-m

EDIT: nm, I forgot to make aliases.db group writable.  duh.

---

