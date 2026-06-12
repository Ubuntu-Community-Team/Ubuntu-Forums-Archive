---
title: "Cacti on VMWare Server"
date: 2009-07-10
forum: Server Platforms
---

### Post by supanatral on 2009-07-10
I would like to monitor the performance of my Ubuntu Server because it's running VMWare. I found a neat program called Cacti and it seems to do exactly what I'm looking for.

The problem is that I'm currently running vmware server on port 80 for http and port 443 for https.  Is there a way to change the port for Cacti? Or a way to change the vmware Server.

---

### Post by Cheesemill on 2009-07-10
You can change the VMware Server port by running:
```
sudo vmware-config.pl
```

---

