---
title: "Lighttpd init.d script fails to create PID file"
date: 2010-11-09
forum: Server Platforms
---

### Post by Tommetje on 2010-11-09
Hey all

I did an **apt-get install ligghtpd** in Ubuntu 10.04 and when the service is started, it fails to create a PID file in */var/run*. This means I can't stop the service using the command **/etc/init.d/lighttpd stop**. There are no error messages shown (or at least, none that I can find).

I've compared the /etc/init.d/lighttpd script witht the /etc/init.d/ssh script but couldn't find any real differences in the say the service gets started.

It's a clean install and I didn't modify the init.d script so I'm wondering if someone knows
a) if there should be some error messages and if so, where I can see them.
b) how I can solve this problem.

---

