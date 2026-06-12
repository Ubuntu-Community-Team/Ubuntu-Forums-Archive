---
title: "Firewall Xbox 360 and Rygel Question"
date: 2012-04-21
forum: Security
---

### Post by BigCityCat on 2012-04-21
I have looked around and have not been able to find anything. I have installed Rygel. I have been able to use xbox 360 to play media files. As long as the firewall is disabled. Just wondering if anyone had any ideas.

Thanks

---

### Post by jensgeorg on 2012-06-20
> **BigCityCat said:**
> I have looked around and have not been able to find anything. I have installed Rygel. I have been able to use xbox 360 to play media files. As long as the firewall is disabled. Just wondering if anyone had any ideas.

Thanks

SSDP Is hard to handle; there is no connection tracking module for it. The best thing you can do is to configure Rygel to a fixed port, allow TCP access to that and UDP access to/from port 1900.

But that might still not be enough.

---

