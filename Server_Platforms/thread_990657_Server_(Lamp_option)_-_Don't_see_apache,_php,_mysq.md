---
title: "Server (Lamp option) - Don't see apache, php, mysql"
date: 2008-11-22
forum: Server Platforms
---

### Post by iroy2000 on 2008-11-22
Hi all, 

Thanks for any help in advance.

I have installed Ubuntu server 8.04 - LAMP option.

But when I try to look for 

apache, mysql and php, I don't think it is pre-installed.

So do I need to install them manually?

For example, I try to run mysql

The program 'mysql' is currently not installed.  You can install it by typing:
sudo apt-get install mysql-client-5.0

---

### Post by iroy2000 on 2008-11-23
When I tried tasksel, I didn't see LAMP option is checked, so I tried to installed it again using tasksel, and I get an error  (failure appitude 100... something like that).

I think it may be related to this bug?
[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134)


Anyway, I installed them one by one, and it works now.

=======

---

### Post by cariboo on 2008-11-23
It would help a lot more if you could paste the real error message, instead of:

> (failure appitude 100... something like that).


You won't see any indication that LAMP is installed, the best way is to run:

```
ps ax
```

If you have all the services installed you should get an output something like this:

```
4519 ?        Sl     7:13 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/my
 4521 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 4994 ?        Ss     0:00 /usr/sbin/exim4 -bd -q30m
 5078 ?        S      0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/s
 5133 ?        S<     0:00 [lockd]
 5134 ?        S<     0:00 [nfsd4]
 5135 ?        S<     0:00 [nfsd]
 5136 ?        S<     0:00 [nfsd]
 5137 ?        S<     0:00 [nfsd]
 5138 ?        S<     0:00 [nfsd]
 5139 ?        S<     0:00 [nfsd]
 5140 ?        S<     0:00 [nfsd]
 5141 ?        S<     0:00 [nfsd]
 5142 ?        S<     0:00 [nfsd]
 5146 ?        Ss     0:00 /usr/sbin/rpc.mountd
 5191 ?        Ss     0:01 /usr/sbin/winbindd
 5208 ?        S      0:00 /usr/sbin/winbindd
 5209 ?        Ss     0:45 /usr/sbin/hald
 5212 ?        Ssl    6:59 /usr/sbin/console-kit-daemon
 5275 ?        S      0:05 hald-runner
 5294 ?        S      0:00 hald-addon-input: Listening on /dev/input/event4 /dev
 5297 ?        S      0:14 hald-addon-hid-ups: listening on /dev/usb/hiddev0
 5306 ?        S      0:00 hald-addon-acpi: listening on acpi kernel interface /
 5315 ?        S      0:45 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 5337 ?        Ssl    0:25 /sbin/apcupsd
 5353 ?        Ss     0:02 proftpd: (accepting connections)
 5366 ?        Ss     0:00 /usr/sbin/atd
 5391 ?        Ss     0:02 /usr/sbin/cron
 5411 ?        Ss     0:10 /usr/sbin/apache2 -k start
 5429 ?        Ss     0:14 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webm
 5840 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5884 ?        S<     0:51 [kjournald]
 5916 ?        S      0:00 /usr/sbin/winbindd
 5917 ?        S      0:00 /usr/sbin/winbindd
 6817 ?        Ssl    0:05 /usr/sbin/cupsd
12394 ?        Ss     0:00 /usr/sbin/uptimed
12542 ?        S      0:00 /usr/sbin/apache2 -k start
12543 ?        S      0:00 /usr/sbin/apache2 -k start
12544 ?        S      0:00 /usr/sbin/apache2 -k start
12545 ?        S      0:00 /usr/sbin/apache2 -k start
12546 ?        S      0:00 /usr/sbin/apache2 -k start
14099 ?        S      0:04 [pdflush]
14744 ?        S      0:01 [pdflush]
22463 ?        Ss     0:00 /usr/sbin/sshd
23128 ?        Ss     0:00 sshd: jim [priv]
23135 ?        S      0:00 sshd: jim@pts/0 
23138 pts/0    Ss     0:00 -bash
23193 pts/0    R+     0:00 ps ax
31927 ?        S      0:02 python /usr/sbin/denyhosts --daemon --config=/etc/denyhosts

```

Jim

---

