---
title: "Start saslauthd fail"
date: 2008-05-29
forum: Server Platforms
---

### Post by satimis on 2008-05-29
Hi folks,


Ubuntu 6.05 drake amd64


$ sudo /etc/init.d/saslauthd start```

Password:
Starting SASL Authentication Daemon: (failed).

```


$ tail /var/log/daemon.log```

May 30 00:00:01 lampserver squid[4311]:         0 Objects expired. 
May 30 00:00:01 lampserver squid[4311]:         0 Objects cancelled. 
May 30 00:00:01 lampserver squid[4311]:         0 Duplicate URLs purged. 
May 30 00:00:01 lampserver squid[4311]:         0 Swapfile clashes avoided. 
May 30 00:00:01 lampserver squid[4311]:   Took 0.7 seconds (   0.0 objects/sec). 
May 30 00:00:01 lampserver squid[4311]: Beginning Validation Procedure 
May 30 00:00:01 lampserver squid[4311]:   Completed Validation Procedure 
May 30 00:00:01 lampserver squid[4311]:   Validated 0 Entries 
May 30 00:00:01 lampserver squid[4311]:   store_swap_size = 0k 
May 30 00:00:01 lampserver squid[4311]: storeLateRelease: released 0 objects 

```
Please advise where shall I check and how to fix the problem.


TIA


B.R.
satimis

---

### Post by satimis on 2008-05-30
Hi


I found my mistake on running;


$ sudo sh -x /etc/init.d/saslauthd start```

+ NAME=saslauthd
+ DAEMON=/usr/sbin/saslauthd
+ DESC='SASL Authentication Daemon'
+ DEFAULTS=/etc/default/saslauthd
+ PWDIR=/var/run/saslauthd
+ PIDFILE=/var/spool/postfix/var/run//saslauthd.pid
+ test -f /usr/sbin/saslauthd
+ '[' -e /etc/default/saslauthd ']'
+ . /etc/default/saslauthd
++ START=yes
++ PARAMS='-m /var/spool/postfix/var/run/saslauthd -r'
++ MECHANISMS=pam
+ '[' yes '!=' yes ']'
+ '[' xpam = x ']'
+ PARAMS='-m /var/spool/postfix/var/run/saslauthd -r -a pam'
+ START='--start --quiet --pidfile /var/spool/postfix/var/run//saslauthd.pid --startas /usr/sbin/saslauthd --name saslauthd -- -m /var/spool/postfix/v
ar/run/saslauthd -r -a pam'
+ case "${1}" in
+ echo -n 'Starting SASL Authentication Daemon: '
Starting SASL Authentication Daemon: ++ dpkg-statoverride --list /var/run/saslauthd
+ dir='root sasl 710 /var/run/saslauthd'
+ test -z 'root sasl 710 /var/run/saslauthd'
+ createdir root sasl 710 /var/run/saslauthd
+ '[' -d /var/run/saslauthd ']'
+ chown -c -h root:sasl /var/run/saslauthd
+ chmod -c 710 /var/run/saslauthd
+ start-stop-daemon --start --quiet --pidfile /var/spool/postfix/var/run//saslauthd.pid --startas /usr/sbin/saslauthd --name saslauthd -- -m /var/spoo
l/postfix/var/run/saslauthd -r -a pam
+ start-stop-daemon --test --start --quiet --pidfile /var/spool/postfix/var/run//saslauthd.pid --startas /usr/sbin/saslauthd --name saslauthd -- -m /v
ar/spool/postfix/var/run/saslauthd -r -a pam
+ echo '(failed).'
(failed).
+ exit 1

```
There is a problem on;```

/var/spool/postfix/var/run//saslauthd.pid --startas 

```
// before saslauthd.pid


Then I found a typo on /etc/init.d/saslauthd on following line```

PIDFILE="/var/spool/postfix/var/run/${NANE}/saslauthd.pid"

```
After changing;
NANE

to;
NAME


$ sudo /etc/init.d/saslauthd restart```

Stopping SASL Authentication Daemon: (not running).
Starting SASL Authentication Daemon: saslauthd.

```
My problem gone.


Now I have to concentrate solving the problem on "login SM"


B.R.
satimis

---

