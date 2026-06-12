---
title: "Migrating DNS servers"
date: 2013-07-11
forum: Server Platforms
---

### Post by nerdtron on 2013-07-11
Has anyone here tried migrating DNS servers?

I mean, we are currently running 1 master and 1 slave dns servers running Red Hat 9. The hardware are just Desktop type Pentium 4 computers and no RAID, no backups!
The situation is really bad although the dns service and requests are still running smoothly, the slave dns hard drive starts to show signs of failure. 
I don't want to wait for them to fail completely so I'm considering to create new dns servers with Ubuntu 12.04.

Any suggestions on how to configure and test a DNS server? I don't want to just replace the old servers and expect the new ones to takeover with no problems.
Also, how will you migrate? In terms of IP address and hostnames, will you shutdown the old ones, and use their IP address as you turn on the new ones? Is it that simple?

Any advice is appreciated.
Thanks!

---

### Post by newbie-user on 2013-07-12
> **nerdtron said:**
> shutdown the old ones, and use their IP address as you turn on the new ones

Yes, that's what I would do. That way you don't have to mess with your DHCP settings. Your clients will still point to same IP addresses for name resolution, they'll just be querying the new servers instead.

Are you using bind? If you are, you can just copy your db files over to the new bind and reference those files in your named.conf.local. If you want to test the new DNS server first, just point a single client to it or use the dig command on the server itself:
```
dig @localhost [some domain]
```

---

### Post by SeijiSensei on 2013-07-12
I'd replace the slave first and point the new slave server to the existing master.  After the records are transferred to the new slave, you can replace the master.  You'll then have one server in production throughout the switchover.

---

### Post by Vegan on 2013-07-12
You can use 3 DNS servers too, for more fault tolerance.

---

