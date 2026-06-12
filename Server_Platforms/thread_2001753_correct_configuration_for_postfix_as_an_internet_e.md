---
title: "correct configuration for postfix as an internet email server"
date: 2012-06-11
forum: Server Platforms
---

### Post by SeaKing on 2012-06-11
Hey,

I've already set up an postfix mailserver using this [page.]("http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/") Now that I want this as an public emailserver on the internet I'm confronted with some problems that might be caused by config issues:

the important configs:

main.cf
```

#/etc/postfix/main.cf

myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
mydestination =
relayhost =
mynetworks = 85.214.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
mailbox_size_limit = 0
virtual_mailbox_limit = 0
recipient_delimiter = +
inet_interfaces = all
message_size_limit = 0
 
# SMTP Authentication (SASL)
 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
 
# Encrypted transfer (SSL/TLS)
 
smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/private/mail.[mydmoain.tdl].crt
smtpd_tls_key_file = /etc/ssl/private/mail.[mydmoain.tdl].key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
# Basic SPAM prevention
 
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, reject_unknown_helo_hostname, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, permit
permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit_mynetworks,reject_unauth_destination, permit

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
 
# Force incoming mail to go through Amavis
 
content_filter = amavis:[127.0.0.1]:10024

receive_override_options = no_address_mappings
 
# Virtual user mappings
 
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000
virtual_gid_maps =  static:5000
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf

anvil_rate_time_unit = 30
smtpd_client_connection_count_limit = 3
smtpd_client_connection_rate_limit = 3


```master.cf
```

#/etc/postfix/master.cf
#
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
submission inet n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
amavis    unix -        -       -       -       2       smtp
  -o smtp_data_done_timeout=1200
  -o smtp_send_xforward_command=yes
  -o disable_dns_lookups=yes
  -o max_use=20
127.0.0.1:10025 inet n  -       -       -       -       smtpd
  -o content_filter=
  -o local_recipient_maps=
  -o relay_recipient_maps=
  -o smtpd_restriction_classes=
  -o smtpd_delay_reject=no
  -o smtpd_client_restrictions=permit_mynetworks,reject
  -o smtpd_helo_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o smtpd_data_restrictions=reject_unauth_pipelining
  -o smtpd_end_of_data_restrictions=
  -o mynetworks=127.0.0.0/8
  -o smtpd_error_sleep_time=0
  -o smtpd_soft_error_limit=1001
  -o smtpd_hard_error_limit=1000
  -o smtpd_client_connection_count_limit=0
  -o smtpd_client_connection_rate_limit=0
  -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

``````

#/etc/amavis/conf.d/15-content-filter-mode

use strict;
 
@bypass_virus_checks_maps = (
   \%bypass_virus_checks, \@bypass_virus_checks_acl, \$bypass_virus_checks_re);
 
@bypass_spam_checks_maps = (
   \%bypass_spam_checks, \@bypass_spam_checks_acl, \$bypass_spam_checks_re);
 
1;

``````

#/etc/amavis/conf.d/50-user

use strict;
 
@local_domains_acl = qw(.);
$log_level = 1;
$syslog_priority = 'info';
$sa_kill_level_deflt = 6.5;
$final_spam_destiny = D_DISCARD;
$pax = 'pax';
 
1;

``````

# /etc/default/spamassassin

ENABLED=1
OPTIONS="--create-prefs --max-children 5 --helper-home-dir"
PIDFILE="/var/run/spamd.pid"
CRON=0

```First I have to add 0.0.0.0/0 to 'mynetworks' in the main.cf to recieve any email send to the server from everywhere ?! So if I add this I get bombarded with messenges like these in the server.log
```
Jun 11 14:34:36 h2026662 postfix/error[3076]: 3D2794A747: to=<michael1620520@yahoo.com.tw>, relay=none, delay=133167, delays=132944/214/0/8.6, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporaily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
 
```This might be thousands in a minute and my log is messed up completely but another lot more impartant problem is, that it seems that all these request block my networkinterface and I can't even log in to my mail accounts, the request isn't even getting through according to the log.

