---
title: "user specific hosts file"
date: 2009-06-30
forum: Server Platforms
---

### Post by anonmars on 2009-06-30
Is there a way specify a user-specific hosts file?  If I'm on a box where I can't add stuff to /etc/hosts I'd still like to have certain names resolve to IPs for my user.

Thanks.

---

### Post by anonmars on 2009-06-30
> **anonmars said:**
> Is there a way specify a user-specific hosts file?  If I'm on a box where I can't add stuff to /etc/hosts I'd still like to have certain names resolve to IPs for my user.

Thanks.

Note: I'm not able to setup a DNS server in my scenario, as suggested in: [http://ubuntuforums.org/showthread.php?t=891788](http://ubuntuforums.org/showthread.php?t=891788)

---

### Post by bab1 on 2009-06-30
> **anonmars said:**
> Note: I'm not able to setup a DNS server in my scenario, as suggested in: [http://ubuntuforums.org/showthread.php?t=891788](http://ubuntuforums.org/showthread.php?t=891788)

Are you the administrator of the LAN domain?  A DNS server (or etc/hosts) is not an ad-hoc device.  Especially if it is authoritative (not just caching).

What are you attempting to do?  maybe there is another way to achieve your goal.

---

### Post by Vegan on 2009-06-30
The hosts file is general and is not designed for user specific setups.

The same applies to DNS entries.

The is by design of DNS is intended to be mirrored to provide a consistent database to machines and resources.

---

