---
title: "Mail server unable to receive mails"
date: 2008-11-13
forum: Server Platforms
---

### Post by satimis on 2008-11-13
Hi folks,


I'm following;
[http://flurdy.com/docs/postfix/edition5.html](http://flurdy.com/docs/postfix/edition5.html)

building a mail server running postfix virtual.  The server can send mails via telnet but unable to receive mails.


# tail /var/log/mail.log```

Nov 14 04:35:58 xen05 postfix/master[2761]: daemon started -- version 2.3.8, configuration /etc/postfix
Nov 14 04:35:59 xen05 spamd[2527]: spamd: server started on port 783/tcp (running version 3.1.7-deb)
Nov 14 04:35:59 xen05 spamd[2527]: spamd: server pid: 2527
Nov 14 04:35:59 xen05 spamd[2527]: spamd: server successfully spawned child process, pid 2774
Nov 14 04:35:59 xen05 spamd[2527]: spamd: server successfully spawned child process, pid 2775
Nov 14 04:35:59 xen05 spamd[2527]: prefork: child states: IS
Nov 14 04:35:59 xen05 spamd[2527]: prefork: child states: II
Nov 14 04:40:31 xen05 postfix/smtpd[3089]: connect from web35206.mail.mud.yahoo.com[66.163.179.85]
Nov 14 04:40:33 xen05 postfix/smtpd[3089]: NOQUEUE: reject: RCPT from web35206.mail.mud.yahoo.com[66.163.179.85]: 554 5.7.1 <satimis@satimis.com>: Relay access denied; from=<satimis@yahoo.com> to=<satimis@satimis.com> proto=SMTP helo=<web35206.mail.mud.yahoo.com>
Nov 14 04:40:33 xen05 postfix/smtpd[3089]: disconnect from web35206.mail.mud.yahoo.com[66.163.179.85]

```


# tail /var/log/mysql.log
# tail /var/log/mysql.err
both without printout


# grep mydestination /etc/postfix/main.cf```

#mydestination = $myhostname, localhost.$mydomain, localhost, satimis.com
mydestination =

```


# grep relayhost /etc/postfix/main.cf```

relayhost =

```


If "mydestination = $myhostname, localhost.$mydomain, localhost, satimis.com", then mails can be received on /var/spool/mail/ directory.  But this server is running postfix virtual.  It must be "mydestination =" and incoming mails should be delivered to /var/spool/mail/virtual/ directory.


I have been trying and googling couple days without a solution.  Please help.  TIA


B.R.
satimis

---

### Post by hictio on 2008-11-14
A couple of questions:

- Can you connect to the port 25 of the server? I mean, using the public IP address or the registered hostname.
- Does the server have FQDN hostname?
- Is the server registered as the MX server for the domain it is working as the mailserver for?

---

### Post by satimis on 2008-11-14
> **hictio said:**
> A couple of questions:

- Can you connect to the port 25 of the server? I mean, using the public IP address or the registered hostname.


$ telnet xen05.satimis.com 25```

Trying 192.168.0.205...
Connected to xen05.satimis.com.
Escape character is '^]'.
220 xen05.satimis.com ESMTP Postfix (Debian/GNU)
ehlo xen05.satimis.com
250-xen05.satimis.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
250-AUTH=PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: satimis@satimis.com
250 2.1.0 Ok
rcpt to: satimis@yahoo.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: xen05 14-01

xen05 14-01
.
250 2.0.0 Ok: queued as BBA94782D1
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

Mail sent and received on Yahoo.


$ tail /var/log/mail.log```

Nov 14 06:25:05 xen05 postfix/smtp[3313]: F34A2782FF: to=<root@xen05.satimis.com>, relay=xen05.satimis.com[220.232.213.178]:25, delay=0.07, delays=0/0/0.06/0, dsn=5.4.6, status=bounced (mail for xen05.satimis.com loops back to myself)
Nov 14 06:25:05 xen05 postfix/qmgr[2768]: F34A2782FF: removed
Nov 14 06:25:05 xen05 postfix/smtpd[3314]: disconnect from unknown[220.232.213.178]
Nov 14 06:26:11 xen05 postfix/smtpd[3183]: BBA94782D1: client=xen05.satimis.com[192.168.0.205]
Nov 14 06:26:47 xen05 postfix/cleanup[3311]: BBA94782D1: message-id=<20081114062611.BBA94782D1@xen05.satimis.com>
Nov 14 06:26:47 xen05 postfix/qmgr[2768]: BBA94782D1: from=<satimis@satimis.com>, size=391, nrcpt=1 (queue active)
Nov 14 06:26:48 xen05 postfix/smtp[3319]: BBA94782D1: host b.mx.mail.yahoo.com[66.196.97.250] refused to talk to me: 421 Message from (220.232.213.178) temporarily deferred - 4.16.50. Please refer to http://help.yahoo.com/help/us/mail/defer/defer-06.html
Nov 14 06:26:50 xen05 postfix/smtp[3319]: BBA94782D1: to=<satimis@yahoo.com>, relay=a.mx.mail.yahoo.com[67.195.168.31]:25, delay=60, delays=57/0.01/1.7/0.77, dsn=2.0.0, status=sent (250 ok dirdel)
Nov 14 06:26:50 xen05 postfix/qmgr[2768]: BBA94782D1: removed
Nov 14 06:26:51 xen05 postfix/smtpd[3183]: disconnect from xen05.satimis.com[192.168.0.205]
```


$ telnet 220.232.213.178 25```

Trying 220.232.213.178...
Connected to 220.232.213.178.
Escape character is '^]'.
220 xen05.satimis.com ESMTP Postfix (Debian/GNU)
ehlo 220.232.213.178
250-xen05.satimis.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
250-AUTH=PLAIN NTLM LOGIN DIGEST-MD5 CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: satimis@satimis.com
250 2.1.0 Ok
rcpt to: satimis@yahoo.com
554 5.7.1 <satimis@yahoo.com>: Relay access denied

```

It is hanging here.


On another terminal;

# tail /var/log/mail.log```

Nov 14 06:26:48 xen05 postfix/smtp[3319]: BBA94782D1: host b.mx.mail.yahoo.com[66.196.97.250] refused to talk to me: 421 Message from (220.232.213.178) temporarily deferred - 4.16.50. Please refer to http://help.yahoo.com/help/us/mail/defer/defer-06.html
Nov 14 06:26:50 xen05 postfix/smtp[3319]: BBA94782D1: to=<satimis@yahoo.com>, relay=a.mx.mail.yahoo.com[67.195.168.31]:25, delay=60, delays=57/0.01/1.7/0.77, dsn=2.0.0, status=sent (250 ok dirdel)
Nov 14 06:26:50 xen05 postfix/qmgr[2768]: BBA94782D1: removed
Nov 14 06:26:51 xen05 postfix/smtpd[3183]: disconnect from xen05.satimis.com[192.168.0.205]
Nov 14 06:28:25 xen05 postfix/anvil[3315]: statistics: max connection rate 2/60s for (smtp:220.232.213.178) at Nov 14 06:25:05
Nov 14 06:28:25 xen05 postfix/anvil[3315]: statistics: max connection count 1 for (smtp:220.232.213.178) at Nov 14 06:25:04
Nov 14 06:28:25 xen05 postfix/anvil[3315]: statistics: max cache size 1 at Nov 14 06:25:04
Nov 14 06:53:00 xen05 postfix/smtpd[3333]: connect from unknown[220.232.213.178]
Nov 14 06:54:20 xen05 postfix/smtpd[3333]: NOQUEUE: reject_warning: RCPT from unknown[220.232.213.178]: 504 5.5.2 <220.232.213.178>: Helo command rejected: need fully-qualified hostname; from=<satimis@satimis.com> to=<satimis@yahoo.com> proto=ESMTP helo=<220.232.213.178>
Nov 14 06:54:21 xen05 postfix/smtpd[3333]: NOQUEUE: reject: RCPT from unknown[220.232.213.178]: 554 5.7.1 <satimis@yahoo.com>: Relay access denied; from=<satimis@satimis.com> to=<satimis@yahoo.com> proto=ESMTP helo=<220.232.213.178>

```



> 
- Does the server have FQDN hostname?

Yes, satimis.com


> 
- Is the server registered as the MX server for the domain it is working as the mailserver for?

No, this is NOT a mail exchange server.  It is a mail server for multi domains running as guest on a Xen box.  All ports on the external IP are forwarded to its local IP, 192.168.0.205


B.R.
satimis

---

### Post by MJN on 2008-11-14
> **satimis said:**
> If "mydestination = $myhostname, localhost.$mydomain, localhost, satimis.com", then mails can be received on /var/spool/mail/ directory. But this server is running postfix virtual. It must be "mydestination =" and incoming mails should be delivered to /var/spool/mail/virtual/ directory.You've pretty much answered your own question.
 
Postfix needs to know what it is the final destination for otherwise it will assume a relay attempt and refuse. So, whilst you have removed the 'real' destination directive of $mydestination chances are you have not configured the 'virtual' destinations correctly and hence Postfix is unaware of its responsibilities.
 
Post the whole Postfix main.cf config and we can take a look.
 
Mathew

---

### Post by satimis on 2008-11-14
Hi Mathew,


> **MJN said:**
> You've pretty much answered your own question.
 
Postfix needs to know what it is the final destination for otherwise it will assume a relay attempt and refuse. So, whilst you have removed the 'real' destination directive of $mydestination chances are you have not configured the 'virtual' destinations correctly and hence Postfix is unaware of its responsibilities.


```

virtual_mailbox_base = /var/spool/mail/virtual

```
is on main.cf.  It doesn't work.


>  
Post the whole Postfix main.cf config and we can take a look.


# postconf -n```

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = xen05.satimis.com
mynetworks = 192.168.0.0/24, 127.0.0.0/8 ##
mynetworks_style = host
relayhost =
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```


# /home/satimis/postfinger```

postfinger - postfix configuration on Fri Nov 14 12:45:39 UTC 2008
version: 1.30

--System Parameters--
mail_version = 2.3.8
hostname = xen05.satimis.com
uname = Linux xen05.satimis.com 2.6.18-xen #1 SMP Fri May 18 16:11:33 BST 2007 i686 GNU/Linux

--Packaging information--
looks like this postfix comes from deb package: postfix-ii  postfix                     2.3.8-2+etch1 A high-performance mail transport agent

--main.cf non-default parameters--
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
broken_sasl_auth_clients = yes
delay_warning_time = 4h
disable_vrfy_command = yes
local_recipient_maps =
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
mydestination =
mynetworks = 192.168.0.0/24, 127.0.0.0/8 ##
mynetworks_style = host
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes
smtp_helo_timeout = 60s
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

--master.cf--
smtp      inet  n       -       n       -       -       smtpd
smtps     inet  n       -       n       -       -       smtpd
    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
587       inet  n       -       n       -       -       smtpd
    -o smtpd_enforce_tls=yes
    -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
amavis    unix  -       -       -       -       2       smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
    -o content_filter=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o smtpd_restriction_classes=
    -o smtpd_client_restrictions=
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o strict_rfc821_envelopes=yes
    -o mynetworks=127.0.0.0/8
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1001
pre-cleanup unix n      -       -       -       0       cleanup
    -o virtual_alias_maps=
    -o canonical_maps=
    -o sender_canonical_maps=
    -o recipient_canonical_maps=
    -o masquerade_domains=

-- end of postfinger output --

```

# cat /etc/postfix/mysql_domains.cf```

user=mail
password=mailpasswd
dbname=maildb
table=domains
select_field=domain
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1

```


# cat /etc/postfix/mysql_mailbox.cf```

user=mail
password=mailpasswd
dbname=maildb
table=users
select_field=maildir
where_field=id hosts=127.0.0.1
additional_conditions = and enabled = 1

```


B.R.
satimis

---

### Post by MJN on 2008-11-14
> **satimis said:**
> ```

virtual_mailbox_base = /var/spool/mail/virtual

```
is on main.cf. It doesn't work.It wouldn't. That directive just states where the mail should end up, not what recipient domains are acceptable.
 
As you're using MySQL to store your user/domain details, has satimis.com been entered as a valid destination domain into your 'domains' table?
 
Mathew

---

### Post by satimis on 2008-11-14
> **MJN said:**
> It wouldn't. That directive just states where the mail should end up, not what recipient domains are acceptable.
 
As you're using MySQL to store your user/domain details, has satimis.com been entered as a valid destination domain into your 'domains' table?


# mysql -u root -p
Enter password:

mysql> USE maildb
Database changed

mysql> show tables;```

+------------------+
| Tables_in_maildb |
+------------------+
| aliases          |
| domains          |
| users            |
+------------------+
3 rows in set (0.00 sec)

```


mysql> SELECT * from domains;```

+------+-----------------------+-----------+---------+
| pkid | domain                | transport | enabled |
+------+-----------------------+-----------+---------+
|    1 | localhost             | virtual:  |       1 |
|    2 | localhost.localdomain | virtual:  |       1 |
|    3 | satimis.com.tld       | virtual:  |       1 |
+------+-----------------------+-----------+---------+
3 rows in set (0.00 sec)

```

Here I have a doubt.  Whether ".tld" (top_level_domain) should be drop.  If YES what command shall I run on MySQL to delete it?  Thanks


mysql> SELECT * from users;```

+---------------------+---------+------+------+-------------------------+----------+---------+-----------------+------------+---------------+-------+------------+----------------+
| id                  | name    | uid  | gid  | home                    | maildir  | enabled | change_password | clear      | crypt         | quota | procmailrc | spamassassinrc |
+---------------------+---------+------+------+-------------------------+----------+---------+-----------------+------------+---------------+-------+------------+----------------+
| root@localhost      | root    | 5000 | 5000 | /var/spool/mail/virtual | root/    |       1 |               1 | x05root    | sdtrusfX0Jj66 |       |            |                |
| satimis@satimis.com | Stephen | 5000 | 5000 | /var/spool/mail/virtual | Stephen/ |       1 |               1 | x05satimis | sdtrusfX0Jj66 |       |            |                |
+---------------------+---------+------+------+-------------------------+----------+---------+-----------------+------------+---------------+-------+------------+----------------+
2 rows in set (0.00 sec)
```


mysql> SELECT * from aliases;```

+------+----------------------------+--------------------------+---------+
| pkid | mail                       | destination              | enabled |
+------+----------------------------+--------------------------+---------+
|    1 | postmaster@localhost       | root@localhost           |       1 |
|    2 | sysadmin@localhost         | root@localhost           |       1 |
|    3 | webmaster@localhost        | root@localhost           |       1 |
|    4 | abuse@localhost            | root@localhost           |       1 |
|    5 | root@localhost             | root@localhost           |       1 |
|    6 | @localhost                 | root@localhost           |       1 |
|    7 | @localhost.localdomain     | @localhost               |       1 |
|    8 | @satimis.com.tld           | satimisowner@satimis.com |       1 |
|    9 | postmaster@satimis.com.tld | postmaster@satimis.com   |       1 |
|   10 | abuse@satimis.com.tld      | abuse@satimis.com        |       1 |
|   11 | stephen@satimis.com        | soduer@satimis.com       |       1 |
+------+----------------------------+--------------------------+---------+
11 rows in set (0.00 sec)

```

Again whether ".tld" should be dropped.


satimis

---

### Post by MJN on 2008-11-14
> **satimis said:**
> ```

+------+-----------------------+-----------+---------+
| pkid | domain | transport | enabled |
+------+-----------------------+-----------+---------+
| 1 | localhost | virtual: | 1 |
| 2 | localhost.localdomain | virtual: | 1 |
| 3 | satimis.com.tld | virtual: | 1 |
+------+-----------------------+-----------+---------+
3 rows in set (0.00 sec)

```
 
Here I have a doubt. Whether ".tld" (top_level_domain) should be drop.
 
Absolutely. Without 'satimis.com' in the table Postfix thinks it's a foreign domain.
 
> If YES what command shall I run on MySQL to delete it? ThanksI don't use MySQL so don't know. However, it's got to be pretty trivial so given you use it I'll leave the Googling to you as you're going to need to get to grips with the basics anyway (the DELETE command, or even REPLACE, are what you're looking for).
 
At the very least you could go through your INSERT process once more and add satimis.com as a new domain.
 
Mathew

---

### Post by satimis on 2008-11-15
> **MJN said:**
> Absolutely. Without 'satimis.com' in the table Postfix thinks it's a foreign domain.
 
I don't use MySQL so don't know. However, it's got to be pretty trivial so given you use it I'll leave the Googling to you as you're going to need to get to grips with the basics anyway (the DELETE command, or even REPLACE, are what you're looking for).
 
At the very least you could go through your INSERT process once more and add satimis.com as a new domain.


Hi Mathew,


Changes made on MySQL


Made following test;


On MySQL

mysql> show tables;```

+------------------+
| Tables_in_maildb |
+------------------+
| aliases          |
| domains          |
| users            |
+------------------+
3 rows in set (0.00 sec)

```


changed;```


mysql> SELECT * from domains;
+------+-----------------------+-----------+---------+
| pkid | domain                | transport | enabled |
+------+-----------------------+-----------+---------+
|    1 | localhost             | virtual:  |       1 |
|    2 | localhost.localdomain | virtual:  |       1 |
|    3 | satimis.com.tld       | virtual:  |       1 |
+------+-----------------------+-----------+---------+
3 rows in set (0.00 sec)

```

to;```

mysql> SELECT * from domains;
+------+-----------------------+-----------+---------+
| pkid | domain                | transport | enabled |
+------+-----------------------+-----------+---------+
|    1 | localhost             | virtual:  |       1 |
|    2 | localhost.localdomain | virtual:  |       1 |
|    3 | satimis.com           | virtual:  |       1 |
+------+-----------------------+-----------+---------+
3 rows in set (0.00 sec)

```


and


change;```

mysql> SELECT * from aliases;
+------+----------------------------+--------------------------+---------+
| pkid | mail                       | destination              | enabled |
+------+----------------------------+--------------------------+---------+
|    1 | postmaster@localhost       | root@localhost           |       1 |
|    2 | sysadmin@localhost         | root@localhost           |       1 |
|    3 | webmaster@localhost        | root@localhost           |       1 |
|    4 | abuse@localhost            | root@localhost           |       1 |
|    5 | root@localhost             | root@localhost           |       1 |
|    6 | @localhost                 | root@localhost           |       1 |
|    7 | @localhost.localdomain     | @localhost               |       1 |
|    8 | @satimis.com               | satimisowner@satimis.com |       1 |
|    9 | postmaster@satimis.com.tld | postmaster@satimis.com   |       1 |
|   10 | abuse@satimis.com.tld      | abuse@satimis.com        |       1 |
|   11 | stephen@satimis.com        | soduer@satimis.com       |       1 |
+------+----------------------------+--------------------------+---------+
11 rows in set (0.00 sec)

```


to;```

mysql> SELECT * from aliases;
+------+------------------------+--------------------------+---------+
| pkid | mail                   | destination              | enabled |
+------+------------------------+--------------------------+---------+
|    1 | postmaster@localhost   | root@localhost           |       1 |
|    2 | sysadmin@localhost     | root@localhost           |       1 |
|    3 | webmaster@localhost    | root@localhost           |       1 |
|    4 | abuse@localhost        | root@localhost           |       1 |
|    5 | root@localhost         | root@localhost           |       1 |
|    6 | @localhost             | root@localhost           |       1 |
|    7 | @localhost.localdomain | @localhost               |       1 |
|    8 | @satimis.com           | satimisowner@satimis.com |       1 |
|    9 | postmaster@satimis.com | postmaster@satimis.com   |       1 |
|   10 | abuse@satimis.com      | abuse@satimis.com        |       1 |
|   11 | stephen@satimis.com    | soduer@satimis.com       |       1 |
+------+------------------------+--------------------------+---------+
11 rows in set (0.00 sec)

```


# postconf -n```

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = xen05.satimis.com
mynetworks = 192.168.0.0/24, 127.0.0.0/8 ##
mynetworks_style = host
relayhost =
smtp_helo_timeout = 60s
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permitsmtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```


# postfix reload
postfix/postfix-script: refreshing the Postfix mail system

# postfix check

# tail /var/log/mail.log```

Nov 15 07:14:22 xen05 postfix/smtpd[3380]: disconnect from unknown[121.24.66.55]
Nov 15 07:17:42 xen05 postfix/anvil[3381]: statistics: max connection rate 1/60s for (smtp:121.24.66.55) at Nov 15 07:14:19
Nov 15 07:17:42 xen05 postfix/anvil[3381]: statistics: max connection count 1 for (smtp:121.24.66.55) at Nov 15 07:14:19
Nov 15 07:17:42 xen05 postfix/anvil[3381]: statistics: max cache size 1 at Nov 15 07:14:19
Nov 15 07:20:00 xen05 postfix/postfix-script: refreshing the Postfix mail system
Nov 15 07:20:00 xen05 postfix/master[2775]: reload configuration /etc/postfix
Nov 15 07:20:00 xen05 postfix/qmgr[3394]: B3F6E78304: from=<satimis@yahoo.com>, size=1431, nrcpt=1 (queue active)
Nov 15 07:20:01 xen05 postfix/virtual[3396]: warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'hosts=127.0.0.1='root@satimis.com' and enabled = 1' at line 1
Nov 15 07:20:01 xen05 postfix/virtual[3396]: warning: table virtual_mailbox_maps: lookup root@satimis.com: Success
Nov 15 07:20:01 xen05 postfix/virtual[3396]: B3F6E78304: to=<root@satimis.com>, relay=virtual, delay=7240, delays=7240/0.03/0/0.11, dsn=4.3.5, status=deferred (mail system configuration error)

```

Error indicated.


Sent a mail to [email]satimis@satimis.com[/email] on Gmail.


# tail /var/log/mail.log```

Nov 15 07:23:25 xen05 postfix/smtpd[3471]: disconnect from localhost.localdomain[127.0.0.1]
Nov 15 07:23:25 xen05 postfix/qmgr[3394]: 4258778309: from=<satimisliu@gmail.com>, size=2217, nrcpt=1 (queue active)
Nov 15 07:23:25 xen05 amavis[2412]: (02412-01) FWD via SMTP: <satimisliu@gmail.com> -> <satimis@satimis.com>, 250 2.6.0 Ok, id=02412-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4258778309
Nov 15 07:23:25 xen05 postfix/virtual[3472]: warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'hosts=127.0.0.1='satimis@satimis.com' and enabled = 1' at line 1
Nov 15 07:23:25 xen05 postfix/virtual[3472]: warning: table virtual_mailbox_maps: lookup satimis@satimis.com: Success
Nov 15 07:23:25 xen05 amavis[2412]: (02412-01) Passed CLEAN, [209.85.198.247] [209.85.198.247] <satimisliu@gmail.com> -> <satimis@satimis.com>, Message-ID: <ca46cd50811142318v2126b94dqd99a0bdb92ffbae2@mail.gmail.com>, mail_id: F4+fUTBje8c5, Hits: -, queued_as: 4258778309, 892 ms
Nov 15 07:23:25 xen05 amavis[2412]: (02412-01) TIMING [total 911 ms] - SMTP EHLO: 151 (17%)17, SMTP pre-MAIL: 1 (0%)17, mkdir tempdir: 4 (0%)17, create email.txt: 3 (0%)18, SMTP pre-DATA-flush: 8 (1%)18, SMTP DATA: 19 (2%)21, body_digest: 4 (0%)21, gen_mail_id: 2 (0%)21, mkdir parts: 0 (0%)21, mime_decode: 53 (6%)27, get-file-type1: 78 (9%)36, parts_decode: 0 (0%)36, update_cache: 8 (1%)37, decide_mail_destiny: 1 (0%)37, fwd-connect: 171 (19%)55, fwd-mail-from: 6 (1%)56, fwd-rcpt-to: 210 (23%)79, fwd-data-cmd: 1 (0%)79, write-header: 3 (0%)80, fwd-data-contents: 2 (0%)80, fwd-data-end: 40 (4%)84, fwd-rundown: 7 (1%)85, prepare-dsn: 4 (0%)85, main_log_entry: 115 (13%)98, update_snmp: 12 (1%)99, unlink-1-files: 5 (1%)100, rundown: 2 (0%)100
Nov 15 07:23:25 xen05 postfix/smtp[3469]: 0288678306: to=<satimis@satimis.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=2, delays=0.96/0.01/0.29/0.76, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=02412-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4258778309)
Nov 15 07:23:25 xen05 postfix/qmgr[3394]: 0288678306: removed
Nov 15 07:23:25 xen05 postfix/virtual[3472]: 4258778309: to=<satimis@satimis.com>, relay=virtual, delay=0.43, delays=0.26/0.03/0/0.14, dsn=4.3.5, status=deferred (mail system configuration error)

