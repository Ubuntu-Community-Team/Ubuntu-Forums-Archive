---
title: "Nagios 3 - NRPE only install"
date: 2009-09-21
forum: Server Platforms
---

### Post by badger_fruit on 2009-09-21
I have a Nagios server which monitors my computers, it's running on Suse11.0 and has been for a while; I have just built a Ubuntu machine which I would like to monitor from the existing Nagios server ... I have been googling for a while but can't seem to find how to install just the NRPE plug-in neeeded to do this; I tried ...

```
sudo apt-get install nagios-nrpe-plugin
```

... but it tries to start the nagios service on the machine (which isn't installed), fails and doesn't install any of the configuration files etc for the NRPE plug-in.

I am worried that if I do ```
sudo apt-get install nagios3
``` then it will install the full product including web-content which simply is not needed.

As it's been a while since I installed the NRPE onto the other computers it monitors, I don't recall the procedure, mind you, they are all Suse so it'd be different anyway!

If there's anyone who can help I would love to hear from them.
Many thanks to all for reading and any advice or suggestions they can provide.

---

### Post by badger_fruit on 2009-09-21
Sorry for the bump; no replies in 11 hours :(

---

### Post by midwesterndirt on 2009-09-23
If this is just a host being monitored by a separate nagios server, you want to install the nagios-nrpe-server package.

```
sudo apt-get install nagios-nrpe-server
```

---

### Post by KiLaHuRtZ on 2009-09-25
> **midwesterndirt said:**
> If this is just a host being monitored by a separate nagios server, you want to install the nagios-nrpe-server package.

```
sudo apt-get install nagios-nrpe-server
```

Yup, he's right.  It's probably failing because you need to configure '/etc/nagios/nrpe.cfg' first.

---

