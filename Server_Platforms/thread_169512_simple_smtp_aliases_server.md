---
title: "simple smtp aliases server?"
date: 2006-05-02
forum: Server Platforms
---

### Post by Gherald on 2006-05-02
We have a very old RedHat 7.x machine whose only purpose is to forward mail using a sendmail /etc/aliases file similar to the following:

```
aos: user1@facstaff.blah.edu
arthistory: user2@facstaff.blah.edu
asianamstudies: user3@facstaff.blah.edu
astro: user4@astro.blah.edu
botany: user5@facstaff.blah.edu
botgrad: user6@facstaff.blah.edu
...and so on, and on...
```
I've been tasked with moving this functionality to a newer machine.

I thought the simplest thing would be to keep using sendmail, so I tried to configure it as a daemon listening on eth0:
```
LINUX ~ # grep "^[^#]" /etc/mail/sendmail.conf
DAEMON_NETMODE="Static";
DAEMON_NETIF="eth0";
DAEMON_MODE="Daemon";
DAEMON_PARMS="";
DAEMON_HOSTSTATS="Yes";
DAEMON_MAILSTATS="Yes";
QUEUE_MODE="${DAEMON_MODE}";
QUEUE_INTERVAL="10m";
QUEUE_PARMS="";
MSP_MODE="Cron";
MSP_INTERVAL="20m";
MSP_PARMS="";
MSP_MAILSTATS="${DAEMON_MAILSTATS}";
MISC_PARMS="";
CRON_MAILTO="root";
CRON_PARMS="";
LOG_CMDS="No";
HANDS_OFF="No";
AGE_DATA="";
DAEMON_RUNASUSER="No";
DAEMON_STATS="${DAEMON_MAILSTATS}";
MSP_STATS="${MSP_MAILSTATS}";
```
But it's not running the MTA...
```
# sendmailconfig
Configure sendmail with the existing /etc/mail/sendmail.conf? [Y]  
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Configure sendmail with the existing /etc/mail/sendmail.mc? [Y] y
Updating sendmail environment ...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Could not open /etc/mail/databases(No such file or directory), creating it.
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...

Checking filesystem, this may take some time - it will not hang!
  ...   Done.
 
Checking for installed MDAs...
sasl2-bin not installed, not configuring sendmail support.

To enable sendmail SASL2 support at a later date, invoke "/usr/share/sendmail/update_auth"

 
Creating/Updating SSL(for TLS) information
Creating /etc/mail/tls/starttls.m4...
You already have sendmail certificates
 

*** *** *** WARNING *** WARNING *** WARNING *** WARNING *** *** ***

Everything you need to support STARTTLS (encrypted mail transmission
and user authentication via certificates) is installed and configured
but *IS* not being used.

To enable sendmail to use STARTTLS, you need to:
1) Add this line to /etc/mail/sendmail.mc and optionally
   to /etc/mail/submit.mc:
  include(`/etc/mail/tls/starttls.m4')dnl
2) Run sendmailconfig
3) Restart sendmail

Checking {sendmail,submit}.mc and related databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/databases...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Creating /etc/mail/Makefile...
Reading configuration from /etc/mail/sendmail.conf.
Validating configuration.
Writing configuration to /etc/mail/sendmail.conf.
Writing /etc/cron.d/sendmail.
Creating /etc/mail/sendmail.cf...
Creating /etc/mail/submit.cf...
Informational: confCR_FILE file empty: /etc/mail/relay-domains
Informational: confCT_FILE file empty: /etc/mail/trusted-users
Updating /etc/mail/access...
Updating /etc/mail/aliases...
/etc/mail/aliases: 72 aliases, longest 184 bytes, 1801 bytes total
Reload the running sendmail now with the new configuration? [Y] y
Reloading sendmail ...
LINUX ~ # /etc/init.d/sendmail restart
Restarting Transport Agent: sendmail.
LINUX ~ # /etc/init.d/sendmail status
MSP: is run via cron (20m)
MTA: is not running
QUE: Same as MTA
```

So, what am I missing?

Is there some other (simpler/easier/stabler) MTA that can forward these aliases?

I really have no experience or preference with mail stuff, I just want something that works.

---

### Post by Gherald on 2006-05-04
Trying to start the mta manually, I get the following:
```
# /usr/sbin/sendmail -v -L sm-mta -bD -q25m
451 4.0.0 opendaemonsocket: daemon MTA-v4: cannot bind: Cannot assign requested address
```

---

### Post by Gherald on 2006-05-04
(double post)

---

