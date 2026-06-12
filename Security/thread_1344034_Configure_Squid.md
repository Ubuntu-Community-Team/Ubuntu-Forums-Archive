---
title: "Configure Squid"
date: 2009-12-02
forum: Security
---

### Post by lgjsheron on 2009-12-02
Hi, I hv a problem in my home computer. I like to block some websites in my local machine, Then i found the better way is using Squid. But i have a problem while configure. After i configure the squid.conf file I restart the squid. The blocked website was displayed. How to over come this problem. I made a file containing all the block sites in my /etc/squid/squid-block.acl file

acl blocksites dstdomain "/etc/squid/squid-block.acl"

http_access deny blocksites

Any one. Any idea.

---

### Post by i.r.id10t on 2009-12-03
Have you set your browser to use your local machine (or whatever machine is running squid) as its proxy?

---

### Post by suzypeppercorn on 2009-12-03
Squid is a proxy server. So for it to block websites, your browser needs to be setup to be using your proxy server, wherever it may be located.

If you are running squid on the same machine you want to block websites, then the proxy's address would be 127.0.0.1

---

