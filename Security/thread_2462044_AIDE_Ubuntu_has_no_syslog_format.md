---
title: "AIDE Ubuntu has no syslog_format?"
date: 2021-05-12
forum: Security
---

### Post by jauling on 2021-05-12
I'm setting up AIDE checks on my RHEL and Ubuntu systems and logging output to syslog. In RHEL, there is a convenient option called **syslog_format** which prints changes on a per line basis. I checked the AIDE package in both Ubuntu 14.04 as well as 20.04, and neither have this option. I couldn't find a pertinent changelog in the source to point to why this was removed, but it exists in AIDE 0.14 and 0.15.1 (versions in RHEL6 and RHEL7), but it seems the 0.16.x releases in Ubuntu don't have this.

Anyone know if it's possible to replicate this logging format without this option?

```
       syslog_format
              Valid  values  are yes,true,no and false. This option enables new syslog format which is suitable for
              logging. Every change is logged as one simple line. This option changes verbose level to 0 and prints
              everything that was changed. It is suggested to use this option with "report_url=syslog:...". Default
              value is "false/no".  Maximum size of message is 1KB which is limitation of syslog call.  If  message
              is  greater  than  limit, message will be truncated.  Option summarize_changes has no impact for this
              format.


              Output always starts with:
              "AIDE found differences between database and filesystem!!"
              And it is followed by summary:
              summary;total_number_of_files=1000;added_files=0;removed_files=0;changed_files=1
              And finally there are logs about changes:
              dir=/usr/sbin;Mtime_old=0000-00-00 00:00:00;Mtime_new=0000-00-00 00:00:00;...
```

---

