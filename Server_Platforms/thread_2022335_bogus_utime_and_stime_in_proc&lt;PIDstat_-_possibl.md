---
title: "bogus utime and stime in /proc/&lt;PID/stat - possibly related to fs/proc/array.c"
date: 2012-07-10
forum: Server Platforms
---

### Post by alecm3 on 2012-07-10
I administer a large number of servers, and I have this problem only with Ubuntu 10.04 LTS: I run a server under normal load (say load average 3.0 on an 8-core server). The "top" command shows processes taking certain % of CPU that cause this load average: say

```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
11008 mysql     20   0 25.9g  22g 5496 S   67 76.0 643539:38 mysqld  
```

```
ps -o pcpu,pid -p11008
%CPU   PID
53.1 11008
```
, everything is consistent.

The all of the sudden, the process causing the load average disappears from "top", but the process continues to run normally (albeit with a slight performance decrease), and the system load average becomes somewhat higher. The output of ps -o pcpu becomes bogus:

```
# ps -o pcpu,pid -p11008
%CPU      PID
317910278 1587
```
This happened to at least 5 different severs (different brand new IBM System X hardware), each running different software: one httpd 2.2, one mysqld 5.1, and one Twisted Python TCP servers. Each time the kernel was between 2.6.32-32-server and 2.6.32-40-server. I updated some machines to 2.6.32-41-server, and it has not happened on those yet, but the bug is rare (once every 60 days or so).

This is from an affected machine:

```
top - 10:39:06 up 73 days, 17:57,  3 users,  load average: 6.62, 5.60, 5.34
Tasks: 207 total,   2 running, 205 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.4%us, 18.0%sy,  0.0%ni, 66.3%id,  4.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  74341464k total, 71985004k used,  2356460k free,   236456k buffers
Swap:  3906552k total,      328k used,  3906224k free, 24838212k cached

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                
805 root      20   0     0    0    0 S    3  0.0   1493:09 fct0-worker                                                            
982 root      20   0     0    0    0 S    1  0.0 111:35.05 fioa-data-groom                                                        
914 root      20   0     0    0    0 S    0  0.0 884:42.71 fct1-worker                                                            
1068 root      20   0 19364 1496 1060 R    0  0.0   0:00.02 top
```             

Nothing causing high load is showing on top, but I have two highly loaded mysqld instances on it, that suddenly show crazy %CPU:

```
#ps -o pcpu,pid,cmd -p1587
%CPU   PID CMD
317713124 1587 /nail/encap/mysql-5.1.60/libexec/mysqld
```
and

```
#ps -o pcpu,pid,cmd -p1624
%CPU   PID CMD
2802  1624 /nail/encap/mysql-5.1.60/libexec/mysqld
```
Here are the numbers from

```
 # cat /proc/1587/stat
```
 1587 (mysqld) S 1212 1088 1088 0 -1 4202752 14307313 0 162 0 **85773299069     4611685932654088833** 0 0 20 0 52 0 3549 27255418880 5483524 18446744073709551615 4194304 11111617 140733749236976 140733749235984 8858659 0 552967 4102 26345 18446744073709551615 0 0 17 5 0 0 0 0 0

The 14th and 15th numbers according to

man proc and fs/proc/array.c are supposed to be:

utime %lu   Amount of time that this process has been scheduled in user mode, measured in clock ticks  (divide  by
                      sysconf(_SC_CLK_TCK).   This  includes  guest  time, guest_time (time spent running a virtual CPU, see
                      below), so that applications that are not aware of the guest time field do not  lose  that  time  from
                      their calculations.

stime %lu   Amount of time that this process has been scheduled in kernel mode, measured in clock ticks (divide by
                      sysconf(_SC_CLK_TCK).

On a normal server, these numbers 13 orders of magnitude smaller and they are advancing by about 10 per sec. On a buggy server, these numbers are stuck at a ridiculously high value like 4611685932654088833, and they are not changing.

Has anyone encountered this bug?

---

