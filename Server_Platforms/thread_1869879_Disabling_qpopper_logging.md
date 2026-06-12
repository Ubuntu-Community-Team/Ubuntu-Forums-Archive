---
title: "Disabling qpopper logging"
date: 2011-10-26
forum: Server Platforms
---

### Post by awacs on 2011-10-26
I'd like to hide qpopper messages. I put 
set log-facility             = local7
in /etc/qpopper.conf

and 
local7.none                     -/var/log/syslog
local7.*                        -/var/log/popper.log

*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none,user.warning,local7.none         -/var/log/messages

and I'm still getting popper messages in syslog (but not in messages). What am I doing wrong?

---

