---
title: "starting exim  problem"
date: 2009-03-13
forum: Server Platforms
---

### Post by pdc124 on 2009-03-13
I want to use exim - ive got a full working config on A.N.other OS.

ive installed it, and run the config.

ive got log files but no messages when try to start/stop the daemon 

root@server:/etc/exim4# ls -la /var/log/exim4/
total 8
drwxr-s---  2 Debian-exim adm  4096 2009-03-13 17:28 .
drwxr-xr-x 15 root        root 4096 2009-03-13 17:28 ..
root@server:/etc/exim4# /etc/init.d/exim4 status
root@server:/etc/exim4# /etc/init.d/exim4 stop
root@server:/etc/exim4# /etc/init.d/exim4 start


When I *think* ive started it , it isnt running 

root@server:/etc/exim4# ps -A | grep x
 1518 ?        00:00:00 ata_aux
root@server:/etc/exim4# ps -A | grep ex
root@server:/etc/exim4#   

so what is missing ?

---

### Post by brian_p on 2009-03-13
> **pdc124 said:**
> 

so what is missing ?

What does

```
exim -bV
```

say?

---

### Post by pdc124 on 2009-03-14
root@server:/backups# exim -bv
The program 'exim' can be found in the following packages:
 * exim4-daemon-heavy
 * exim4-daemon-light
Try: apt-get install <selected package>
bash: exim: command not found
root@server:/backups#

---

### Post by pdc124 on 2009-03-14
root@server:/backups# apt-get install exim4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  exim4-daemon-light
The following NEW packages will be installed:
  exim4 exim4-daemon-light
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 423kB of archives.
After this operation, 975kB of additional disk space will be used.
Do you want to continue [Y/n]? y

and i seems to install it. no idea what it installed first time

Trying to run an init script gave me no errors

---

### Post by pdc124 on 2009-03-19
so somethign stragne is happening. 
Ive got fetchmail to retrieve my POP3 mail, which passses it on to exim for local delivery , which fails 

each message generates this fetchmail: can't even send to pcy!

exim -bv says this 
root@server:/etc/exim4/conf.d/acl# exim -bv
The program 'exim' can be found in the following packages:
 * exim4-daemon-heavy
 * exim4-daemon-light
Try: apt-get install <selected package>
bash: exim: command not found
root@server:/etc/exim4/conf.d/acl#               

sop which do i need ? whats the difference ?

---