---

### Post by SeaKing on 2012-06-12
Now I updated my main.cf to:
```

myorigin = /etc/mailname
smtpd_banner = $mydomain (SMTP Server - Linux)
biff = no
append_dot_mydomain = no
readme_directory = no
mydestination = $myhostname localhost.$mydomain localhost $mydomain
relayhost =
relay_domains = $mydomain
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
virtual_mailbox_limit = 0
recipient_delimiter = +
inet_interfaces = all
message_size_limit = 0

### Max flow rate (1 sec delay per 50 emails/sec over the number of emails delivered/sec) 
in_flow_delay = 1s
 
# SMTP Authentication (SASL)
 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
 
# Encrypted transfer (SSL/TLS)
 
smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/private/mail.[mydomain.tld].crt
smtpd_tls_key_file = /etc/ssl/private/mail.[mydomain.tld].key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 
# Basic SPAM prevention
 
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

### Tarpit those bots/clients/spammers who send errors or scan for accounts
smtpd_error_sleep_time = 20
smtpd_soft_error_limit = 1
smtpd_hard_error_limit = 3
smtpd_junk_command_limit = 2

 
# Force incoming mail to go through Amavis
 
content_filter = amavis:[127.0.0.1]:10024

receive_override_options = no_address_mappings
 
# Virtual user mappings
 
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000
virtual_gid_maps =  static:5000
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf

anvil_rate_time_unit = 30
smtpd_client_connection_count_limit = 3
smtpd_client_connection_rate_limit = 3
maximal_queue_lifetime = 1d

### Reject codes == 554
access_map_reject_code = 554
invalid_hostname_reject_code = 554
maps_rbl_reject_code = 554
multi_recipient_bounce_reject_code = 554
non_fqdn_reject_code = 554
plaintext_reject_code = 554
reject_code = 554
relay_domains_reject_code = 554
unknown_address_reject_code = 554
unknown_client_reject_code = 450
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 554
unknown_relay_recipient_reject_code = 554
unknown_virtual_alias_reject_code = 554
unknown_virtual_mailbox_reject_code = 554
unverified_recipient_reject_code = 554
unverified_sender_reject_code = 554

### SMTP Restrictions
smtpd_client_restrictions = permit_mynetworks, reject_invalid_hostname, reject_rbl_client zen.spamhaus.org, reject_rbl_client tw.yahoo.com, reject_rbl_client yahoo.com.tw,  reject_rbl_client hinet.net , reject_rbl_client msa.hinet.net , reject_unknown_client, permit

smtpd_helo_restrictions = permit_mynetworks, check_helo_access hash:/etc/postfix/helo_access, reject_unauth_pipelining, reject_non_fqdn_hostname, reject_invalid_hostname, warn_if_reject reject_unknown_hostname, permit

smtpd_recipient_restrictions =  reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_non_fqdn_hostname, reject_invalid_hostname, permit_mynetworks, reject_unauth_pipelining, reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_destination, reject_unknown_client, permit

smtpd_sender_restrictions =  permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unknown_address

smtpd_etrn_restrictions =permit_mynetworks, reject

smtpd_data_restrictions = reject_unauth_pipelining, reject_multi_recipient_bounce, permit

```And a part my syslog with this config:
```

Jun 12 18:47:24 [myhost] postfix/error[9488]: 3A5D14506D: to=<lucky_john_joy@yahoo.com.tw>, relay=none, delay=238474, delays=238443/25/0/6.7, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/bounce[9518]: 31E4B100A2A: sender non-delivery notification: 7355E47EC7
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 1B88B1C4425: from=<050293@msa.hinet.net>, size=1914, nrcpt=40 (queue active)
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 31E4B100A2A: removed
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 3061E605C5: from=<050293@msa.hinet.net>, size=3245, nrcpt=7 (queue active)
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 12E871A2E52: from=<050293@msa.hinet.net>, size=1065, nrcpt=10 (queue active)
Jun 12 18:47:24 [myhost] postfix/error[9472]: 37E7E128E82: to=<yagamee@yahoo.com.tw>, relay=none, delay=204695, delays=204663/32/0/0.23, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9502]: 3BC7157EF8: to=<ycc0422@yahoo.com.tw>, relay=none, delay=228921, delays=228889/27/0/4.8, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9514]: 3DAE5E188F: to=<loverforever26@yahoo.com.tw>, relay=none, delay=214079, delays=214047/25/0/7.2, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9479]: 38CC05F85B: to=<pko_yang@yahoo.com.tw>, relay=none, delay=225766, delays=225734/25/0/7.4, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9498]: 3B03BC7767: to=<nicole6317@yahoo.com.tw>, relay=none, delay=215388, delays=215356/28/0/4.3, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9506]: 3633746706: to=<sdf741123@yahoo.com.tw>, relay=none, delay=237163, delays=237131/21/0/11, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/error[9474]: 37869140722: to=<love0505123@yahoo.com.tw>, relay=none, delay=204537, delays=204505/22/0/9.5, dsn=4.7.0, status=deferred (delivery temporarily suspended: host mx1.mail.tw.yahoo.com[203.188.197.119] refused to talk to me: 421 4.7.0 [GL01] Message from (85.214.58.225) temporarily deferred - 4.16.50. Please refer to http://postmaster.yahoo.com/errors/postmaster-21.html)
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 37B33A13DD: from=<050293@msa.hinet.net>, size=1499, nrcpt=8 (queue active)
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 37E7E128E82: from=<050293@msa.hinet.net>, status=expired, returned to sender
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 3BC7157EF8: from=<050293@msa.hinet.net>, status=expired, returned to sender
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 4865F109867: from=<050293@msa.hinet.net>, size=1665, nrcpt=26 (queue active)
Jun 12 18:47:24 [myhost] postfix/cleanup[9491]: BF258C44A4: message-id=<20120612164724.BF258C44A4@[myhost].[myprovider].net>
Jun 12 18:47:24 [myhost] postfix/cleanup[9490]: BF16DC4261: message-id=<20120612164724.BF16DC4261@[myhost].[myprovider].net>
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 3573F41517: from=<050293@msa.hinet.net>, size=1827, nrcpt=22 (queue active)
Jun 12 18:47:24 [myhost] postfix/qmgr[9453]: 6AF571A21B1: from=<050293@msa.hinet.net>, size=1494, nrcpt=22 (queue active)

```Question is now is this config good or am I a spambot?

