---
title: "Snort Rule Problem"
date: 2016-10-09
forum: Security
---

### Post by sniper8752 on 2016-10-09
I am trying to add the porn rules to my snort configuration, and when I test the configuration file for it, I get this error:

```
sudo snort -T -c /etc/snort/snort.conf -i eth0
.....
ERROR: /etc/snort/rules/porn.rules(24) Unknown ClassType: kickass-porn
Fatal Error, Quitting..

```

I am implementing the default file that came with the software package.  What do I need to do to resolve this?

---

### Post by sniper8752 on 2016-10-11
Anybody have any ideas?

---

### Post by bashiergui on 2016-10-18
See this thread [https://forum.pfsense.org/index.php?topic=23185.0](https://forum.pfsense.org/index.php?topic=23185.0)
> **/usr/local/etc/snort/rules/porn.rules** is not a snort.org rule or emergingthreats.net rule. Please remove said file and your updates will work. Maybe a wrong rule got add by snort.org. The Current rule downloads do not have porn.rules.

Though if you want that rule just add **kickass-porn** to clasification.config in the dir /usr/local/etc/snort/rules. Then do an update.

---

