---
title: "ufw ordering question"
date: 2014-01-13
forum: Security
---

### Post by andrew725 on 2014-01-13
Hi,

I have some rules set up in UFW that were implemented without using a numbering system so they were given default numbers in the order they were added.

I've recently blocked traffic from an IP address that is below the IPv4 traffic.  Is it possible to renumber the existing rules so that my DENY rule can be before the ALLOW rules?

This is how it currently looks:
andrew@localhost:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 3232/tcp                   ALLOW IN    Anywhere
[ 2] 80/tcp                     ALLOW IN    Anywhere
[ 3] 25/tcp                     ALLOW IN    Anywhere
[ 4] 143/tcp                    ALLOW IN    Anywhere
[ 5] Anywhere                   DENY IN     IP Address
[ 6] 3232/tcp                   ALLOW IN    Anywhere (v6)
[ 7] 80/tcp                     ALLOW IN    Anywhere (v6)
[ 8] 25/tcp                     ALLOW IN    Anywhere (v6)
[ 9] 143/tcp                    ALLOW IN    Anywhere (v6)

---

### Post by steeldriver on 2014-01-13
Yes you should be able to give a specific rule # on the command line e.g.

```

sudo ufw **insert 1** deny from 192.168.1.65 to any

```

The existing rule numbers will get bumped down to accommodate the new rule. You can then delete the previous deny rule by its (new) number.

---

### Post by andrew725 on 2014-01-13
> **steeldriver said:**
> Yes you should be able to give a specific rule # on the command line e.g.

```

sudo ufw **insert 1** deny from 192.168.1.65 to any

```

The existing rule numbers will get bumped down to accommodate the new rule. You can then delete the previous deny rule by its (new) number.

I had to delete the old DENY rule before it would properly add the new one.  when I tried adding the new one without deleting the old one, it returned this error:
Skipping inserting existing rule

nonetheless, thanks!

---

