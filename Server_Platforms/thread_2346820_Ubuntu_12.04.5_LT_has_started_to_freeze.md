---
title: "Ubuntu 12.04.5 LT has started to freeze"
date: 2016-12-19
forum: Server Platforms
---

### Post by sdhweb on 2016-12-19
Hello,

Our Ubuntu 12.04.5 LTS has suddenly startet to freeze. It stops responding to PING and can no longer be reached via SSH. It happened for the first time on Saturday and happened again today (Monday). This is a server in production so it's not a good thing. Also, I admit I'm not very skilled when it comes to Linux, hence this post. The server runs on a Hyper-V platform, but it has been stable for month before it started to behave like this. A couple of weeks ago we increased the amount of RAM from 8GB up to 24GB. 

Where and how should I start looking for errors in order to solve this?

Thanks

---

### Post by Irihapeti on 2016-12-19
Moved to *Server Platforms*. You're likely to get help more quickly here.

---

### Post by Graham_Willis on 2016-12-20
Are there other machines running on this Hyper-V?

Places worth looking:

/var/log/kern.log
/var/log/syslog
dmesg

Also, it's good to regularly check the standard utilities like top etc.

---

