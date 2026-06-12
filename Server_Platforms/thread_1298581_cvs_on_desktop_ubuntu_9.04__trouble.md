---
title: "cvs on desktop ubuntu 9.04  trouble?"
date: 2009-10-23
forum: Server Platforms
---

### Post by yilin on 2009-10-23
Well, the trouble is that the ubuntu 9.04 documentation looks quite different than the real situation, and I really need your help!!!

Here is my situation:

apt-get install cvs  ..... ok ....very smooth
apt-get install xinetd  ..........very smooth

cvs -d /home/developer/repository/cvs init

root@workbook:~# ls -l /home/developer/repository/cvs
total 4
drwxrwxr-x 3 root src 4096 2009-10-22 18:55 CVSROOT

root@workbook:~# cat /etc/cvs-cron.conf 
ROT_HIST="no"
# Please use : to separate the repositories=
REPOS="/home/developer/repository/cvs"
ROTKEEP="no"

root@workbook:~# cat /etc/cvs-pserver.conf 
CVS_PSERV_REPOS="/home/developer/repository/cvs"
CVS_PSERV_LIMIT_MEM=hard
CVS_PSERV_LIMIT_DATA=hard
CVS_PSERV_LIMIT_CORE=0
CVS_PSERV_LIMIT_CPU=hard

root@workbook:/etc/xinetd.d# cat /etc/xinetd.d/cvspserver 
service cvspserver
{
     port = 2401
     socket_type = stream
     protocol = tcp
     user = root
     wait = no
     type = UNLISTED
     server = /usr/bin/cvs
     server_args = -f --allow-root /home/developer/repository/cvs pserver
     disable = no
}


BUT:
```
root@workbook:/etc/xinetd.d# /etc/init.d/xinetd start
 * Starting internet superserver xinetd                 [fail] 
```s


I know my system is NOt ubuntu server but desktop/laptop
but how different is for the server and the desktop with respect to cvs?

Thanks!

---

### Post by yilin on 2009-10-24
One thing clear is that it's more of the xinetd problem than cvs problem.
I changed back the default repository path, didn't help: got the same error

---

### Post by yilin on 2009-11-18
Anyone ever get cvs pserver work on ubuntu 9.10 desktop?

---

### Post by TGMONKHOUSE on 2009-12-03
Instead of using "/etc/init.d/xinetd start"
 
trying using "/etc/init.d/xinetd reload"
 
this solved my problem!

---

### Post by odab on 2010-03-07
tgmonkhouse,

You prince among men! Cured my frustration, many thanks.

Cheers, Odab

---

