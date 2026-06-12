---
title: "Server Web Monitor"
date: 2008-03-20
forum: Server Platforms
---

### Post by SuperMiguel on 2008-03-20
I want something like ISPconfig for a lamp, ssh, and samba server just to have a web interface of whats going on on my server, like help me setup services if needed, tell me how much ram and hard drive is being use, etc, etc, i tried ISPconfig but since i dont have a mail server it fails the installations... thanks =)

---

### Post by TurboRush on 2008-03-20
Munin maybe???

[http://howtoforge.com/server_monitoring_monit_munin](http://howtoforge.com/server_monitoring_monit_munin)

---

### Post by kwambus on 2008-03-21
Actually I would recommend Webmin, it's available from the repositories also:

apt-get install webmin

Further information at:

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by vpsville on 2008-03-21
Webmin is exactly what you want.

---

### Post by teqsun on 2008-03-21
I have been running webmin for a day now and its great!  even though im a noob I would still reccomend it.

---

### Post by CharlieSummers on 2008-03-21
> **kwambus said:**
> Actually I would recommend Webmin, it's available from the repositories also:

apt-get install webmin

Er...no, at least not the default repositories:

```
# apt-get --dry-run install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate
```

---

### Post by kwambus on 2008-03-28
My bad, I honestly thought it was in the Repo's. It certainly used to be. Either way you can install it from source by downloading at:

[www.webmin.com](www.webmin.com)

There are some reasonable instructions at:

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)

For gutsy, look for the heading - "Installing Webmin in Ubuntu Gutsy Gibbon"

Hope that helps.

P.S. I believe enabling Multiverse & Universe Repos makes this available.

---

