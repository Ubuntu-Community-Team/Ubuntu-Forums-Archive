---
title: "ISPConfig3 mail doesn't work"
date: 2011-05-22
forum: Server Platforms
---

### Post by pehden on 2011-05-22
postfix  
 ```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server.phossite.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server.phossite.net, localhost, localhost.localdomain
relayhost = mail.cableone.net
mynetworks = 127.0.0.0/8 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
message_size_limit = 0
smtp_sasl_auth_enable = no
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 


```

error 
with mail que
```

-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
85E8E392453C 865 Fri May 20 12:30:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27665-06 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27665-06 (in reply to end of DATA command))
www-data@phossite.net

828913924333 865 Fri May 20 04:30:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=26614-01 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=26614-01 (in reply to end of DATA command))
www-data@phossite.net

8A38E3924337 865 Fri May 20 05:10:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27224-08 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27224-08 (in reply to end of DATA command))
www-data@phossite.net

8030639243E1 865 Fri May 20 07:30:03 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27571-01 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27571-01 (in reply to end of DATA command))
www-data@phossite.net

601CF392450B 744 Fri May 20 08:54:41 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27571-06 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 411.): id=27571-06 (in reply to end of DATA command))
logs@pehden.net

6B6933924387 865 Fri May 20 06:00:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=26614-08 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=26614-08 (in reply to end of DATA command))
www-data@phossite.net

65B5239243E4 782 Fri May 20 07:43:29 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27665-04 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 292.): id=27665-04 (in reply to end of DATA command))
logs@pehden.net

69C5D3924511 865 Fri May 20 09:20:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=26107-12 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=26107-12 (in reply to end of DATA command))
www-data@phossite.net

65182392450E 865 Fri May 20 09:00:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27571-08 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27571-08 (in reply to end of DATA command))
www-data@phossite.net

622713924335 865 Fri May 20 05:00:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27665-01 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27665-01 (in reply to end of DATA command))
www-data@phossite.net

66115392452B 784 Fri May 20 11:53:14 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27665-05 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 322.): id=27665-05 (in reply to end of DATA command))
logs@pehden.net

6CAC73924519 986 Fri May 20 09:58:42 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27571-04 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 352.): id=27571-04 (in reply to end of DATA command))
logs@pehden.net

DFE1D3924392 865 Fri May 20 07:10:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=26863-05 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=26863-05 (in reply to end of DATA command))
www-data@phossite.net

DCA7D392451A 772 Fri May 20 09:59:12 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27665-02 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Error writing to socket: Broken pipe at (eval 113) line 200, line 59.): id=27665-02 (in reply to end of DATA command))
logs@pehden.net

D121439244BB 865 Fri May 20 08:50:02 www-data@phossite.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27571-05 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=27571-05 (in reply to end of DATA command))
www-data@phossite.net

DA2E13924527 758 Fri May 20 11:37:05 webmaster@pehden.net
(host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=27224-09 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 592.): id=27224-09 (in reply to end of DATA command))
logs@pehden.net


```

error-log

```

May 20 12:41:30 server imapd: pehden: No such file or directory
May 20 12:42:43 server postfix/smtpd[28329]: fatal: no SASL authentication mechanisms
May 20 12:43:44 server postfix/smtpd[28337]: fatal: no SASL authentication mechanisms
May 20 12:43:44 server postfix/smtpd[28336]: fatal: no SASL authentication mechanisms
May 20 12:44:45 server postfix/smtpd[28344]: fatal: no SASL authentication mechanisms
May 20 12:44:45 server postfix/smtpd[28345]: fatal: no SASL authentication mechanisms
May 20 12:45:33 server postfix/smtpd[28389]: fatal: no SASL authentication mechanisms
May 20 12:45:33 server postfix/smtpd[28390]: fatal: no SASL authentication mechanisms
May 20 12:45:46 server postfix/smtpd[28396]: fatal: no SASL authentication mechanisms
May 20 12:45:46 server postfix/smtpd[28397]: fatal: no SASL authentication mechanisms
May 20 12:45:46 server postfix/smtpd[28398]: fatal: no SASL authentication mechanisms

```

and mail log

