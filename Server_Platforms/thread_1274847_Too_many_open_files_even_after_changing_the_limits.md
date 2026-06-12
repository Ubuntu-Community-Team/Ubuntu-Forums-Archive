---
title: "Too many open files even after changing the limits.conf"
date: 2009-09-25
forum: Server Platforms
---

### Post by dr-alves on 2009-09-25
Hi

 I'm using ubuntu karmic without a hitch so far.
 My box has the desktop installed but is mostly a server box (was installed as such at first) and that's why i'm posting here.
 One of the things I run in my box is jboss with several applications deployed (jira, hudson, confluence) but I'm getting a weird error

 Jboss fails to deploy some applications due to "too many open files". When I first saw this I thought it would be simple to solve, just needed to up ulimit, now I'm not so sure.

I increased the limit to all user to 65536 (at first I had only * but then i decided to get creative):

```

*               soft    nofile          65536
*               hard    nofile          65536
jboss           soft    nofile          65536
jboss           hard    nofile          65536
root            soft    nofile          65536
root            hard    nofile          65536

```

Also the max limit is high

linux-server:~# cat /proc/sys/fs/file-max 
202989

and the max ever occupied is well below the limit:
cat /proc/sys/fs/file-nr
6304	0	202989


all users return the same limit (including the jboss user who initiates the app server):
jboss@linux-server:/home$ ulimit -n
65536


I'm out of ideas and it is hard to find results in google as similar problems are always solved upping ulimit.

Any ideas? 


Regards
David R Alves

---

### Post by dr-alves on 2009-09-28
Shameless bump!

Still need help figuring out this issue.

Anyone?

Cheers
David

---

### Post by dr-alves on 2009-10-08
Still getting this issue.

I've done that i can find on google. All users return 65536 limits and still applications crash due to "too many open files".

Please help!!

---

### Post by Xianath on 2009-10-09
```
for pid in `pidof java`; do echo "$(< /proc/$pid/cmdline)"; egrep 'files|Limit' /proc/$pid/limits; echo "Currently open files: $(ls -1 /proc/$pid/fd | wc -l)"; echo; done
```

Any discrepancy between what you see in your processes and what you've set in limits.conf? You may need to add the following to /etc/pam.d/common-session:

```
session required        pam_limits.so
```

Cheers,
Peter

---

### Post by RafaelSantos on 2009-10-20
I'm having this problem too, I'll try to explain better (but sorry about my awful english):

I have a server running Nginx + Jetty 6 on a Ubuntu Server 8.10 and I'm receiving some error messages of "Too many open files". Since then I'm trying to increase the "nofile" limit without success.

On my */etc/security/limits.conf*:
> *      soft   nofile      2048   
*      hard   nofile      4096
> # grep pam_limits.so *
atd:session    required   pam_limits.so
common-session:session required        pam_limits.so
cron:session    required   pam_limits.so
login:session    required   pam_limits.so
sshd:session    required     pam_limits.so
su:session    required   pam_limits.so
sudo:session required pam_limits.soBut its not working:

> # for pid in `pidof java`; do echo "$(< /proc/$pid/cmdline)"; egrep 'files|Limit' /proc/$pid/limits; echo "Currently open files: $(ls -1 /proc/$pid/fd | wc -l)"; echo; done
/usr/lib/jvm/java-6-sun-1.6.0.14/jre/bin/java-DSTART=/usr/share/jetty6/etc/start.config-Xms512m-Xmx4096m-XX:MaxPermSize=800M-Djava.awt.headless=true-javaagent:/usr/share/jetty6/newrelic/newrelic.jar-Dnewrelic.environment=production-Djetty.home=/usr/share/jetty6-Djava.io.tmpdir=/var/cache/jetty6-jar/usr/share/jetty6/start.jar/etc/jetty6/jetty-logging.xml/etc/jetty6/jetty.xml
Limit                     Soft Limit           Hard Limit           Units     
Max open files            1024                 1024                 files     
Currently open files: 919Any ideas?

---

### Post by RafaelSantos on 2009-10-21
Desperated bump...

I've tried to find some help on google and found more people with the same problem but got no answers. :frown:

---

### Post by stlhrt on 2009-10-27
I have the same problem on ubuntu 8.10 and 9.04.

setting limits in 
```
/etc/security/limits.conf 
/etc/sysctl.conf 

```

when logged in ```
ulimit-n 
```
shows correct limits per user, but after spawnig java process 

```
for pid in `pidof java`; do echo "$(< /proc/$pid/cmdline)"; egrep 'files|Limit' /proc/$pid/limits; echo "Currently open files: $(ls -1 /proc/$pid/fd | wc -l)"; echo; done
```

shows limit 1024

fail :(

---

### Post by stlhrt on 2009-10-27
ok, solved mine problem...
$BEA_HOME/weblogic81/common/bin/commEnv.sh contains calls to ```
ulimit -n **1024
```
hack it and you are set ;) i bet jetty scripts contain something similar

---

