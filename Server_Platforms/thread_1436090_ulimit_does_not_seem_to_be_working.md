---
title: "ulimit does not seem to be working"
date: 2010-03-22
forum: Server Platforms
---

### Post by amuthan on 2010-03-22
[SIZE=2]Hi,
            We are using a hadoop server & we dont want the server memory to overload. So, I have set the ulimit for max memory size and for some time it was working fine but memory was overloading before EOD. I came to know about soft & hard limits and set the hard limit for the maximum memory size in /etc/security/limits.conf file. But, the limits were not shown in ulimit -a command ouput. 

So, I restarted the server. Then, the limit was shown in the ulimit command output. But, memory is still getting overloaded as you can see the memory used is more than the limit set. Anyone kndly suggest me on this issue.[/SIZE]

[SIZE=2][menon@265430-vm1 ~]$ top

top - 09:55:30 up  5:37,  1 user,  load average: 0.04, 0.03, 0.00
Tasks: 117 total,   1 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.7%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3866400k total,  3743456k used,   122944k free,   123100k buffers
Swap:  2096472k total,       88k used,  2096384k free,  1078780k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2078 root      15   0     0    0    0 S  1.0  0.0   0:56.78 vmmemctl
 2108 root      15   0 10672  952  740 S  0.3  0.0   0:16.74 vmware-guestd
 4288 menon   24   0 1412m  79m  10m S  0.3  2.1   0:23.97 java
18914 menon   15   0 12740 1092  820 R  0.3  0.0   0:00.01 top
    1 root      15   0 10348  708  592 S  0.0  0.0   0:00.34 init
    2 root      RT  -5     0    0    0 S  0.0  0.0   0:00.11 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.11 migration/1
    5 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/1
    6 root      11  -5     0    0    0 S  0.0  0.0   0:19.51 events/0
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/1
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
   39 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
   44 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
   45 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/1
   46 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  103 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue/0
[menon@265430-vm1 ~]$ ulimit -Hm
3479700
[menon@265430-vm1 ~]$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 30720
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) 3479700
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 10240
cpu time               (seconds, -t) unlimited
max user processes              (-u) 30720
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
[/SIZE][SIZE=4]
               I have also given the contents of limits.conf file. Anyone kndly suggest me on this issue.[/SIZE]

[SIZE=2]root  # cat /etc/security/limits.conf
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to
#        - rtprio - max realtime priority
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
*                hard    rss             3479760
@menon         hard    rss             3479700
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#@student        -       maxlogins       4

# End of file


I 
[/SIZE]

---

### Post by 164747 on 2010-04-14
I am having similar problems myself. This is what I _think_ (I dont know below for sure)

* I think ulimit is only valid for users logged in.
* A user not logged in is not affected by limits.conf
* A user can log in in many ways (cron, ssh, login, su, ...?), to activate limits for a user, make
 sure relevant row in in relvant file under /etc/pam.d/ is not commented out

I try to find a safeguard, that some process under apache does not hang my server. I think this might be impossible using limits.conf (since www-data is not logged in). For apache have been trying RLimitMEM but that does not seem to work.

---