---

### Post by SeaKing on 2012-06-13
So I added some additional spam filtering but it does not really changed much. Anyone any idea?

---

### Post by SeaKing on 2012-06-14
seemed I fixed it using: [http://www.howtoforge.com/block_spam_at_mta_level_postfix](http://www.howtoforge.com/block_spam_at_mta_level_postfix)

but now I have an amavis error:```

Jun 14 16:15:08 mailserver postfix/smtpd[3575]: connect from localhost[127.0.0.1]
Jun 14 16:15:08 mailserver postfix/smtpd[3575]: NOQUEUE: reject: CONNECT from localhost[127.0.0.1]: 554 5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied; proto=SMTP
Jun 14 16:15:08 mailserver amavis[1328]: (01328-15) (!)FWD via SMTP: <sender> -> <receiver>, 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting: 554 5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied at (eval 98) line 596, <GEN37> line 627.): id=01328-15
Jun 14 16:15:08 mailserver amavis[1328]: (01328-15) Blocked MTA-BLOCKED, [85.214.58.225] [85.214.58.225] <sender> -> <receiver>, Message-ID: <26ed95a6c5e353eb926c6509c292c85e@tuxundich.org>, mail_id: VE7AdMprEMCe, Hits: -1, size: 567, 144 ms


```

---

### Post by SeaKing on 2012-06-14
ok seemed to be a very stupid mistake, due to copying I canged in master.cf 
-o mynetworks to 0.0.0.0/8
when I changed it back to 127.0.0.0/8
everything works fine

---

