---
title: "Rsyslog: Formatted logs/alert"
date: 2013-06-11
forum: Server Platforms
---

### Post by termvrl on 2013-06-11
Hi All,

I want to ask, in rsyslog, how can we standardize the logs output. For e.g :

Let say, this is my fwall logs sample:-

<163>May 23 2013 15:59:55: %ASA-3-106014: Deny inbound icmp src outside:69.12.34.53 dst outside:192.168.0.10 (type 8, code 0)

i want to process the incoming log and produce output like this:-

device:firewall alertdate: May-23-2013, alerttime: 15:59:55, Protocol:icmp, sourceip:69.12.34.53, destip: 192.168.0.10

The reason is i need to standardize the logs, different devices produce different type/format of logs. It is difficult to find/analyse in the future if the log in raw format.

Thanks.

---

