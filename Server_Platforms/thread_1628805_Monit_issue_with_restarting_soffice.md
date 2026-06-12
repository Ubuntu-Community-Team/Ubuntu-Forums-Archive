---
title: "Monit issue with restarting soffice"
date: 2010-11-23
forum: Server Platforms
---

### Post by feighen on 2010-11-23
Ubuntu version: Ubuntu 10.04.1 LTS \n \l
                        2.6.32-25-server #45-Ubuntu SMP x86_64 GNU/Linux
Monit version: monit -V
                     This is monit version 5.0.3

Problem: Monitoring cpu usage does not work

I can't get monitoring CPU usage to work.

Excerpt from /etc/monit/monitrc
```

check process soffice with pidfile /var/run/soffice.pid
    group openoffice
    start program = "/etc/init.d/soffice start"
    stop program = "/etc/init.d/soffice stop"
    # if loadavg(5min) greater than 80.0 for 1 cycles then restart
    # Added by Feighen 2010-11-08 16h27
    # if cpu is greater than 65% for 3 cycles then restart 
    if cpu usage > 75% for 3 cycles then restart # Added by Feighen 2010-11-22 14h45

```So we have an issue with soffice that it is using 100% of CPU. So to try and combat it we have enabled a monit rule to check to see if cpu usage is greater than a set percent for 3 cycles (6minutes as daemon is set to 120), but it is not working as expected. I will watch as soffice.bin sits at 100% of CPU for 30minutes processing documents and no monit  restart. I know that there is a bug report filed against soffice.bin. Will look around to see if I can find the bug number again. 

monit -t shows that the config file syntax is OK

Not too sure if there is anything else you need from me to help

Still in process for testing on my side
1) Log files checked to see if there is an issue
2) running  sudo monit status after 6 minute barrier for soffice.bin
3) Writing trivial test on local machine to see if I can get a process to restart via monitrc file

---

### Post by feighen on 2010-11-24
Log files checked and I can't find anything in either
/var/log/syslog or
/var/log/daemon.log

sudo more /var/log/daemon.log | grep soffice
Nov 22 13:48:25 bobafett monit[31314]: restart service 'soffice' on user request

Nothing in /var/log/syslog

---

### Post by feighen on 2010-11-24
Something I only noticed now

running a top shows that nginx is using 8% of CPU

but monit status shows

Process 'nginx'
  status                            running
  monitoring status                 monitored
  pid                               1532
  parent pid                        1
  uptime                            1h 20m 
  children                          1
  memory kilobytes                  1124
  memory kilobytes total            6328
  memory percent                    0.0%
  memory percent total              0.1%
  cpu percent                       0.0%
  cpu percent total                 3.2%
  port response time                0.000s to 127.0.0.1:80 [DEFAULT via TCP]
  data collected                    Wed Nov 24 16:39:21 2010

Not too sure if this is what is causing soffice not to restart correctly. Also not too sure how monit gathers the information on CPU usage and if it different to how top gathers info or whether the results are being skewed by having to switch between terminal tabs. But at least I have more to go on now

---

### Post by feighen on 2010-11-25
finally got soffice.bin to use 100% in top again today and checked monit status. Was only showing cpu usage of ~24%. So the rule isn't broken just will never be run as the usage seems likely not to be met.

Marking thread as resolved

---

