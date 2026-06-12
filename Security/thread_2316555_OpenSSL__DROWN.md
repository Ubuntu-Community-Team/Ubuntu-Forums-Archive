---
title: "OpenSSL / DROWN"
date: 2016-03-09
forum: Security
---

### Post by mike403 on 2016-03-09
Hi all


looking for a little help. 


I am running Ubuntu Server 15.10 and I notice the version of open ssl is 1.0.2d. But reading DROWN Vulnerabilities  post ([https://www.openssl.org/news/secadv/20160301.txt](https://www.openssl.org/news/secadv/20160301.txt)) I see i should looking at OpenSSL 1.0.2g


Can someone advise how I move up to 1.0.2g? But I guess I need to understand what impact this would have on the server

Thanks

---

### Post by mastablasta on 2016-03-09
you should be able to check it server is actually vulnerable here: [https://drownattack.com/](https://drownattack.com/)

package: [https://launchpad.net/ubuntu/+source/openssl/1.0.2g-1ubuntu1](https://launchpad.net/ubuntu/+source/openssl/1.0.2g-1ubuntu1)

also a guide: [http://www.miguelvallejo.com/updating-to-openssl-1-0-2g-on-ubuntu-server-12-04-14-04-lts-to-stop-cve-2016-0800-drown-attack/](http://www.miguelvallejo.com/updating-to-openssl-1-0-2g-on-ubuntu-server-12-04-14-04-lts-to-stop-cve-2016-0800-drown-attack/)

I wonder why it hasn't made it yet to LTS version in regular security updates?!

---

### Post by mike403 on 2016-03-09
Thanks for this. But I cant see if 15.10 is needing to be updated, still little confused on that.  I have no GUI loaded on so running from CLI only. I will keep digging

Thanks for install link, i will try that on my test bed server.

> **mastablasta said:**
> you should be able to check it server is actually vulnerable here: [https://drownattack.com/](https://drownattack.com/)

package: [https://launchpad.net/ubuntu/+source/openssl/1.0.2g-1ubuntu1](https://launchpad.net/ubuntu/+source/openssl/1.0.2g-1ubuntu1)

also a guide: [http://www.miguelvallejo.com/updating-to-openssl-1-0-2g-on-ubuntu-server-12-04-14-04-lts-to-stop-cve-2016-0800-drown-attack/](http://www.miguelvallejo.com/updating-to-openssl-1-0-2g-on-ubuntu-server-12-04-14-04-lts-to-stop-cve-2016-0800-drown-attack/)

I wonder why it hasn't made it yet to LTS version in regular security updates?!

---

