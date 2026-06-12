---
title: "Ubunutu Server with WebUI squid user authentication and log/monitoring"
date: 2013-03-18
forum: Server Platforms
---

### Post by xpd777 on 2013-03-18
I'd like to configure an Ubuntu Server box with webadmin or webui.

At the same time as transparent proxy with user authentication and monitoring and logging.

To be used in a school environment

---

### Post by sandyd on 2013-03-18
I would reccomend a bit of reading up on LDAP (Lightweight Directory Access Protocol). LDAP is a database that can be used for user/group management, seperating users into different departments, and so on. For the transparent Proxy, you can use squid and its squid-ldap_auth helper to integrate squid with LDAP. You can then manage access to the proxy through LDAP. LDAP also has a nice web interface called GOsa that can be used to configure users/groups/objects in LDAP.

Though a web interface for configuring Ubuntu can be acchieved by Webmin, it is not reccomended due to security problems.

---

### Post by theHAAG on 2013-04-10
how did you go??

---

### Post by xpd777 on 2013-06-27
Just started with zentyal. I'm still thinking of using proxy authentication or captive portal. I'm very much concerned with what websites that students are visiting.

---

