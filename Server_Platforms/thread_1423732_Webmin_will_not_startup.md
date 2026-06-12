---
title: "Webmin will not startup"
date: 2010-03-07
forum: Server Platforms
---

### Post by espressobeanie on 2010-03-07
After I installed Webmin, it worked fine till my next restart. Then I can't access it through the web. I tried "/etc/webmin/reboot" and it said the Webmin-Core was loaded. I then run "netstat -tlnp" and it shows that a perl program is on the correct port that webmin is setup. Yet, I still can't get a connection through my browser. ufw has that port open on tcp and udp, so I'm still not sure where the problem lies. Any advice?

---

### Post by Queue29 on 2010-03-07
Did you do:

# /etc/webmin/start 

?

---

### Post by espressobeanie on 2010-03-07
I did. It still had no effect. The only thing I recently did since was to install openssh client and server so I could connect using an sftp to transfer files. The ssh server is running on port 22 and Webmin is on 10000. Unless they are competing for the same resource somewhere.

Some other obvious things are: it's connected to a router, it worked while connected to the same router before, sudo apt-get update works, and that's all I can really think of.


It's working right now, but on many bootups, it doesn't work. Not sure if it's a bug.

---

