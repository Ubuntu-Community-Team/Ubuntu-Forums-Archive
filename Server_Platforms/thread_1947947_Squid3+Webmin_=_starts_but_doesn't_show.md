---
title: "Squid3+Webmin = starts but doesn't show?"
date: 2012-03-27
forum: Server Platforms
---

### Post by Sternfan on 2012-03-27
Hi all,

I am running ubuntu 11.10, squid3.1 & latest webmin.  I managed to get it running, however after I hit START SQUID in webmin it just sits there on start.  I can verify that it is running by using the proxy on another PC, but for whatever reason webmin isn't seeing it as started.

Did I miss something?  Not install something?  The other webmin server all show that squid has started (and even has a button to stop).

Thanks,
Rob

---

### Post by Sternfan on 2012-03-27
Ok - I finally figured it out and am posting the solution so that if anyone else has this problem, maybe it will help someone.

In module configuration the path to the PID file should be /var/run/squid3.pid - I had it as squid.pid and it was not working correctly.

Rob

---

