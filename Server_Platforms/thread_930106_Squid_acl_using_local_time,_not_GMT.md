---
title: "Squid acl using local time, not GMT ?"
date: 2008-09-25
forum: Server Platforms
---

### Post by dbyrne on 2008-09-25
Don't know if this is possible, but can't find any solutions. Ideas or advice appreciated.

I have a squid transparent proxy set up to control internet access, specifically to prevent access to some sites at 'homework time' :) I've configured an acl in squid.conf like so:

```
acl homework_time time MTWHF 14:30-17:00

```

However as we are currently running Daylight Savings Time (BST = GMT+1), this will have to be changed to "15:30-18:00" at the end of October when we revert to GMT.

Any ideas on how to make this refer to local time rather than server time ? My only thought is a script that updates the conf file and restarts the squid server on the appropriate dates ... pretty kludgey.

I'm running squid 2.6.STABLE14.

---

### Post by windependence on 2008-09-25
Is your server not set to automatically adjust to daylight time?

-Tim

---

### Post by dbyrne on 2008-10-02
> **windependence said:**
> Is your server not set to automatically adjust to daylight time?

-Tim

As far as I'm aware the base system time is GMT (=UTC), and the time is *displayed* according to the user, e.g. using the environment variable TZ=GMT0BST ? I've never come across a unix system that actually adjusts the physical system time when daylight savings time comes in :confused:

---

