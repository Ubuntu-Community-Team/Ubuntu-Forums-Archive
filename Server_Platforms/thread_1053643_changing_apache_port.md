---
title: "changing apache port"
date: 2009-01-28
forum: Server Platforms
---

### Post by perks on 2009-01-28
My ISP blocks port 80. I've tried running my server using port 78 and have it forwarded in my router's config. I also changed the port in ports.conf and restarted Apache. However, when I try to access my site from [http://67.81.64.58:78](http://67.81.64.58:78) or [http://192.168.1.150:78](http://192.168.1.150:78), I get a 404 error. However when I don't specify a port, I get the "It Works!" page. Any help is much appreciated.

---

### Post by Wayne_V on 2009-01-28
from ports.conf:

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default

Look for VirtualHost in /etc/apache2/sites-enabled/000-default

---

### Post by perks on 2009-01-29
Thanks a lot, that got it working!

---