```

May 20 12:47:48 server postfix/smtpd[28448]: connect from mail-iw0-f200.google.com[209.85.214.200]
May 20 12:47:48 server postfix/smtpd[28448]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:47:48 server postfix/smtpd[28448]: fatal: no SASL authentication mechanisms
May 20 12:47:49 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28446 exit status 1
May 20 12:47:49 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:47:49 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28447 exit status 1
May 20 12:47:49 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28448 exit status 1
May 20 12:48:50 server postfix/smtpd[28454]: connect from mail-vx0-f200.google.com[209.85.220.200]
May 20 12:48:50 server postfix/smtpd[28454]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:48:50 server postfix/smtpd[28454]: fatal: no SASL authentication mechanisms
May 20 12:48:51 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28454 exit status 1
May 20 12:48:51 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:50:02 server pop3d: Connection, ip=[::ffff:127.0.0.1]
May 20 12:50:02 server pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May 20 12:50:02 server imapd: Connection, ip=[::ffff:127.0.0.1]
May 20 12:50:02 server imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0
May 20 12:50:02 server postfix/smtpd[28493]: connect from localhost[127.0.0.1]
May 20 12:50:02 server postfix/smtpd[28493]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:50:02 server postfix/smtpd[28493]: fatal: no SASL authentication mechanisms
May 20 12:50:03 server postfix/pickup[27805]: 50D94392453D: uid=33 from=
May 20 12:50:03 server postfix/cleanup[28511]: 50D94392453D: message-id=<20110520175003.50D94392453D@server.phossite.net>
May 20 12:50:03 server postfix/qmgr[16930]: 50D94392453D: from=, size=865, nrcpt=1 (queue active)
May 20 12:50:03 server postfix/smtpd[28516]: connect from localhost[127.0.0.1]
May 20 12:50:03 server postfix/smtpd[28516]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:50:03 server postfix/smtpd[28516]: fatal: no SASL authentication mechanisms
May 20 12:50:03 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28493 exit status 1
May 20 12:50:03 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:50:04 server amavis[28226]: (28226-04) (!)FWD via SMTP: -> , 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28226-04
May 20 12:50:04 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28516 exit status 1
May 20 12:50:04 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:50:04 server amavis[28226]: (28226-04) Blocked MTA-BLOCKED, -> , Message-ID: <20110520175003.50D94392453D@server.phossite.net>, mail_id: iV68VVKP+Y07, Hits: -0.001, size: 865, 1120 ms
May 20 12:50:04 server postfix/smtp[28513]: 50D94392453D: to=, orig_to=, relay=127.0.0.1[127.0.0.1]:10024, delay=1.2, delays=0.03/0.01/0/1.1, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=28226-04 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28226-04 (in reply to end of DATA command))
May 20 12:50:31 server postfix/anvil[28006]: statistics: max connection rate 1/60s for (smtp:209.85.216.72) at May 20 12:41:25
May 20 12:50:31 server postfix/anvil[28006]: statistics: max connection count 1 for (smtp:209.85.216.72) at May 20 12:41:25
May 20 12:50:31 server postfix/anvil[28006]: statistics: max cache size 4 at May 20 12:46:47
May 20 12:50:31 server postfix/scache[28393]: statistics: start interval May 20 12:45:34
May 20 12:50:31 server postfix/scache[28393]: statistics: domain lookup hits=4 miss=2 success=66%
May 20 12:50:31 server postfix/scache[28393]: statistics: max simultaneous domains=1 addresses=1 connection=2
May 20 12:50:33 server postfix/qmgr[16930]: 828913924333: from=, size=865, nrcpt=1 (queue active)
May 20 12:50:33 server postfix/qmgr[16930]: DEECF392448A: from=, size=928, nrcpt=1 (queue active)
May 20 12:50:33 server postfix/qmgr[16930]: 3A9163924533: from=, size=865, nrcpt=1 (queue active)
May 20 12:51:04 server postfix/smtpd[28528]: connect from localhost[127.0.0.1]
May 20 12:51:04 server postfix/smtpd[28528]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:51:04 server postfix/smtpd[28528]: fatal: no SASL authentication mechanisms
May 20 12:51:04 server postfix/smtpd[28529]: connect from localhost[127.0.0.1]
May 20 12:51:04 server postfix/smtpd[28529]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:51:04 server postfix/smtpd[28529]: fatal: no SASL authentication mechanisms
May 20 12:51:05 server amavis[28225]: (28225-04) (!)FWD via SMTP: -> , 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28225-04
May 20 12:51:05 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28528 exit status 1
May 20 12:51:05 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:51:05 server amavis[28225]: (28225-04) Blocked MTA-BLOCKED, -> , Message-ID: <20110520093002.828913924333@server.phossite.net>, mail_id: mjhDp4aWi7KB, Hits: -0.001, size: 865, 32280 ms
May 20 12:51:05 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28529 exit status 1
May 20 12:51:05 server amavis[28226]: (28226-05) (!)FWD via SMTP: -> , 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 205.): id=28226-05
May 20 12:51:05 server postfix/smtp[28513]: 828913924333: to=, orig_to=, relay=127.0.0.1[127.0.0.1]:10024, delay=30063, delays=30031/0.01/0.02/32, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=28225-04 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28225-04 (in reply to end of DATA command))
May 20 12:51:05 server amavis[28226]: (28226-05) Blocked MTA-BLOCKED, -> , Message-ID: <20110520130223.DEECF392448A@server.phossite.net>, mail_id: SKf-OW+NNRxk, Hits: 0.001, size: 927, 32308 ms
May 20 12:51:05 server postfix/smtp[28519]: DEECF392448A: to=, relay=127.0.0.1[127.0.0.1]:10024, delay=17322, delays=17290/0.04/0.01/32, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=28226-05 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596, line 205.): id=28226-05 (in reply to end of DATA command))
May 20 12:51:40 server amavis[28225]: (28225-05) (!)rw_loop: leaving rw loop, no progress, last event (select) 35.035 s ago
May 20 12:51:40 server amavis[28225]: (28225-05) (!)FWD via SMTP: -> , 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28225-05
May 20 12:51:40 server amavis[28225]: (28225-05) Blocked MTA-BLOCKED, -> , Message-ID: <20110520174003.3A9163924533@server.phossite.net>, mail_id: HR9e2rmLdrva, Hits: -0.001, size: 865, 35155 ms
May 20 12:51:40 server postfix/smtp[28513]: 3A9163924533: to=, orig_to=, relay=127.0.0.1[127.0.0.1]:10024, delay=698, delays=630/32/0.05/35, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 id=28225-05 - Temporary MTA failure on relaying, From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: at (eval 113) line 596.): id=28225-05 (in reply to end of DATA command))
May 20 12:51:47 server amavis[28225]: (28225-05) (!)rw_loop: leaving rw loop, no progress, last event (select) 5.005 s ago
May 20 12:52:05 server postfix/smtpd[28557]: connect from localhost[127.0.0.1]
May 20 12:52:05 server postfix/smtpd[28557]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:52:05 server postfix/smtpd[28557]: fatal: no SASL authentication mechanisms
May 20 12:52:06 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28557 exit status 1
May 20 12:52:06 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:52:14 server postfix/smtpd[28558]: connect from smtprelay00.siteprotect.com[64.26.28.5]
May 20 12:52:14 server postfix/smtpd[28558]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:52:14 server postfix/smtpd[28558]: fatal: no SASL authentication mechanisms
May 20 12:52:15 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28558 exit status 1
May 20 12:52:15 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:53:15 server postfix/smtpd[28566]: connect from mail-px0-f200.google.com[209.85.212.200]
May 20 12:53:15 server postfix/smtpd[28566]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:53:15 server postfix/smtpd[28566]: fatal: no SASL authentication mechanisms
May 20 12:53:16 server postfix/smtpd[28567]: connect from utuaoteolopuka.mailfwd.taloha.net[216.75.55.110]
May 20 12:53:16 server postfix/smtpd[28567]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:53:16 server postfix/smtpd[28567]: fatal: no SASL authentication mechanisms
May 20 12:53:16 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28566 exit status 1
May 20 12:53:16 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:53:17 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28567 exit status 1
May 20 12:54:16 server postfix/smtpd[28574]: connect from mail-iw0-f200.google.com[209.85.214.200]
May 20 12:54:16 server postfix/smtpd[28574]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:54:16 server postfix/smtpd[28574]: fatal: no SASL authentication mechanisms
May 20 12:54:16 server postfix/smtpd[28575]: connect from mail-yi0-f48.google.com[209.85.218.48]
May 20 12:54:16 server postfix/smtpd[28575]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:54:16 server postfix/smtpd[28575]: fatal: no SASL authentication mechanisms
May 20 12:54:16 server postfix/smtpd[28576]: connect from alias1.c17-ave-mta-out2.cnet.com[216.239.114.77]
May 20 12:54:16 server postfix/smtpd[28576]: warning: SASL: Connect to private/auth failed: No such file or directory
May 20 12:54:16 server postfix/smtpd[28576]: fatal: no SASL authentication mechanisms
May 20 12:54:17 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28574 exit status 1
May 20 12:54:17 server postfix/master[16926]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
May 20 12:54:17 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28575 exit status 1
May 20 12:54:17 server postfix/master[16926]: warning: process /usr/lib/postfix/smtpd pid 28576 exit status 1
May 20 12:54:25 server postfix/scache[28530]: statistics: start interval May 20 12:51:05
May 20 12:54:25 server postfix/scache[28530]: statistics: domain lookup hits=0 miss=1 success=0%
May 20 12:54:25 server postfix/scache[28530]: statistics: max simultaneous domains=1 addresses=1 connection=1
May 20 12:55:02 server pop3d: Connection, ip=[::ffff:127.0.0.1]
May 20 12:55:02 server pop3d: Disconnected, ip=[::ffff:127.0.0.1]
May 20 12:55:02 server imapd: Connection, ip=[::ffff:127.0.0.1]
May 20 12:55:02 server imapd: Disconnected, ip=[::ffff:127.0.0.1], time=0

```


hostname

server.phossite.net

mailname

phossite.net

hostname -f
server.phossite.net



Followed [http://www.ispconfig.org/news/tutorial-the-perfect-server-ubuntu-11-04-ispconfig-3/](http://www.ispconfig.org/news/tutorial-the-perfect-server-ubuntu-11-04-ispconfig-3/) 
ubuntu 11.04 server

---

### Post by pehden on 2011-05-25
Bump.

---

### Post by user4572 on 2011-05-27
I had the exact same thing...perfect server 10.10 - ISPConfig3.
 
I gave it four days and went back to the old system. Never did figure it out. When I get time I'll look into it more.

---

