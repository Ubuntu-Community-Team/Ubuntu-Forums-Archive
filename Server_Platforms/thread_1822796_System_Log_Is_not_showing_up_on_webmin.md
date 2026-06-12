---
title: "System Log Is not showing up on webmin"
date: 2011-08-11
forum: Server Platforms
---

### Post by kustomjs on 2011-08-11
Hi Guys
I am using ubuntu 10.04.3 LTS and I have webmin 1.560 installed but when I look at Un-used Modules its showing system log is there and when I click on it I get this: The syslog configuration file /etc/syslog.conf was not found on your system. Maybe syslog is not installed, or a newer version like syslog-ng is in use, or the module configuration is incorrect.

How do I fix this?

---

### Post by dinu90 on 2011-08-11
The default ubuntu sysloger is rsyslog, perhaps you need to install that module for webmin

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by kustomjs on 2011-08-11
I was able to get to work after switching the settings to: /etc/rsyslog.conf from /etc/syslog.conf

---

