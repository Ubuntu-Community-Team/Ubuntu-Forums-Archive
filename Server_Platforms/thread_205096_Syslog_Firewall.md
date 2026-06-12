---
title: "Syslog Firewall"
date: 2006-06-27
forum: Server Platforms
---

### Post by mattwestm on 2006-06-27
Hi, I have a Netgear FVS318 firewall router. I have the logs sent to a syslog server (ubuntu). Although I never see the logs. How do I set this up to receive the logs? Thanks, Matt

---

### Post by jvl on 2006-06-28
change SYSLOGD="-u syslog" to SYSLOGD="-u syslog -r" in /etc/init.d/sysklogd, restart the service and allow port 514/udp in in packet filter.

---

