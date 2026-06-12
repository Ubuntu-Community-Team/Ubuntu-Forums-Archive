---
title: "RSYSLOG weird behavior"
date: 2014-03-12
forum: Server Platforms
---

### Post by TheOnlyChosenOne on 2014-03-12
Hi

I manage a bunch of servers which are all reachable between each other. I set up remote forwarding for rsyslog on one server. To a certain remote server. I sort them by ip ($template FILENAME,"/var/log/%fromhost-ip%/syslog.log").
Now I get messages from other servers too, although I did not set that up :).

Another question. I have the next rule:
```
$template FILENAME,"/var/log/%fromhost-ip%/syslog.log"
```
which puts everything under "syslog.log". I don't want this. I want to have the same division like locally (faillog, maillog, ...).

---

