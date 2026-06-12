---
title: "Mail server"
date: 2011-10-06
forum: Server Platforms
---

### Post by bcraig24 on 2011-10-06
I'm totally new to installing a mail server and I need some help please =)

My system is probably full of rubbish configurations now after multiple failed attempts of following tutorials...

I have a static IP and a domain name pointing to my localwebser on my Ubuntu 10.04 system.
I need to setup some type of mail server to be able to activate mail functions in my php.

I've followed many tutorials to install postfix but at the end of it I test the status and get "Postfix is not running" even after commanding it to start...

Pleeeease help! So frustraing.
Let me know what info I need to post up..

/etc/hosts
```
127.0.0.1	localhost.localdomain	localhost
127.0.1.1	ben-server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


/var/log/mail.log:
```

Oct  6 17:40:01 ben-server sm-msp-queue[26386]: My unqualified host name (ben-server) unknown; sleeping for retry
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: unable to qualify my own domain name (ben-server) -- using short name
Oct  6 17:41:01 ben-server sm-mta[26392]: p964f1qe026392: SYSERR(root): collect: Cannot write ./dfp964f1qe026392 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26392]: p964f1qe026392: from=<>, size=5622, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p94NL2H8017112: to=postmaster, delay=1+05:19:58, xdelay=00:00:00, mailer=relay, pri=7954984, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1qe026392 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26393]: p964f1Ix026393: SYSERR(root): collect: Cannot write ./dfp964f1Ix026393 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:01 ben-server sm-mta[26393]: p964f1Ix026393: from=<>, size=3758, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p94JL2aP015957: to=postmaster, delay=1+09:19:58, xdelay=00:00:00, mailer=relay, pri=9033144, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1Ix026393 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:01 ben-server sm-mta[26394]: p964f19u026394: SYSERR(root): collect: Cannot write ./dfp964f19u026394 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26394]: p964f19u026394: from=<>, size=7329, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p930L1qg002969: to=postmaster, delay=3+04:19:58, xdelay=00:00:00, mailer=relay, pri=20646673, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f19u026394 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26395]: p964f1u5026395: SYSERR(root): collect: Cannot write ./dfp964f1u5026395 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26395]: p964f1u5026395: from=<>, size=5447, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p92KL1Ib001766: to=postmaster, delay=3+08:19:59, xdelay=00:00:00, mailer=relay, pri=21724809, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1u5026395 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:02 ben-server sm-mta[26396]: p964f2bd026396: SYSERR(root): collect: Cannot write ./dfp964f2bd026396 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26396]: p964f2bd026396: from=<>, size=2263, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:02 ben-server sm-msp-queue[26386]: p91N11U4027649: to=root, delay=4+05:40:01, xdelay=00:00:00, mailer=relay, pri=27481493, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f2bd026396 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26397]: p964f2dD026397: SYSERR(root): collect: Cannot write ./dfp964f2dD026397 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26397]: p964f2dD026397: from=<root@ben-server>, size=459, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:02 ben-server sm-msp-queue[26386]: p91ImH4g026427: to=root, ctladdr=root (0/0), delay=4+09:52:45, xdelay=00:00:00, mailer=relay, pri=28650217, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f2dD026397 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:50:23 ben-server postfix/master[27177]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 17:53:16 ben-server postfix/master[27472]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 17:57:12 ben-server postfix/master[27606]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:00:18 ben-server postfix/postfix-script[27628]: the Postfix mail system is not running
Oct  6 18:00:24 ben-server postfix/postfix-script[27732]: starting the Postfix mail system
Oct  6 18:00:24 ben-server postfix/master[27733]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:00:37 ben-server sm-mta[27736]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory
Oct  6 18:00:37 ben-server sm-mta[27736]: ruleset=check_relay, arg1=localhost.localdomain, arg2=127.0.0.1, relay=localhost.localdomain [127.0.0.1], reject=451 4.3.0 Temporary system failure. Please try again later.
Oct  6 18:01:41 ben-server postfix/postfix-script[27846]: starting the Postfix mail system
Oct  6 18:01:41 ben-server postfix/master[27847]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:03:47 ben-server postfix/postfix-script[28072]: the Postfix mail system is not running
Oct  6 18:04:16 ben-server sm-mta[28082]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory
Oct  6 18:04:16 ben-server sm-mta[28082]: ruleset=check_relay, arg1=localhost.localdomain, arg2=127.0.0.1, relay=localhost.localdomain [127.0.0.1], reject=451 4.3.0 Temporary system failure. Please try again later.
Oct  6 18:04:51 ben-server postfix/postfix-script[28092]: the Postfix mail system is not running
Oct  6 18:04:59 ben-server postfix/postfix-script[28197]: starting the Postfix mail system
Oct  6 18:04:59 ben-server postfix/master[28198]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:09:37 ben-server postfix/master[28357]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:09:43 ben-server postfix/postfix-script[28366]: the Postfix mail system is not running
Oct  6 18:30:12 ben-server postfix/postfix-script[31908]: the Postfix mail system is not running
Oct  6 18:30:17 ben-server postfix/postfix-script[32012]: starting the Postfix mail system
Oct  6 18:30:17 ben-server postfix/master[32013]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:30:41 ben-server postfix/postfix-script[32571]: starting the Postfix mail system
Oct  6 18:30:41 ben-server postfix/master[32572]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:30:47 ben-server postfix/postfix-script[32695]: the Postfix mail system is not running
Oct  6 18:30:49 ben-server postfix/postfix-script[32703]: the Postfix mail system is not running
Oct  6 18:31:02 ben-server postfix/postfix-script[485]: starting the Postfix mail system
Oct  6 18:31:02 ben-server postfix/master[486]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:32:34 ben-server postfix/postfix-script[2062]: starting the Postfix mail system
Oct  6 18:32:34 ben-server postfix/master[2064]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:36:26 ben-server postfix/postfix-script[2406]: the Postfix mail system is not running
Oct  6 18:36:29 ben-server postfix/postfix-script[2488]: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Oct  6 18:36:29 ben-server postfix/postfix-script[2511]: starting the Postfix mail system
Oct  6 18:36:29 ben-server postfix/master[2512]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:39 ben-server postfix/postfix-script[2641]: starting the Postfix mail system
Oct  6 18:37:39 ben-server postfix/master[2642]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:45 ben-server postfix/postfix-script[2648]: error: unknown command: 'restart'
Oct  6 18:37:45 ben-server postfix/postfix-script[2649]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:37:50 ben-server postfix/postfix-script[2656]: fatal: the Postfix mail system is not running
Oct  6 18:37:54 ben-server postfix/postfix-script[2761]: starting the Postfix mail system
Oct  6 18:37:54 ben-server postfix/master[2762]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:56 ben-server postfix/postfix-script[2768]: error: unknown command: 'restart'
Oct  6 18:37:56 ben-server postfix/postfix-script[2769]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:37:59 ben-server postfix/postfix-script[2775]: error: unknown command: 'restart'
Oct  6 18:37:59 ben-server postfix/postfix-script[2776]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:38:01 ben-server postfix/postfix-script[2880]: starting the Postfix mail system
Oct  6 18:38:01 ben-server postfix/master[2881]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:38:03 ben-server postfix/postfix-script[2888]: the Postfix mail system is not running
Oct  6 18:39:27 ben-server postfix/postfix-script[3625]: starting the Postfix mail system
Oct  6 18:39:28 ben-server postfix/master[3626]: fatal: bind 0.0.0.0 port 587: Address already in use
```

---

### Post by lcman on 2011-10-06
> **bcraig24 said:**
> I'm totally new to installing a mail server and I need some help please =)

My system is probably full of rubbish configurations now after multiple failed attempts of following tutorials...

I have a static IP and a domain name pointing to my localwebser on my Ubuntu 10.04 system.
I need to setup some type of mail server to be able to activate mail functions in my php.

I've followed many tutorials to install postfix but at the end of it I test the status and get "Postfix is not running" even after commanding it to start...

Pleeeease help! So frustraing.
Let me know what info I need to post up..

/etc/hosts
```
127.0.0.1    localhost.localdomain    localhost
127.0.1.1    ben-server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
/var/log/mail.log:
```

Oct  6 17:40:01 ben-server sm-msp-queue[26386]: My unqualified host name (ben-server) unknown; sleeping for retry
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: unable to qualify my own domain name (ben-server) -- using short name
Oct  6 17:41:01 ben-server sm-mta[26392]: p964f1qe026392: SYSERR(root): collect: Cannot write ./dfp964f1qe026392 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26392]: p964f1qe026392: from=<>, size=5622, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p94NL2H8017112: to=postmaster, delay=1+05:19:58, xdelay=00:00:00, mailer=relay, pri=7954984, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1qe026392 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26393]: p964f1Ix026393: SYSERR(root): collect: Cannot write ./dfp964f1Ix026393 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:01 ben-server sm-mta[26393]: p964f1Ix026393: from=<>, size=3758, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p94JL2aP015957: to=postmaster, delay=1+09:19:58, xdelay=00:00:00, mailer=relay, pri=9033144, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1Ix026393 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:01 ben-server sm-mta[26394]: p964f19u026394: SYSERR(root): collect: Cannot write ./dfp964f19u026394 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26394]: p964f19u026394: from=<>, size=7329, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p930L1qg002969: to=postmaster, delay=3+04:19:58, xdelay=00:00:00, mailer=relay, pri=20646673, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f19u026394 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26395]: p964f1u5026395: SYSERR(root): collect: Cannot write ./dfp964f1u5026395 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:01 ben-server sm-mta[26395]: p964f1u5026395: from=<>, size=5447, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:01 ben-server sm-msp-queue[26386]: p92KL1Ib001766: to=postmaster, delay=3+08:19:59, xdelay=00:00:00, mailer=relay, pri=21724809, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f1u5026395 (sm_io_flush||sm_io_error, uid=0, gid=129): Input/output error
Oct  6 17:41:02 ben-server sm-mta[26396]: p964f2bd026396: SYSERR(root): collect: Cannot write ./dfp964f2bd026396 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26396]: p964f2bd026396: from=<>, size=2263, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:02 ben-server sm-msp-queue[26386]: p91N11U4027649: to=root, delay=4+05:40:01, xdelay=00:00:00, mailer=relay, pri=27481493, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f2bd026396 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26397]: p964f2dD026397: SYSERR(root): collect: Cannot write ./dfp964f2dD026397 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:41:02 ben-server sm-mta[26397]: p964f2dD026397: from=<root@ben-server>, size=459, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct  6 17:41:02 ben-server sm-msp-queue[26386]: p91ImH4g026427: to=root, ctladdr=root (0/0), delay=4+09:52:45, xdelay=00:00:00, mailer=relay, pri=28650217, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp964f2dD026397 (bfcommit, uid=0, gid=129): No such file or directory
Oct  6 17:50:23 ben-server postfix/master[27177]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 17:53:16 ben-server postfix/master[27472]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 17:57:12 ben-server postfix/master[27606]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:00:18 ben-server postfix/postfix-script[27628]: the Postfix mail system is not running
Oct  6 18:00:24 ben-server postfix/postfix-script[27732]: starting the Postfix mail system
Oct  6 18:00:24 ben-server postfix/master[27733]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:00:37 ben-server sm-mta[27736]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory
Oct  6 18:00:37 ben-server sm-mta[27736]: ruleset=check_relay, arg1=localhost.localdomain, arg2=127.0.0.1, relay=localhost.localdomain [127.0.0.1], reject=451 4.3.0 Temporary system failure. Please try again later.
Oct  6 18:01:41 ben-server postfix/postfix-script[27846]: starting the Postfix mail system
Oct  6 18:01:41 ben-server postfix/master[27847]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:03:47 ben-server postfix/postfix-script[28072]: the Postfix mail system is not running
Oct  6 18:04:16 ben-server sm-mta[28082]: NOQUEUE: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory
Oct  6 18:04:16 ben-server sm-mta[28082]: ruleset=check_relay, arg1=localhost.localdomain, arg2=127.0.0.1, relay=localhost.localdomain [127.0.0.1], reject=451 4.3.0 Temporary system failure. Please try again later.
Oct  6 18:04:51 ben-server postfix/postfix-script[28092]: the Postfix mail system is not running
Oct  6 18:04:59 ben-server postfix/postfix-script[28197]: starting the Postfix mail system
Oct  6 18:04:59 ben-server postfix/master[28198]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:09:37 ben-server postfix/master[28357]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:09:43 ben-server postfix/postfix-script[28366]: the Postfix mail system is not running
Oct  6 18:30:12 ben-server postfix/postfix-script[31908]: the Postfix mail system is not running
Oct  6 18:30:17 ben-server postfix/postfix-script[32012]: starting the Postfix mail system
Oct  6 18:30:17 ben-server postfix/master[32013]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:30:41 ben-server postfix/postfix-script[32571]: starting the Postfix mail system
Oct  6 18:30:41 ben-server postfix/master[32572]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:30:47 ben-server postfix/postfix-script[32695]: the Postfix mail system is not running
Oct  6 18:30:49 ben-server postfix/postfix-script[32703]: the Postfix mail system is not running
Oct  6 18:31:02 ben-server postfix/postfix-script[485]: starting the Postfix mail system
Oct  6 18:31:02 ben-server postfix/master[486]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:32:34 ben-server postfix/postfix-script[2062]: starting the Postfix mail system
Oct  6 18:32:34 ben-server postfix/master[2064]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:36:26 ben-server postfix/postfix-script[2406]: the Postfix mail system is not running
Oct  6 18:36:29 ben-server postfix/postfix-script[2488]: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Oct  6 18:36:29 ben-server postfix/postfix-script[2511]: starting the Postfix mail system
Oct  6 18:36:29 ben-server postfix/master[2512]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:39 ben-server postfix/postfix-script[2641]: starting the Postfix mail system
Oct  6 18:37:39 ben-server postfix/master[2642]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:45 ben-server postfix/postfix-script[2648]: error: unknown command: 'restart'
Oct  6 18:37:45 ben-server postfix/postfix-script[2649]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:37:50 ben-server postfix/postfix-script[2656]: fatal: the Postfix mail system is not running
Oct  6 18:37:54 ben-server postfix/postfix-script[2761]: starting the Postfix mail system
Oct  6 18:37:54 ben-server postfix/master[2762]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:37:56 ben-server postfix/postfix-script[2768]: error: unknown command: 'restart'
Oct  6 18:37:56 ben-server postfix/postfix-script[2769]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:37:59 ben-server postfix/postfix-script[2775]: error: unknown command: 'restart'
Oct  6 18:37:59 ben-server postfix/postfix-script[2776]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Oct  6 18:38:01 ben-server postfix/postfix-script[2880]: starting the Postfix mail system
Oct  6 18:38:01 ben-server postfix/master[2881]: fatal: bind 0.0.0.0 port 587: Address already in use
Oct  6 18:38:03 ben-server postfix/postfix-script[2888]: the Postfix mail system is not running
Oct  6 18:39:27 ben-server postfix/postfix-script[3625]: starting the Postfix mail system
Oct  6 18:39:28 ben-server postfix/master[3626]: fatal: bind 0.0.0.0 port 587: Address already in use
```