```


Mail arrived saying "table virtual_mailbox_maps: lookup [email]satimis@satimis.co[/email] m: Success ....".  But can't find it nor being rejected to Gmail.  I think it is bouncing on Internet.


# /home/satimis/postfinger```

postfinger - postfix configuration on Sat Nov 15 07:49:09 UTC 2008
version: 1.30

--System Parameters--
mail_version = 2.3.8
hostname = xen05.satimis.com
uname = Linux xen05.satimis.com 2.6.18-xen #1 SMP Fri May 18 16:11:33 BST 2007 i686 GNU/Linux

--Packaging information--
looks like this postfix comes from deb package: postfix-ii  postfix         2.3.8-2+etch1               A high-performance mail transport agent

--main.cf non-default parameters--
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
broken_sasl_auth_clients = yes
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
local_recipient_maps =
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
mydestination =
mynetworks = 192.168.0.0/24, 127.0.0.0/8 ##
mynetworks_style = host
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permitsmtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes
smtp_helo_timeout = 60s
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

--master.cf--
smtp      inet  n       -       n       -       -       smtpd
smtps     inet  n       -       n       -       -       smtpd
    -o smtpd_tls_wrappermode=yes
    -o smtpd_sasl_auth_enable=yes
587       inet  n       -       n       -       -       smtpd
    -o smtpd_enforce_tls=yes
    -o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipientscalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
