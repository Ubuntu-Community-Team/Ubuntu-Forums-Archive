---
title: "OpenVAS fails, 0% test complete"
date: 2010-04-15
forum: Security
---

### Post by saphil on 2010-04-15
OpenVAS installed through repos. cert made, server is running, client connects to server and loads plugins.
However, when I run a test the progress window comes up, the tests use all of my cpu cycles and the progress never gets past zero %.
Left running to test 2 machines previously discovered and thoroughly tested with nmap.
Is this a firewall issue.  The docs say openVAS connects on port 9390, and it connects on that port to the client, but it is listening on lo only
wolf@telcontar:~$ sudo netstat -nap | grep openvas
tcp        0      0 0.0.0.0:9390            0.0.0.0:*               LISTEN      22356/openvasd: wai
tcp        0      0 127.0.0.1:9390          127.0.0.1:49273         ESTABLISHED 23404/openvasd: ser
tcp        0      0 127.0.0.1:9390          127.0.0.1:54703         ESTABLISHED 17022/openvasd: ser
tcp        0      0 127.0.0.1:9390          127.0.0.1:38535         ESTABLISHED 23374/openvasd: ser
tcp        0      0 127.0.0.1:9390          127.0.0.1:55243         ESTABLISHED 2077/openvasd: serv

Is this a firewall issue or is OpenVAS config somehow wrong?

----
I discovered that I had somehow failed to put in the ports to be searched into the field for ports.  It worked far better after I added the ports.

---

