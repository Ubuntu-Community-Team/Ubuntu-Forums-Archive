---
title: "ntp-server at booting"
date: 2010-01-23
forum: Server Platforms
---

### Post by ICEB3AR on 2010-01-23
Hi :)
I've set up a ubuntu server 8.04 with ntp-server. At boot time the ntp service is started, but
```
ntpq -p
```
delivers:
No association ID's returned.

I've set up the ntp the way to be able above my private network to use this as reference.
If i restart ntp everything is fine. 

First i thought that the problem is that dhcp is started after ntp, but after changing the start-order in the runlevels this enigma remains.

Hope you can help me.
Best Regards

---

### Post by ICEB3AR on 2010-01-26
Bump

---

### Post by ICEB3AR on 2010-01-26
UPDATE:

it seems as if the local nameserver (only nameserver in resolv.conf) starts after the ntp daemon. How can that be, if the Link in the runlevel-directories of bind and ntp is:

S15bind9
S99ntp

On booting process the following messages arise (freely quoted):

Stopping ntp-server ntpd [OK]
Stopping ntp-server ntpd [OK]
Starting ntp-server ntpd [OK]
Starting ntp-server ntpd [OK]
Staring name service-deamon bind [OK] -> I Expect that this is S15bind9
Starting ntp-server ntpd [OK] -> And this will probably be the S99ntp

But where do the other message come from and how can i change the order/arising of the command

---

