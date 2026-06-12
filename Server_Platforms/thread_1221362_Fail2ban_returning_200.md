---
title: "Fail2ban returning 200"
date: 2009-07-23
forum: Server Platforms
---

### Post by mikebern on 2009-07-23
I am having a problem with fail2ban on 9.04.

I found the post talking about switch the python version to 2.5. I
modify fail2ban-client and fail2ban-server to use 2.5. Do this removed
the communication errors in the log file.

Now I am having a problem with server and execute commands.

When creating a jail using iptables it getting returning 200 and the jail
in iptables in not setup correct. If I stop and restart fail2ban the jail
that is broken changes.

Please do not tell me that you can do some rate control with iptables.
Using iptables can not block only user that do bad things. It blocks
all users.


Here is are the active jails:
[apache]

enabled = true
port    = http,https
filter  = apache-auth
logpath = /var/log/apache*/*error.log
bantime  = 900
maxretry = 6


[dovecot]

enabled = true
port    = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter  = dovecot-auth
logpath = /var/log/mail.log
bantime  = 900
maxretry = 6

[SquirrelMail]

enabled   = true
port      = http,https
filter    = squirrelmail
logpath   = /var/log/squirrelmail.log
bantime  = 900
maxretry = 3



Here is the log file:
2009-07-23 18:42:31,996 fail2ban.server : INFO   Changed logging target to /var/
log/fail2ban.log for Fail2ban v0.8.3
2009-07-23 18:42:31,998 fail2ban.jail   : INFO   Creating new jail 'apache'
2009-07-23 18:42:31,998 fail2ban.jail   : INFO   Jail 'apache' uses poller
2009-07-23 18:42:32,029 fail2ban.filter : INFO   Added logfile = /var/log/apache
2/error.log
2009-07-23 18:42:32,030 fail2ban.filter : INFO   Set maxRetry = 6
2009-07-23 18:42:32,033 fail2ban.filter : INFO   Set findtime = 600
2009-07-23 18:42:32,034 fail2ban.actions: INFO   Set banTime = 900
2009-07-23 18:42:32,054 fail2ban.jail   : INFO   Creating new jail 'dovecot'
2009-07-23 18:42:32,054 fail2ban.jail   : INFO   Jail 'dovecot' uses poller
2009-07-23 18:42:32,056 fail2ban.filter : INFO   Added logfile = /var/log/mail.l
og
2009-07-23 18:42:32,058 fail2ban.filter : INFO   Set maxRetry = 6
2009-07-23 18:42:32,060 fail2ban.filter : INFO   Set findtime = 600
2009-07-23 18:42:32,062 fail2ban.actions: INFO   Set banTime = 900
2009-07-23 18:42:32,080 fail2ban.jail   : INFO   Creating new jail 'SquirrelMail
'
2009-07-23 18:42:32,080 fail2ban.jail   : INFO   Jail 'SquirrelMail' uses poller
2009-07-23 18:42:32,082 fail2ban.filter : INFO   Added logfile = /var/log/squirr
elmail.log
2009-07-23 18:42:32,083 fail2ban.filter : INFO   Set maxRetry = 3
2009-07-23 18:42:32,086 fail2ban.filter : INFO   Set findtime = 600
2009-07-23 18:42:32,087 fail2ban.actions: INFO   Set banTime = 900
2009-07-23 18:42:32,102 fail2ban.jail   : INFO   Jail 'apache' started
2009-07-23 18:42:32,107 fail2ban.jail   : INFO   Jail 'dovecot' started
2009-07-23 18:42:32,114 fail2ban.jail   : INFO   Jail 'SquirrelMail' started
2009-07-23 18:42:32,139 fail2ban.actions.action: ERROR  iptables -N fail2ban-dov
ecot
iptables -A fail2ban-dovecot -j RETURN
iptables -I INPUT -p tcp -m multiport --dports smtp,ssmtp,imap2,imap3,imaps,pop3
,pop3s -j fail2ban-dovecot returned 200

---

### Post by Ve0 on 2009-11-15
UP

I have this problem too.

---

