---
title: "OSSEC and alert  pam_mount(spawn.c:128)"
date: 2011-09-06
forum: Security
---

### Post by drifting on 2011-09-06
Any one any idea what this is? I am a noob to OSSEC and the documentation is quite confusing.It would not be so bad if I knew what it was complaining about. Here is the alert that is driving me nuts:-


OSSEC HIDS Notification.
2011 Sep 06 23:17:13

Received From: vs->/var/log/auth.log
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:12 vs su[10614]: pam_mount(spawn.c:128): error setting uid to 0



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2011 Sep 06 23:17:19

Received From: vs->/var/log/auth.log
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:18 vs su[10644]: pam_mount(spawn.c:128): error setting uid to 0



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2011 Sep 06 23:17:19

Received From: vs->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:18 vs CRON[10527]: (CRON) error (grandchild #10529 failed with exit status 1)



 --END OF NOTIFICATION

---

### Post by Dangertux on 2011-09-06
> **drifting said:**
> Any one any idea what this is? I am a noob to OSSEC and the documentation is quite confusing.It would not be so bad if I knew what it was complaining about. Here is the alert that is driving me nuts:-


OSSEC HIDS Notification.
2011 Sep 06 23:17:13

Received From: vs->/var/log/auth.log
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:12 vs su[10614]: pam_mount(spawn.c:128): error setting uid to 0



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2011 Sep 06 23:17:19

Received From: vs->/var/log/auth.log
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:18 vs su[10644]: pam_mount(spawn.c:128): error setting uid to 0



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2011 Sep 06 23:17:19

Received From: vs->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Sep  6 23:17:18 vs CRON[10527]: (CRON) error (grandchild #10529 failed with exit status 1)



 --END OF NOTIFICATION

When a string from $BAD_WORDS is matched , this message is triggered. 

If you look at 50_syslog_rules.xml you will see the following.

```

<var name="BAD_WORDS">core_dumped|failure|error|attack|bad |illegal |denied|refused|unauthorized|fatal|failed|Segmentation Fault|Corrupted</var>

```This should give you a hint as to what to look for. My guess is "failed" and "error" triggered it. I would say false positive, but double check whatever cron is trying to run.

---

### Post by drifting on 2011-09-07
Spot on, thanks ever so much. Seems that I had some leftovers, well I assume they were Myth-Backend jobs, removed all those and the problems has gone.

Regards Paul

---

### Post by Dangertux on 2011-09-07
Glad it helped :-)

---

