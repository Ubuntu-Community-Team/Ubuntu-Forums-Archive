---
title: "Network Intrusion detection"
date: 2008-01-30
forum: Server Platforms
---

### Post by BDNiner on 2008-01-30
I followed this post on howtoforge.com:

[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated)

Now how can I go about testing to see if it works? Do i have to wait until someone tries to enter my network?

---

### Post by Yhetti on 2008-01-30
I don't know what default rules snort comes with, but it should certainly detect a basic port scan.  Something like

nmap -sS 127.0.0.1

Note: it might not detect portscans from localhost.  It should.  I've never used base, it's it's probably avaliable at [http://YOUR.IP.ADDRESS/base-1.3.9](http://YOUR.IP.ADDRESS/base-1.3.9) (Based on the howto)

---

