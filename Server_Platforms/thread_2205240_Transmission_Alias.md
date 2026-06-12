---
title: "Transmission Alias"
date: 2014-02-12
forum: Server Platforms
---

### Post by futureslay on 2014-02-12
Hi,

Messing with Aliases in order to allow myself to be able to add torrents to a queue when I'm behind a college firewall.
I'm already using ports 80 and 81 for different applications, so moving the daemon itself to a new port other than the default one of 9091 is illogical and pointless.

Have created an apache.conf file inside /etc/transmission-daemon and made a symbolic link inside /etc/apache2/conf.d.
Apache reloads and accepts it, but every time I try to access the alias, I get a 403 error. The file itself is pretty bare - I just want to get this working, is all.

Contents below:

```
Alias /transmission /usr/share/transmission

<Proxy *>
Order allow,deny
allow from all
</Proxy>
```

Any ideas at all?

Regards,
Dom

---

### Post by brokenhachi on 2014-02-12
oops, sorry i misunderstood the post:confused: I'll go ahead and leave it alone!

---

