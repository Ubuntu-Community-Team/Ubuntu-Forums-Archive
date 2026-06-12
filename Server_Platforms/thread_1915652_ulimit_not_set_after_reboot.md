---
title: "ulimit not set after reboot"
date: 2012-01-26
forum: Server Platforms
---

### Post by clubbing80s on 2012-01-26
Hi.

I have set the ulimit in /etc/security/limits.conf as follows :

* hard nofile 60000
* soft nofile 20000

rebooted and it is not reflected in ulimit -a 

core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

How do I resolve this as this is causing issues with backups ?

Runing 10.10 LTS x86_64

Thanks

---

### Post by ruffEdgz on 2012-01-26
Did you make sure that pam_limits is enabled in the /etc/pam.d/login file?

Read the man page on pam_limits to understand it better and the example talks about placing the pam_limits.so as a required option for logging in:

[http://manpages.ubuntu.com/manpages/hardy/man8/pam_limits.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_limits.8.html)

Hope this helps.

---

### Post by clubbing80s on 2012-01-26
> **ruffEdgz said:**
> Did you make sure that pam_limits is enabled in the /etc/pam.d/login file?

Read the man page on pam_limits to understand it better and the example talks about placing the pam_limits.so as a required option for logging in:

[http://manpages.ubuntu.com/manpages/hardy/man8/pam_limits.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_limits.8.html)

Hope this helps.

Thanks for your response.  

its in by default 

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

from what I can tell.

Thanks

---

### Post by ruffEdgz on 2012-01-26
> **clubbing80s said:**
> Thanks for your response.  

its in by default 

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

from what I can tell.

Thanks

That is good to know. Are the users local to the system or are they logging in through another means (LDAP, Kerbeos, etc..).

You could always try and add the line below to the /etc/pam.d/common-session file:
```
session    required   pam_limits.so
```
You want to make sure its placed above the other session variables.

Hope that helps.

---

### Post by clubbing80s on 2012-01-26
> **ruffEdgz said:**
> That is good to know. Are the users local to the system or are they logging in through another means (LDAP, Kerbeos, etc..).

You could always try and add the line below to the /etc/pam.d/common-session file:
```
session    required   pam_limits.so
```You want to make sure its placed above the other session variables.

Hope that helps.

ok. I did have it in /etc/pam.d/common-session as well at the start. but it was at the bottom. So that maybe the problem 

Thanks

---

### Post by zete on 2012-08-27
Hi I recently installed ubuntu 12.04 and I am having trouble permanently setting ulimits to what I want. It does it temporarily but even that does not solve the memory problem. I cant open ardour, jack or any other software and watch a video at the same time... please help .. I have searched endlessly and cant find what I am looking for...Thanks

Steph

---

### Post by zete on 2012-08-27
This is what it is set to:

core file size (blocks, -c) 0
data seg size (kbytes, -d) unlimited
scheduling priority (-e) 0
file size (blocks, -f) unlimited
pending signals (-i) 21848
max locked memory (kbytes, -l) 64
max memory size (kbytes, -m) unlimited
open files (-n) 1024
pipe size (512 bytes, -p) 8
POSIX message queues (bytes, -q) 819200
real-time priority (-r) 0
stack size (kbytes, -s) 8192
cpu time (seconds, -t) unlimited
max user processes (-u) 21848
virtual memory (kbytes, -v) unlimited
file locks (-x) unlimited
root@steph-Aspire-7736Z:~# 

This is what I want:
core file size (blocks, -c) 0
data seg size (kbytes, -d) unlimited
scheduling priority (-e) 0
file size (blocks, -f) unlimited
pending signals (-i) 21848
max locked memory (kbytes, -l) 64
max memory size (kbytes, -m) unlimited
open files (-n) 90000
pipe size (512 bytes, -p) 8
POSIX message queues (bytes, -q) 819200
real-time priority (-r) 0
stack size (kbytes, -s) 8192
cpu time (seconds, -t) unlimited
max user processes (-u) unlimited
virtual memory (kbytes, -v) unlimited
file locks (-x) unlimited

I need max user process and open files to be changed permanently

Thanks

Steph

---

