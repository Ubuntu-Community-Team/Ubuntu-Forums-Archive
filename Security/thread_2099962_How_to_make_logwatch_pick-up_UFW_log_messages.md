---
title: "How to make logwatch pick-up UFW log messages"
date: 2012-12-31
forum: Security
---

### Post by cs224 on 2012-12-31
I am using UFW and logwatch. I've recently upgraded from ubuntu 10.04LTS to 12.04LTS. Previously I got in my daily logwatch reports information about blocked connection attempts. With 12.04 this section is missing now.

My question would be: how do I have to configure logwatch to get this information again?

---

### Post by chadk5utc on 2012-12-31
what log level are you using?
> # The default detail level for the report.
# This can either be Low, Med, High or a number.
# Low = 0
# Med = 5
# High = 10
Detail = ????

---

### Post by cs224 on 2013-01-01
The log level of UFW is:
Protokollierung: on (low)

The detail level of logwtach is the default one:
./default.conf/logwatch.conf:
Detail = Low

---

### Post by unspawn on 2013-01-03
> **cs224 said:**
> Previously I got in my daily logwatch reports information about blocked connection attempts. With 12.04 this section is missing now. 

My question would be: how do I have to configure logwatch to get this information again?
Trying to be methodical about it, couple of things:
- Is your iptables rule set identical including --log-levels?
- Is the Syslog destination for kernel logs the same as it was?
- Does logwatch.conf have the "iptables" entry commented out?
- Does ignore.conf have any related entries?
- Does 'logwatch --detail high' show the required nfo?
- Does 'logwatch --debug' show it opens the log file alright?

---

