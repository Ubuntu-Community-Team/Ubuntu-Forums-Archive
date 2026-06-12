---
title: "Dovecot dies with PAM error?"
date: 2008-10-21
forum: Server Platforms
---

### Post by JasonWalton on 2008-10-21
I just setup a new server on the weekend with Ubuntu 8.10 beta.  Every now and then, the IMAP server dies, and won't let users authenticate.  It's happened twice now.  In /var/log/mail.log, you can see dovecot complaining about critial errors:

```
Oct 21 14:44:15 tachikoma dovecot: imap-login: Login: user=<jason>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, TLS
Oct 21 14:44:15 tachikoma dovecot: IMAP(jason): Disconnected: Logged out bytes=769/9124
Oct 21 14:45:15 tachikoma dovecot: imap-login: Login: user=<jason>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, TLS
Oct 21 14:45:16 tachikoma dovecot: IMAP(jason): Disconnected: Logged out bytes=769/9124
Oct 21 14:46:16 tachikoma dovecot: imap-login: Login: user=<jason>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, TLS
Oct 21 14:46:16 tachikoma dovecot: IMAP(jason): Disconnected: Logged out bytes=769/9124
Oct 21 14:47:15 tachikoma dovecot: auth-worker(default): pam(jason,127.0.0.1): pam_start() failed: Critical error - immediate abort
Oct 21 14:47:17 tachikoma dovecot: imap-login: Disconnected (auth failed, 1 attempts): user=<jason>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, TLS
```

If I have a look at /var/log/auth.log, I see:

```
Oct 21 14:47:15 tachikoma dovecot-auth: PAM _pam_init_handlers: error reading /etc/pam.d/dovecot
Oct 21 14:47:15 tachikoma dovecot-auth: PAM _pam_init_handlers: [Critical error - immediate abort]
Oct 21 14:47:15 tachikoma dovecot-auth: PAM error reading PAM configuration file
Oct 21 14:47:15 tachikoma dovecot-auth: PAM pam_start: failed to initialize handlers
```

This sounds ominous.  If I try to cat /etc/pam.d/dovecot, though, the file is obviously there:

```
jason@tachikoma:/var/log$ cat /etc/pam.d/dovecot
#%PAM-1.0

@include common-auth
@include common-account
@include common-session
```

And restarting dovecot seems to fix the problem.  Dovecot WAS running just fine, servicing mail all day long, and then suddenly it won't read the PAM config file, and then it won't let anyone log in until I log in and kill it.  Any ideas?

I'm also noticing, in /var/log/mail.log:

```
Fatal: imap-login: Dovecot version mismatch: Master is v1.1.2, login is v1.1.4 (if you don't care, set version_ignore=yes)
```

which also sounds un-good.  There's lots of these in the log, though.

---

### Post by JasonWalton on 2008-10-22
I did an "apt-get -u upgrade", which cleared up my mismatched version problem, but I'm still seeing dovecot die at random intervals.  Happened twice so far, today.

---

### Post by JasonWalton on 2008-10-26
I got a fix from Timo Sirainen which seems to solve the problem:

Timo said:
> Perhaps it's leaking file descriptors and running out of them. Set auth_worker_max_request_count to some non-zero value and it probably gets fixed.

---

### Post by chadoe on 2008-11-06
Thanks for the info, had the same errors with my 8.10 server install, changing auth_worker_max_request_count seems to "fix" it.

---

### Post by dwek on 2008-11-16
Hi all,

I have the same problem after the 8.10 upgrade. 

I have been trying to roundcube working again with no luck (even after a reinstall of roundcube).

The problem seems to be when IMAP tried to authenticate to PAM.
Although, I have played with the setting for many hours today, it still does not want to authenticate.

I get this in the log: 
[INDENT]
dovecot: auth-worker(default): pam(xxxxx,192.168.xxx.xxx): pam_authenticate() failed: Authentication failur[/INDENT]e 

This is then followed by the following error:
[INDENT]dovecot: imap-login: Disconnected (auth failed, 1 attempts): user=<xxxx>, method=PLAIN, rip=192.168.xxx.xxx, lip=192.168.xxx.xxx, secured[/INDENT]

I tried changing auth_worker_max_request_count to 35, but this did not help.

This is very frustrating.

Additionally, I had problems with the roundcube database, something to do with not being able to upgrade one of the tables during the 8.10 upgrade. I was able to remove Roundcube and dump the database before the reinstall.
This fixed the issue (don know what it was).

The other issue is Gallery2. After the 8.10 upgrade I upgraded the Gallery which then failed on step2 due to the missing smarty files.

Any thoughts are very welcome.

Thanks

---

### Post by kmARC on 2009-01-12
Hi,

is there already any solution for this problem?

---

### Post by GJB on 2009-02-02
You can remove the PAM modules from the /etc/pam.d/dovecot file or comment them out with a #.

```
jason@tachikoma:/var/log$ cat /etc/pam.d/dovecot
#%PAM-1.0

#@include common-auth
#@include common-account
#@include common-session

```
Then restart your /etc/init.d/dovecot process

It wont be using PAM anymore and logging in will be oke

;)

---

### Post by grawest on 2009-02-04
hello.
i have the same problem after the 8.10 upgrade too :)
and i don't know what i have to do.
any thoughts?
>  You can remove the PAM modules from the /etc/pam.d/dovecot file or comment them out with a #.

Code:

jason@tachikoma:/var/log$ cat /etc/pam.d/dovecot
#%PAM-1.0

#@include common-auth
#@include common-account
#@include common-session

Then restart your /etc/init.d/dovecot process

It wont be using PAM anymore and logging in will be oke


thanks GJB, but it didn't help

---

### Post by grawest on 2009-02-09
hello again.
i think i could fix it.
set auth_worker_max_count = 200
and auth_worker_max_request_count = 200

---

### Post by DJalil74 on 2010-02-09
this not fix the problem. Dovecot down.

---

