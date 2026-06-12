---
title: "help with HIDS"
date: 2010-11-03
forum: Security
---

### Post by jeff.sadowski on 2010-11-03
I am looking for an HIDS (Host based Intrusion Detection System) that logs what program is opening what connections. I want something like lsof that stays open and logs to a file. I was looking at the HIDS sticky post but I am not sure that any of the HIDS's there do what I want. I'm not looking for trojans as much as I am looking for what application is connecting to v.w.x.y port z at a particular time; so that when my network admin accuses my box of being compromised I can look at my corresponding network activity log and see what program/user he is accusing. Then I can look at the log and see what application running as what user is generating said traffic. At which point I can decide what to do about said application. Is there a way to get lsof to stay open and log what programs open a network connection? I want a very simple log looking similar to as follows

Date       Time        Application      User ip           port status
2010-11-03 11:20:00.00 /usr/bin/firefox jeff 91.189.94.12 80   opened
....<other activity that may have happend in between> ...
2010-11-03 11:30:00.00 /usr/bin/firefox jeff 91.189.94.12 80   closed

maybe something with udp traffic just saying "sent" as its status.

Is there anything out there that can create such a nice log?

---

### Post by brian_p on 2010-11-03
> **jeff.sadowski said:**
> 

Is there a way to get lsof to stay open and log what programs open a network connection?

Have you looked at the -r option to lsof? Then some creativity with other lsof options, grep. date, redirection etc.

---