Did you do /etc/init.d/postfix start ?

---

### Post by hawk2010 on 2011-10-06
This "
Oct  6 18:39:28 ben-server postfix/master[3626]: fatal: bind 0.0.0.0 port 587: Address already in use"
SHows that your server already has 587 port used. paste a netstat -nap here.

---

### Post by bcraig24 on 2011-10-06
In my router smtp is forwarded to my servers local IP on port 587

unix  3      [ ]         STREAM     CONNECTED     8363     1720/notification-a 
unix  3      [ ]         STREAM     CONNECTED     8362     1720/notification-a /tmp/orbit-ben/linc-6b8-0-9cc546f1999
unix  3      [ ]         STREAM     CONNECTED     8361     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     8360     1719/clock-applet   /tmp/orbit-ben/linc-6b7-0-3feea360ef68f
unix  3      [ ]         STREAM     CONNECTED     8359     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     8358     1718/indicator-appl /tmp/orbit-ben/linc-6b6-0-21309cfae77d3
unix  3      [ ]         STREAM     CONNECTED     8357     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     8356     1715/indicator-appl /tmp/orbit-ben/linc-6b3-0-6a504afae6754
unix  3      [ ]         STREAM     CONNECTED     8355     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     8354     1720/notification-a /tmp/orbit-ben/linc-6b8-0-9cc546f1999
unix  3      [ ]         STREAM     CONNECTED     8353     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8352     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     8351     1720/notification-a 
unix  3      [ ]         STREAM     CONNECTED     8349     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8348     1720/notification-a 
unix  3      [ ]         STREAM     CONNECTED     8347     1720/notification-a /tmp/orbit-ben/linc-6b8-0-9cc546f1999
unix  3      [ ]         STREAM     CONNECTED     8346     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     8343     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     8342     1720/notification-a 
unix  3      [ ]         STREAM     CONNECTED     8338     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8337     1720/notification-a 
unix  3      [ ]         STREAM     CONNECTED     8334     1719/clock-applet   /tmp/orbit-ben/linc-6b7-0-3feea360ef68f
unix  3      [ ]         STREAM     CONNECTED     8333     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8332     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     8331     1719/clock-applet   
unix  3      [ ]         STREAM     CONNECTED     8329     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8328     1719/clock-applet   
unix  3      [ ]         STREAM     CONNECTED     8327     1719/clock-applet   /tmp/orbit-ben/linc-6b7-0-3feea360ef68f
unix  3      [ ]         STREAM     CONNECTED     8326     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     8323     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     8322     1719/clock-applet   
unix  3      [ ]         STREAM     CONNECTED     8318     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8317     1719/clock-applet   
unix  3      [ ]         STREAM     CONNECTED     8314     1718/indicator-appl /tmp/orbit-ben/linc-6b6-0-21309cfae77d3
unix  3      [ ]         STREAM     CONNECTED     8313     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8312     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     8311     1718/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8309     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8308     1718/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8307     1718/indicator-appl /tmp/orbit-ben/linc-6b6-0-21309cfae77d3
unix  3      [ ]         STREAM     CONNECTED     8306     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     8303     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     8302     1718/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8299     1715/indicator-appl /tmp/orbit-ben/linc-6b3-0-6a504afae6754
unix  3      [ ]         STREAM     CONNECTED     8298     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8297     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     8296     1715/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8294     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8293     1715/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8292     1715/indicator-appl /tmp/orbit-ben/linc-6b3-0-6a504afae6754
unix  3      [ ]         STREAM     CONNECTED     8291     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     8288     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     8287     1715/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8283     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8282     1718/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8278     1722/gvfsd-burn     @/dbus-vfs-daemon/socket-zfoIqAww
unix  3      [ ]         STREAM     CONNECTED     8277     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     8279     1722/gvfsd-burn     @/dbus-vfs-daemon/socket-jdzQ0fVJ
unix  3      [ ]         STREAM     CONNECTED     8276     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     8266     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8265     1722/gvfsd-burn     
unix  3      [ ]         STREAM     CONNECTED     8263     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8262     1715/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     8034     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8033     1701/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     8032     1661/gvfsd-trash    @/dbus-vfs-daemon/socket-Xw1RqOgS
unix  3      [ ]         STREAM     CONNECTED     8031     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     8030     1661/gvfsd-trash    @/dbus-vfs-daemon/socket-oWdBknwn
unix  3      [ ]         STREAM     CONNECTED     8029     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     8026     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8025     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     8023     1701/gnome-screensa /tmp/orbit-ben/linc-6a4-0-480035eadca0e
unix  3      [ ]         STREAM     CONNECTED     8022     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     8019     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     8018     1701/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     8014     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     8013     1701/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     8011     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8010     1701/gnome-screensa 
unix  3      [ ]         STREAM     CONNECTED     7941     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7940     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7933     1559/gnome-panel    /tmp/orbit-ben/linc-617-0-1d77c3ca61ad
unix  3      [ ]         STREAM     CONNECTED     7932     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7931     1690/wnck-applet    /tmp/orbit-ben/linc-69a-0-c822a068764c
unix  3      [ ]         STREAM     CONNECTED     7930     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7929     1690/wnck-applet    /tmp/orbit-ben/linc-69a-0-c822a068764c
unix  3      [ ]         STREAM     CONNECTED     7928     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7927     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7926     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7924     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7923     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7922     1690/wnck-applet    /tmp/orbit-ben/linc-69a-0-c822a068764c
unix  3      [ ]         STREAM     CONNECTED     7921     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     7918     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     7917     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7913     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7912     1697/gvfs-gphoto2-v 
unix  3      [ ]         STREAM     CONNECTED     7903     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7902     1694/gvfs-afc-volum 
unix  3      [ ]         STREAM     CONNECTED     7897     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7896     1690/wnck-applet    
unix  3      [ ]         STREAM     CONNECTED     7893     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7892     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7886     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7885     1681/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     7817     1559/gnome-panel    /tmp/orbit-ben/linc-617-0-1d77c3ca61ad
unix  3      [ ]         STREAM     CONNECTED     7816     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     7814     1658/bonobo-activat /tmp/orbit-ben/linc-67a-0-36429436204de
unix  3      [ ]         STREAM     CONNECTED     7813     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7811     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7810     1658/bonobo-activat 
unix  3      [ ]         STREAM     CONNECTED     7809     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7808     1572/vino-server    
unix  3      [ ]         STREAM     CONNECTED     7800     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7799     -                   
unix  3      [ ]         STREAM     CONNECTED     7795     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7794     -                   
unix  3      [ ]         STREAM     CONNECTED     7783     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7782     1681/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     7777     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7776     1681/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     7767     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7766     1442/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     7765     -                   /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     7764     -                   
unix  3      [ ]         STREAM     CONNECTED     7758     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7757     -                   
unix  3      [ ]         STREAM     CONNECTED     7756     -                   @/var/run/hald/dbus-2EcBBn3xKF
unix  3      [ ]         STREAM     CONNECTED     7755     -                   
unix  3      [ ]         STREAM     CONNECTED     7754     -                   @/var/run/hald/dbus-2EcBBn3xKF
unix  3      [ ]         STREAM     CONNECTED     7752     -                   
unix  3      [ ]         STREAM     CONNECTED     7751     -                   @/var/run/hald/dbus-2EcBBn3xKF
unix  3      [ ]         STREAM     CONNECTED     7729     -                   
unix  3      [ ]         STREAM     CONNECTED     7716     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7715     -                   
unix  3      [ ]         STREAM     CONNECTED     7665     1274/gnome-session  @/tmp/.ICE-unix/1274
unix  3      [ ]         STREAM     CONNECTED     7664     1566/metacity       
unix  3      [ ]         STREAM     CONNECTED     7604     1661/gvfsd-trash    @/dbus-vfs-daemon/socket-IG95eAh5
unix  3      [ ]         STREAM     CONNECTED     7602     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7603     1661/gvfsd-trash    @/dbus-vfs-daemon/socket-12pa3NNj
unix  3      [ ]         STREAM     CONNECTED     7601     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7581     -                   @/var/run/hald/dbus-2EcBBn3xKF
unix  3      [ ]         STREAM     CONNECTED     7569     -                   
unix  3      [ ]         STREAM     CONNECTED     7579     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7566     1661/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     7563     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7562     1661/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     7495     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7494     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7453     1274/gnome-session  @/tmp/.ICE-unix/1274
unix  3      [ ]         STREAM     CONNECTED     7452     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7451     1566/metacity       /tmp/orbit-ben/linc-61e-0-76665b7b5002f
unix  3      [ ]         STREAM     CONNECTED     7450     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7447     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7446     1566/metacity       
unix  3      [ ]         STREAM     CONNECTED     7442     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7441     1566/metacity       
unix  3      [ ]         STREAM     CONNECTED     7385     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7384     1566/metacity       
unix  3      [ ]         STREAM     CONNECTED     7349     -                   @/var/run/hald/dbus-Res7LJekcH
unix  3      [ ]         STREAM     CONNECTED     7348     -                   
unix  3      [ ]         STREAM     CONNECTED     7321     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7320     -                   
unix  3      [ ]         STREAM     CONNECTED     7289     1523/pulseaudio     /home/ben/.pulse/2bff8f99fc779f93228395fa4ccdc550-runtime/native
unix  3      [ ]         STREAM     CONNECTED     7286     1442/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     7280     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7279     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7278     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7277     1570/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     7276     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7275     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7271     1600/gconf-helper   /tmp/orbit-ben/linc-640-0-5bb2ae8942794
unix  3      [ ]         STREAM     CONNECTED     7270     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7256     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7255     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7257     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7254     1600/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     7247     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7246     1600/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     7168     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7167     1572/vino-server    
unix  3      [ ]         STREAM     CONNECTED     7163     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7162     1523/pulseaudio     
unix  2      [ ]         DGRAM                    7157     1523/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     7156     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7155     -                   
unix  3      [ ]         STREAM     CONNECTED     7151     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7150     -                   
unix  3      [ ]         STREAM     CONNECTED     7144     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7143     1570/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     7132     1572/vino-server    /tmp/orbit-ben/linc-624-0-5734585e154b
unix  3      [ ]         STREAM     CONNECTED     7131     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7127     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7115     1572/vino-server    
unix  3      [ ]         STREAM     CONNECTED     7125     1568/nautilus       /tmp/orbit-ben/linc-620-0-14c8a002e76
unix  3      [ ]         STREAM     CONNECTED     7112     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7116     1570/nm-applet      /tmp/orbit-ben/linc-622-0-743d9576d81
unix  3      [ ]         STREAM     CONNECTED     7108     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7109     1497/gnome-power-ma /tmp/orbit-ben/linc-5d9-0-6023b5dee188d
unix  3      [ ]         STREAM     CONNECTED     7104     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7094     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7093     1572/vino-server    
unix  3      [ ]         STREAM     CONNECTED     7091     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7090     1572/vino-server    
unix  3      [ ]         STREAM     CONNECTED     7103     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7087     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7082     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7080     1570/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     7081     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7079     1497/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     7077     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7076     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7064     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7063     1570/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     7057     1274/gnome-session  @/tmp/.ICE-unix/1274
unix  3      [ ]         STREAM     CONNECTED     7056     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     7054     1559/gnome-panel    /tmp/orbit-ben/linc-617-0-1d77c3ca61ad
unix  3      [ ]         STREAM     CONNECTED     7053     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     7050     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     7049     1559/gnome-panel    
unix  2      [ ]         DGRAM                    7048     -                   
unix  3      [ ]         STREAM     CONNECTED     7046     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7045     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7043     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     7042     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7036     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7035     1569/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     7033     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7032     1569/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     7028     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7027     1559/gnome-panel    
unix  3      [ ]         STREAM     CONNECTED     7023     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7022     1568/nautilus       
unix  3      [ ]         STREAM     CONNECTED     6983     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6982     1523/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     6971     1498/bluetooth-appl /tmp/orbit-ben/linc-5da-0-5312dd4a29a04
unix  3      [ ]         STREAM     CONNECTED     6970     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     6967     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     6966     1498/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     6963     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6962     1498/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     6930     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6929     1570/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     6838     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6837     -                   
unix  3      [ ]         STREAM     CONNECTED     6803     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6802     1498/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     6800     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6799     1498/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     6695     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6694     1497/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     6692     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6691     1497/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     6634     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6633     -                   
unix  2      [ ]         DGRAM                    6632     -                   
unix  3      [ ]         STREAM     CONNECTED     6557     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6556     1523/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     6497     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6496     1505/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     6486     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6483     1505/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     6416     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6415     1497/gnome-power-ma 
unix  3      [ ]         STREAM     CONNECTED     6237     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6236     1489/gvfsd          
unix  2      [ ]         DGRAM                    6235     -                   
unix  3      [ ]         STREAM     CONNECTED     6230     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6229     1442/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     6172     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6171     1462/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     6167     -                   
unix  3      [ ]         STREAM     CONNECTED     6166     -                   
unix  3      [ ]         STREAM     CONNECTED     6101     1442/gnome-settings /tmp/orbit-ben/linc-5a2-0-72fc06a3d0a5
unix  3      [ ]         STREAM     CONNECTED     6100     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     6097     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     6096     1442/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     6090     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     6089     1442/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     6087     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6086     1442/gnome-settings 
unix  2      [ ]         DGRAM                    5762     -                   
unix  3      [ ]         STREAM     CONNECTED     5755     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5754     1274/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     5716     1274/gnome-session  /tmp/orbit-ben/linc-4fa-0-4a98122a62213
unix  3      [ ]         STREAM     CONNECTED     5715     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     5712     1371/gconfd-2       /tmp/orbit-ben/linc-55b-0-5c297c7d58b11
unix  3      [ ]         STREAM     CONNECTED     5711     1274/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     5708     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5707     1371/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     5483     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     5482     1371/gconfd-2       
unix  2      [ ]         DGRAM                    5455     -                   
unix  3      [ ]         STREAM     CONNECTED     5420     1339/dbus-daemon    @/tmp/dbus-DbUVgyJnBw
unix  3      [ ]         STREAM     CONNECTED     5419     1274/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     5413     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     5412     1274/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     5399     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     5398     1326/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     5397     1339/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     5396     1339/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     5380     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     5379     1326/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     5197     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5196     -                   
unix  2      [ ]         DGRAM                    5180     -                   
unix  3      [ ]         STREAM     CONNECTED     5127     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     5126     -                   
unix  3      [ ]         STREAM     CONNECTED     5122     -                   @/tmp/gdm-session-SQjxMeRo
unix  3      [ ]         STREAM     CONNECTED     5121     -                   
unix  3      [ ]         STREAM     CONNECTED     5118     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     5117     -                   
unix  3      [ ]         STREAM     CONNECTED     4960     -                   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     4959     -                   
unix  2      [ ]         DGRAM                    4929     -                   
unix  2      [ ]         DGRAM                    4918     -                   
unix  3      [ ]         STREAM     CONNECTED     4757     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4756     -                   
unix  2      [ ]         DGRAM                    4755     -                   
unix  3      [ ]         STREAM     CONNECTED     4717     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4716     -                   
unix  2      [ ]         DGRAM                    4715     -                   
unix  3      [ ]         STREAM     CONNECTED     4672     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4671     -                   
unix  3      [ ]         STREAM     CONNECTED     4598     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4597     -                   
unix  2      [ ]         DGRAM                    4570     -                   
unix  3      [ ]         STREAM     CONNECTED     4565     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4564     -                   
unix  3      [ ]         STREAM     CONNECTED     4555     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4554     -                   
unix  3      [ ]         STREAM     CONNECTED     4551     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4550     -                   
unix  2      [ ]         DGRAM                    4547     -                   
unix  3      [ ]         STREAM     CONNECTED     4543     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4542     -                   
unix  3      [ ]         STREAM     CONNECTED     4515     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4514     -                   
unix  3      [ ]         STREAM     CONNECTED     4509     -                   
unix  3      [ ]         STREAM     CONNECTED     4508     -                   
unix  2      [ ]         DGRAM                    4505     -                   
unix  3      [ ]         STREAM     CONNECTED     4457     -                   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     4456     -                   
unix  3      [ ]         STREAM     CONNECTED     4452     -                   
unix  3      [ ]         STREAM     CONNECTED     4451     -                   
unix  3      [ ]         DGRAM                    2964     -                   
unix  3      [ ]         DGRAM                    2963     -                   
unix  3      [ ]         STREAM     CONNECTED     2915     -                   @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2914     -

---

