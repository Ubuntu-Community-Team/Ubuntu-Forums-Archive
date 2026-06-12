---
title: "Unable to Access MaaS Web Interface"
date: 2013-05-03
forum: Ubuntu Cloud and Juju
---

### Post by michaelbruton on 2013-05-03
I have installed Ubuntu 12.04 LTS and 13.04 on virtual machines to mess around with MaaS.  These are fresh installs and from both I cannot access the http://<hostname>/MAAS web interface.  I can access the default Apache website at http://<hostname>/ without issue.  When looking at the Apache error log (/var/log/apache2/error.log), I see the following:

[Fri May 03 12:11:04 2013] [error] [client 172.16.86.1] File does not exist: /var/www/maas


I followed the following guide:

[https://maas.ubuntu.com/docs/quantal/install.html](https://maas.ubuntu.com/docs/quantal/install.html)


And used the following troubleshooting guide, but everything checked out:

[https://maas.ubuntu.com/docs/quantal/troubleshooting.html](https://maas.ubuntu.com/docs/quantal/troubleshooting.html)


I couldn't find any other threads on this topic, any ideas?

---

