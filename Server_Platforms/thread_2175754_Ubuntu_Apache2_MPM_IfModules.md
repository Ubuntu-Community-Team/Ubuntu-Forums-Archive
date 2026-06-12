---
title: "Ubuntu Apache2 MPM IfModules"
date: 2013-09-20
forum: Server Platforms
---

### Post by newsirchuck on 2013-09-20
After installing Apache2 MySQL and PHP on my server I wanted to adjust the MaxClients, but this is the first time i've seen 3 separate MPM types all apparently active. I have 
<IfModule mpm_prefork_module>

<IfModule mpm_worker_module>

<IfModule mpm_event_module>

Each of these modules have uncommented MaxClients but I don't know which one I need to actually adjust, and I don't know if it is ok to comment out the other ones? Is there a way to tell which of the three IfModuals are being triggered when visiting my page? Can I safely comment out 2 of the three IfModuals, or are there times they become necessary?

Thanks

---

