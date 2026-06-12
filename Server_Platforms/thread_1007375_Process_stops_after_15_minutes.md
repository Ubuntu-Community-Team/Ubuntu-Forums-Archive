---
title: "Process stops after 15 minutes"
date: 2008-12-10
forum: Server Platforms
---

### Post by Agner on 2008-12-10
I want to run some number-crunching applications in the background on my server to use the idle time. But the process always stops after 15 minutes.

I start the process from a SSH login shell with a command like, f.eks.:

nohup nice -n5 ./myprogram > output.txt &

The program runs for 15 minutes and then it stops. ps shows:
  PID TTY          TIME CMD
 5813 pts/0    00:00:00 bash
 5966 pts/0    00:15:00 1.out
 8411 pts/0    00:00:00 ps

Same result without nohup and nice.

ulimit -a says cpu time is unlimited. 
I have tried to change /etc/security/limits.conf and reboot. ulimit reflects the change, but the process still stops after 15 minutes even though the limit I have set is much higher.

I found the following page on help search in Webmin:
Resource Limits
This page allows you to define limits on CPU and memory use that apply to this virtual server and all sub-servers. Limits apply to both PHP scripts, and commands run via an SSH login....

This is apparently under virtual server, but I can't find any such page in webmin.

System information:
Ubuntu Linux 8.04.1, Linux 2.6.24-22-server on x86_64, webmin 1.430

Somebody, please help

---

