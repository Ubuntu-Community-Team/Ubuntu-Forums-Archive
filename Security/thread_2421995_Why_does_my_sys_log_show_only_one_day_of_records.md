---
title: "Why does my sys log show only one day of records?"
date: 2019-06-30
forum: Security
---

### Post by linux-user-0987 on 2019-06-30
When I open my sys log the first line every day is : Jun 30 07:35:03 My-PC anacron[560]: Job `cron.daily' terminated

I asked a question before and I was told the sys log keeps records for a long time. Is there some other way to view them?

2) I have read that if a system gets hacked the best thing to do is to reinstall the OS. But is there some way to find out if a system is getting unwanted access? **Some way that you can be sure?** What if a scan using clam antivirus does not show anything?

---

### Post by kpatz on 2019-06-30
Logrotate rotates the logs daily so /var/log/syslog contains today's entries, /var/log/syslog.1 contains yesterday's, then older ones are gzipped, so syslog.2.gz will be 2 days ago, etc.

Depending on when the system is booted logrotate may run at midnight, or some time after.

---

### Post by uRock on 2019-06-30
> **linux-user-0987 said:**
> When I open my sys log the first line every day is : Jun 30 07:35:03 My-PC anacron[560]: ..... I have read that if a system gets hacked the best thing to do is to reinstall the OS. But is there some way to find out if a system is getting unwanted access? **Some way that you can be sure?** What if a scan using clam antivirus does not show anything?

Reinstalling is the best advice for handling a system that has been compromised. Clam AV only detects Windows viruses. What makes you think your system might have been compromised?

---

### Post by TheFu on 2019-07-19
The types of how many and how large the logs can get is all configurable.  Before systemd, it was 100% controlled by logrotate.  Since systemd, I've seen the controls become less clear.  On my 16.04 system, the boot logs are never written to disk. They are held in RAM unless you chnage the configuration to ask for them to held longer.  Very frustrating when we need to troubleshoot a boot issue only to find that the default boot logs aren't retained.  I've since changed my settings to write logs and flush them to disk at least every 2 minutes. 

 In the olden days, pre-systemd, the logrotate configs were in /etc/logrotate.d/ and fairly easy to understand.

---

