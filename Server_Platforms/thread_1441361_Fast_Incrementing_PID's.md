---
title: "Fast Incrementing PID's"
date: 2010-03-28
forum: Server Platforms
---

### Post by goodlife on 2010-03-28
Hi 

I have a virtual private server running Ubuntu 8.04 LTS that is slow to respond and has even crashed at one point.

I have checked the memory and CPU usage, using 'uptime', 'free' and 'top' and have found that there is no shortage there. Neither is there any shortage of disk space.

I have noticed, by repeatedly using the 'ps' command, that the process numbers are cycling very fast and wondered whether this could be causing a constraint. On my home computer and on a different VPS, issuing the 'ps' command twice in succession usually results in a increment of one. On this server it is always more than one. 

To test this I have stopped all non essential services and have found it still to be the case. 

The results of 'ps aux' in this minimalist state are as follows:-

-------------------------------------------------------------------

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  10368   772 ?        Ss   Mar28   0:00 init [2]         
root      7726  0.0  0.0  67960  2924 ?        Ss   00:15   0:00 sshd: root@pts/0 
root      7750  0.0  0.0  18828  1992 pts/0    Ss   00:15   0:00 -bash
root     12084  0.0  0.0  15052  1076 pts/0    R+   00:16   0:00 ps aux
root     29993  0.0  0.0  50904  1156 ?        Ss   Mar28   0:00 /usr/sbin/sshd

-------------------------------------------------------------------


By timing it over longer periods I have found that the PID number returned by ps increments by between approximately 50 and 250 per second, even with only these few essential services running.

I installed 'acct' to try to log where thest processes were coming from but when I issued the command 'accton /var/log/pacct' to get it to log process details in the existing directory /var/log/pacct it responded 'accton: Operation not permitted' I assume that this means that acct support is not compiled into the kernel. I do not know how big a job this would be to provide as I have never recompiled a kernel.

Has anyone come across this before or have any ideas why the PIDs could be incrementing so fast when only even minimal processes are running?

The OS version is : 2.6.18-164.2.1.el5.028stab066.10

---

### Post by gombadi on 2010-03-28
> 
Has anyone come across this before or have any ideas why the PIDs could be incrementing so fast when only even minimal processes are running?

The OS version is : 2.6.18-164.2.1.el5.028stab066.10 


That kernel looks like an OpenVZ or Virtuozzo kernel. It uses one kernel for the whole system with multiple virtual environments running on the one kernel.

My guess is that one of the other VPS's on the hardware is creating a large number of processes and that is what you are seeing.

Ask your hosting company to investigate the load on the hardware node.

---

### Post by goodlife on 2010-03-28
Thanks for the response. It's always good to find out when things seem strange. What you say makes a lot of sense so I'll follow up my VPS hosting company.

---

