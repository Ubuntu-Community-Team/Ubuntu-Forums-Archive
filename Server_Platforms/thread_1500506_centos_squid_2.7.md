---
title: "centos squid 2.7"
date: 2010-06-03
forum: Server Platforms
---

### Post by Shea7993 on 2010-06-03
Hi

Im an avid ubuntu desktop user, however i started working at a company that runs their firewall,mail and proxy server on centos 5.2, all was working well so never needed to tamper with it, however we (myself and the administrator) randomly decided to install squid3 for its features, the install went well, however squid3 didnt run as we wanted it to, after looking into it reading some material on the net, we realised how stupid we were to not to test it -sigh- so weve purged and removed it and reverted back to 2.6,  now however we even have issues with that too, we install squid 2.6 and start the service, and we get errors that stop, and starting fail, however the status of squid shows its running... Anyone have an idea how to get it back to working order???

Any help and guidance would be greatly appreciated!!!! thanx

---

### Post by jijiisme on 2011-04-22
me too. same same problem

---

### Post by JonRohan on 2011-04-22
What do the squid logs show?

---

### Post by ruffEdgz on 2011-04-22
> **JonRohan said:**
> What do the squid logs show?

To go off this, what does the configuration for /etc/squid/squid.conf show? Please feel free to change the config file so it doesn't have the actual information on it but has something similar that we can look over as well.

The log files should be in /var/log/squid/access.log or if there is an error.log, that will work as well (i checked my squid server logs but didn't see any error logs).

---

