---
title: "Why does smbd show up twice in ps -A"
date: 2008-09-21
forum: Server Platforms
---

### Post by wpittman on 2008-09-21
Hello, When I start samba the smbd daemon is listed twice in my ps -A listing. Is this normal, or have I messed up somewhere?  Thanks in Advance ... Wes

root@wesley-desktop:/home/wesley# ps -A | grep smbd
18740 ?        00:00:00 smbd
18744 ?        00:00:00 smbd
root@wesley-desktop:/home/wesley# kill 18740
root@wesley-desktop:/home/wesley# kill 18744
bash: kill: (18744) - No such process
root@wesley-desktop:/home/wesley# ps -A | grep nmbd
18738 ?        00:00:00 nmbd
root@wesley-desktop:/home/wesley# kill 18738
root@wesley-desktop:/home/wesley# /etc/init.d/samba start
 * Starting Samba daemons                                                [ OK ] 
root@wesley-desktop:/home/wesley# ps -A | grep smbd
19927 ?        00:00:00 smbd
19931 ?        00:00:00 smbd
root@wesley-desktop:/home/wesley#

---

### Post by bab1 on 2008-09-21
It's a normal part of the daemon process.  The smbd daemon forks (spawns) a child process to handle each incoming request.

---

### Post by wpittman on 2008-09-21
Thanks for the Info.  Wes.

---