amavis    unix  -       -       -       -       2       smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
    -o content_filter=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o smtpd_restriction_classes=
    -o smtpd_client_restrictions=
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o strict_rfc821_envelopes=yes
    -o mynetworks=127.0.0.0/8
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1001
pre-cleanup unix n      -       -       -       0       cleanup
    -o virtual_alias_maps=
    -o canonical_maps=
    -o sender_canonical_maps=
    -o recipient_canonical_maps=
    -o masquerade_domains=

-- end of postfinger output --

```


# mysql -h 127.0.0.1 -u satimis -pemmanuel```

ERROR 1045 (28000): Access denied for user 'satimis'@'localhost' (using password : YES)

```

satimis is not an user of MySQL.


# mysql -h 127.0.0.1 -u root -pemmanuel```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: Y ES)

```

It is the same.


# postconf -d | grep mail_version```

mail_version = 2.3.8

```


B.R.
satimis

---

### Post by MJN on 2008-11-15
Flippin' eck Satimis - you seem to be at the other end of the spectrum to those users who don't provide enough information with their queries... I don't know which is worse! ;-)

As mentioned I don't use MySQL and so am not in a good position to be able to tell you why your SQL queries aren't working. Hopefully someone with experience in this area can check through your code and syntax but in the meantime I would suggest double-checking with your HowTo that you have not made any errors in these areas.

Mathew

---

### Post by satimis on 2008-11-15
Hi Mathew and folks,


Problem SOLVED


mail.log```

