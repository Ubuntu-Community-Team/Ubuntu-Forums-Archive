---
title: "Maildir Issues w/ IMAP and POP Server"
date: 2007-02-19
forum: Server Platforms
---

### Post by ClayPTino on 2007-02-19
I followed the following tutorial in order to set up a mail server running postfix and courier on a Dapper install:

[http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour](http://www.urbanpuddle.com/articles/2006/10/12/setup-postfix-in-about-1-hour)

I guess its a combo of the flurdy, perfect dapper install, and a few other tutorials.

I can telnet all of the servers and they all appear to be working; however, I can't log into any of them.

I have sent SEVERAL emails to the address in order to populate the mail folders, but for some reason it still isn't working and I can't log in to IMAP server using SquirrelMail or the POP server using Thunderbird.

When I log in using SquirrelMail I get the following back:

```

ERROR: Could not complete request.
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.

```

Thunderbird returns:

Maildir invalid (no 'cur' directory)

Here is my main.cf file:

```

myhostname = clayscape.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf 
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipi$

```

mail.err log:

```

Feb 18 18:17:07 hal authdaemond.mysql: Bad line in /etc/courier/authdaemonrc: MYSQL_SERVER localhost
Feb 18 18:26:11 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 18:29:36 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 18:34:45 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 18:36:51 hal imaplogin: Error reading ACLs for INBOX.Sent: No such file or directory
Feb 18 18:39:46 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 18:50:06 hal imaplogin: DISCONNECTED, ip=[::ffff:192.168.1.1], time=9
Feb 18 18:50:15 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 21:22:04 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:128.61.127.95], headers=0, body=0, time=1800, starttls=1
Feb 18 21:22:24 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:128.61.127.95], headers=0, body=0, time=1824, starttls=1
Feb 18 21:26:40 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:128.61.127.95], headers=0, body=0, time=1800, starttls=1
Feb 18 23:28:27 hal imaplogin: LOGIN FAILED, ip=[::ffff:192.168.1.1]
Feb 18 23:28:32 hal imaplogin: LOGIN FAILED, ip=[::ffff:192.168.1.1]
Feb 18 23:33:02 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 23:42:24 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 23:43:47 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 23:43:50 hal last message repeated 2 times
Feb 18 23:48:37 hal imaplogin: DISCONNECTED, user=clayton@clayscape.com, ip=[::ffff:127.0.0.1], headers=0, body=0, time=0
Feb 18 23:48:40 hal last message repeated 3 times

```

The last few entries from mail.log log:

```

Feb 19 00:03:39 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:03:39 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:04:02 hal postfix/smtpd[15415]: connect from unknown[192.168.1.1]
Feb 19 00:04:03 hal postfix/smtpd[15415]: 1A02F4F02E3: client=unknown[192.168.1.1], sasl_method=PLAIN, sasl_username=clayton@clayscape.com
Feb 19 00:04:03 hal postfix/cleanup[15424]: 1A02F4F02E3: message-id=<45D92FBC.5050505@clayscape.com>
Feb 19 00:04:03 hal postfix/qmgr[15275]: 1A02F4F02E3: from=<clayton@clayscape.com>, size=537, nrcpt=1 (queue active)
Feb 19 00:04:03 hal postfix/smtpd[15415]: disconnect from unknown[192.168.1.1]
Feb 19 00:04:03 hal postfix/local[15426]: 1A02F4F02E3: to=<clayton@clayscape.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb 19 00:04:03 hal postfix/qmgr[15275]: 1A02F4F02E3: removed   
Feb 19 00:04:06 hal courierpop3login: Connection, ip=[::ffff:192.168.1.1]
Feb 19 00:04:06 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:04:06 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:06:35 hal postfix/smtpd[15438]: connect from unknown[192.168.1.1]
Feb 19 00:06:35 hal postfix/trivial-rewrite[15419]: warning: do not list domain clayscape.com in BOTH mydestination and virtual_mailbox_domains
Feb 19 00:06:35 hal postfix/smtpd[15438]: 9199D4F02E3: client=unknown[192.168.1.1], sasl_method=PLAIN, sasl_username=clayton@clayscape.com
Feb 19 00:06:35 hal postfix/cleanup[15445]: 9199D4F02E3: message-id=<45D93055.5090408@clayscape.com>  
Feb 19 00:06:35 hal postfix/qmgr[15275]: 9199D4F02E3: from=<clayton@clayscape.com>, size=550, nrcpt=1 (queue active)
Feb 19 00:06:35 hal postfix/smtpd[15438]: disconnect from unknown[192.168.1.1]
Feb 19 00:06:35 hal postfix/local[15447]: 9199D4F02E3: to=<clayton@clayscape.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb 19 00:06:35 hal postfix/qmgr[15275]: 9199D4F02E3: removed
Feb 19 00:06:38 hal courierpop3login: Connection, ip=[::ffff:192.168.1.1]
Feb 19 00:06:38 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:06:38 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:06:45 hal courierpop3login: Connection, ip=[::ffff:192.168.1.1]
Feb 19 00:06:45 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:06:45 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max connection rate 1/60s for (smtp:130.207.165.183) at Feb 19 00:03:35
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max connection count 1 for (smtp:130.207.165.183) at Feb 19 00:03:35
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max cache size 2 at Feb 19 00:04:02

```

And just in case, mail.info:

```

Feb 19 00:03:35 hal postfix/smtpd[15415]: 700BD4F02E3: client=deliverator8.gatech.edu[130.207.165.183]
Feb 19 00:03:35 hal postfix/cleanup[15424]: 700BD4F02E3: message-id=<45D92F9E.2050505@clayscape.com>
Feb 19 00:03:35 hal postfix/smtpd[15415]: disconnect from deliverator8.gatech.edu[130.207.165.183]
Feb 19 00:03:35 hal postfix/qmgr[15275]: 700BD4F02E3: from=<clayton@clayscape.com>, size=1593, nrcpt=1 (queue active)
Feb 19 00:03:35 hal postfix/trivial-rewrite[15419]: warning: do not list domain clayscape.com in BOTH mydestination and virtual_mailbox_domains
Feb 19 00:03:35 hal postfix/local[15426]: 700BD4F02E3: to=<clayton@clayscape.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb 19 00:03:35 hal postfix/qmgr[15275]: 700BD4F02E3: removed
Feb 19 00:03:39 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:03:39 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:04:02 hal postfix/smtpd[15415]: connect from unknown[192.168.1.1]
Feb 19 00:04:03 hal postfix/smtpd[15415]: 1A02F4F02E3: client=unknown[192.168.1.1], sasl_method=PLAIN, sasl_username=clayton@clayscape.com
Feb 19 00:04:03 hal postfix/cleanup[15424]: 1A02F4F02E3: message-id=<45D92FBC.5050505@clayscape.com>
Feb 19 00:04:03 hal postfix/qmgr[15275]: 1A02F4F02E3: from=<clayton@clayscape.com>, size=537, nrcpt=1 (queue active)
Feb 19 00:04:03 hal postfix/smtpd[15415]: disconnect from unknown[192.168.1.1]
Feb 19 00:04:03 hal postfix/local[15426]: 1A02F4F02E3: to=<clayton@clayscape.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb 19 00:04:03 hal postfix/qmgr[15275]: 1A02F4F02E3: removed
Feb 19 00:04:06 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:04:06 hal courierpop3login: scancur opendir("cur"): No such file or directory  
Feb 19 00:06:35 hal postfix/smtpd[15438]: connect from unknown[192.168.1.1]
Feb 19 00:06:35 hal postfix/trivial-rewrite[15419]: warning: do not list domain clayscape.com in BOTH mydestination and virtual_mailbox_domains
Feb 19 00:06:35 hal postfix/smtpd[15438]: 9199D4F02E3: client=unknown[192.168.1.1], sasl_method=PLAIN, sasl_username=clayton@clayscape.com
Feb 19 00:06:35 hal postfix/cleanup[15445]: 9199D4F02E3: message-id=<45D93055.5090408@clayscape.com>
Feb 19 00:06:35 hal postfix/qmgr[15275]: 9199D4F02E3: from=<clayton@clayscape.com>, size=550, nrcpt=1 (queue active)
Feb 19 00:06:35 hal postfix/smtpd[15438]: disconnect from unknown[192.168.1.1]
Feb 19 00:06:35 hal postfix/local[15447]: 9199D4F02E3: to=<clayton@clayscape.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Feb 19 00:06:35 hal postfix/qmgr[15275]: 9199D4F02E3: removed
Feb 19 00:06:38 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:06:38 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:06:45 hal courierpop3login: LOGIN, user=clayton@clayscape.com, ip=[::ffff:192.168.1.1]
Feb 19 00:06:45 hal courierpop3login: scancur opendir("cur"): No such file or directory
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max connection rate 1/60s for (smtp:130.207.165.183) at Feb 19 00:03:35
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max connection count 1 for (smtp:130.207.165.183) at Feb 19 00:03:35
Feb 19 00:09:55 hal postfix/anvil[15418]: statistics: max cache size 2 at Feb 19 00:04:02

```

I had this working yesterday, but switched machines and I can't seem to duplicate my results.

Thanks for the help.

---

### Post by enriquecm on 2007-02-19
I think that u configured so quickly jejejejejje

First Check if u dont have a firewall ?

JEJEJEJE OK

OK first if u want IMAP and POP the COURIER package can give U

Only need install the package of POP
```
courier-pop
courier-pop-ssl
```

And configure

You need to check ure hostname 
> myhostname = clayscape.com

You can add ure lan networks 

> mynetworks = 127.0.0.0/8
mynetworks = 127.0.0.0/8, 192.168.1.0/24

---