....
warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'hosts=127.0.0.1='satimis@satimis.com' and enabled = 1' at line 1
...

```

already indicating a hint.  The problem came from mysql_*cf files.  This time google did not help me.  Finally I have to check each mysql_*cf and found on mysql_mailbox.cf```

..
where_field=id  hosts=127.0.0.1
...

```
on the same line.

Changed it as.```

..
where_field=id
hosts=127.0.0.1
...

```


Ran;
# /etc/init.d/mysql reload

# postfix reload
# postfix check

to make sure no mistake.


Sent a mail to [email]satimis@satimis.com[/email] on Gmail.


# tail /var/log/mail.log```

Nov 15 13:29:29 xen05 postfix/qmgr[4756]: E51A57830A: from=<>, size=4241, nrcpt=1 (queue active)
Nov 15 13:29:29 xen05 postfix/qmgr[4756]: E51EF78310: from=<>, size=4244, nrcpt=1 (queue active)
Nov 15 13:29:31 xen05 postfix/smtp[4848]: E51EF78310: to=<satimisliu@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.143.27]:25, delay=1.8, delays=0.07/0.02/0.29/1.5, dsn=2.0.0, status=sent (250 2.0.0 OK 1226755489 b4si4697531tic.2)
Nov 15 13:29:31 xen05 postfix/qmgr[4756]: E51EF78310: removed
Nov 15 13:29:31 xen05 postfix/smtp[4847]: E51A57830A: to=<satimisliu@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.143.27]:25, delay=1.9, delays=0.06/0.02/0.31/1.5, dsn=2.0.0, status=sent (250 2.0.0 OK 1226755489 i9si555433tid.9)
Nov 15 13:29:31 xen05 postfix/qmgr[4756]: E51A57830A: removed
Nov 15 13:43:51 xen05 postfix/master[2775]: reload configuration /etc/postfix
Nov 15 13:43:51 xen05 postfix/qmgr[4889]: ABE8B7830F: from=<satimisliu@gmail.com>, size=2215, nrcpt=1 (queue active)
Nov 15 13:43:51 xen05 postfix/virtual[4893]: ABE8B7830F: to=<satimis@satimis.com>, relay=virtual, delay=1744, delays=1744/0.03/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Nov 15 13:43:51 xen05 postfix/qmgr[4889]: ABE8B7830F: removed

```

Mail arrived on;

# ls /var/spool/mail/virtual/Stephen/```

cur  new  tmp

```

Directories automatically created.

# ls /var/spool/mail/virtual/Stephen/new/```

1226756631.V301I7c135M921128.xen05.satimis.com

```

That is the new mail.


Now the mail server can send and receive mails.  This is my 5th round building Postfix virtual.  There is still a long way ahead.


B.R.
satimis

---

