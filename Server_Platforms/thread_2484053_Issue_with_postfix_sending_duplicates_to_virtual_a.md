---
title: "Issue with postfix sending duplicates to virtual_alias?"
date: 2023-02-16
forum: Server Platforms
---

### Post by hanji866 on 2023-02-16
Here is the scenario. I'm recently migrating to a new server and postfix is not acting as expected on the new server.

I have [EMAIL="admin@target.com"]admin@target.com[/EMAIL]. In postfix alias database table, that has a 'goto' to [EMAIL="admin@target.com"]admin@target.com[/EMAIL] and [EMAIL="droid@target.com"]droid@target.com[/EMAIL]. When I send an email to [EMAIL="admin@target.com"]admin@target.com[/EMAIL], it should be delivered to admin, as well as to droid. But droid, gets a duplicate (2) emails.

Here is a log portion:
```

Feb 16 06:09:14 mailserver postfix/smtpd[282072]: C1E2843DF2: client=localhost[127.0.0.1]
Feb 16 06:09:14 mailserver postfix/cleanup[282068]: C1E2843DF2: message-id=<20230216060908.00000985@testsource.com>
Feb 16 06:09:14 mailserver postfix/qmgr[246197]: C1E2843DF2: from=<admin@testsource.com>, size=1629, nrcpt=3 (queue active)
Feb 16 06:09:14 mailserver amavis[261695]: (261695-15) Passed CLEAN {RelayedInbound}, [47.47.157.150]:51992 [47.47.157.150] <admin@testsource.com> -> <admin@target.com>,<droid@target.com>, Queue-ID: D78893F374, Message-ID: <20230216060908.00000985@testsource.com>, mail_id: 8CUFMeuJ2ibm, Hits: -0.999, size: 970, queued_as: C1E2843DF2, 5649 ms
Feb 16 06:09:14 mailserver postfix/amavis/smtp[282069]: D78893F374: to=<admin@target.com>, relay=localhost[127.0.0.1]:10024, delay=6.1, delays=0.43/0/0/5.7, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as C1E2843DF2)
Feb 16 06:09:14 mailserver postfix/amavis/smtp[282069]: D78893F374: to=<droid@target.com>, orig_to=<admin@target.com>, relay=localhost[127.0.0.1]:10024, delay=6.1, delays=0.43/0/0/5.7, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as C1E2843DF2)
Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<admin@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<droid@target.com>, orig_to=<admin@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<droid@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
Feb 16 06:09:14 mailserver postfix/qmgr[246197]: C1E2843DF2: removed
```

As you can see, admin receives the email - good

```
Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<admin@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
```

droid gets an email - stating it was orig_to admin - good
```

Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<droid@target.com>, orig_to=<admin@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
```

But why did it get it again? - bad

```
Feb 16 06:09:14 mailserver postfix/virtual[282075]: C1E2843DF2: to=<droid@target.com>, relay=virtual, delay=0.07, delays=0.04/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to maildir)
```


Here is my main.cf with comments and spaces removed:

```
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix/sbin/
data_directory = /var/lib/postfix
mail_owner = postfix
myhostname = mailserver
mydomain = mailserver.com
inet_interfaces = all
mydestination = $myhostname, localhost.$mydomain
local_recipient_maps = $alias_maps $virtual_mailbox_maps
unknown_local_recipient_reject_code = 550
mynetworks = 23.253.56.16, 127.0.0.0/8
relay_domains = $mydestination
alias_maps = hash:/etc/aliases
mail_name = Mailserver Quiet Version
smtpd_banner = mailserver.com Mailserver forbids use of this system for unsolicited electronic mail advertisements. All actions are being logged and reviewed
local_destination_concurrency_limit = 2
default_destination_concurrency_limit = 20
debug_peer_level = 5
debugger_command =
         PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
         ddd $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
setgid_group = postdrop
html_directory = no
manpage_directory = /usr/share/man
sample_directory = /etc/postfix
readme_directory = no
inet_protocols = ipv4
home_mailbox = .maildir/
unknown_address_reject_code = 554
unknown_client_reject_code = 554
unknown_hostname_reject_code = 554
smtpd_discard_ehlo_keywords = silent-discard, dsn
smtpd_helo_required = yes
disable_vrfy_command = yes
smtpd_helo_restrictions =
   permit_mynetworks,
   permit_sasl_authenticated
smtpd_client_restrictions =
   permit_mynetworks,
   permit_sasl_authenticated,
   reject_rbl_client zen.spamhaus.org
smtpd_sender_restrictions =
   check_sender_access hash:/etc/postfix/sender_access,
   check_sender_access pcre:/etc/postfix/sender_access_pcre,
   reject_rhsbl_reverse_client dbl.spamhaus.org
mime_header_checks = regexp:/etc/postfix/mime_header_checks
smtpd_restriction_classes = check_policyd_weight
check_policyd_weight =
    check_policy_service inet:127.0.0.1:12525
header_checks = regexp:/etc/postfix/header_checks
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_helo_access regexp:/etc/postfix/helo_access reject_invalid_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_destination, check_client_access cidr:/etc/postfix/blacklist.cidr, check_policy_service inet:127.0.0.1:10030, reject_unauth_pipelining, check_client_access hash:/etc/postfix/whitelist_hosts, reject_rbl_client zen.spamhaus.org, reject_rbl_client dul.dnsbl.sorbs.net, reject_unauth_destination check_client_access hash:/etc/postfix/policyd_weight_client_whitelist, check_recipient_access hash:/etc/postfix/policyd_weight_recipient_whitelist, check_recipient_access hash:/etc/postfix/policyd_weight_users, check_policy_service unix:private/policy-spf
content_filter = smtp-amavis:[localhost]:10024
message_size_limit = 50000000
smtpd_sasl_path = smtpd
cyrus_sasl_config_path = /etc/postfix/sasl
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_use_tls = yes
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file =  /etc/configs/ssl/mailserver.com.key
smtpd_tls_cert_file = /etc/configs/ssl/mailserver.com.cer
smtpd_tls_CAfile = /etc/configs/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_session_cache_database = btree:/var/lib/postfix/smtpd_tls_session_cache
tls_random_source = dev:/dev/urandom
smtpd_tls_exclude_ciphers = aNULL, eNULL, EXPORT, DES, RC4, MD5, PSK, aECDH, EDH-DSS-DES-CBC3-SHA, EDH-RSA-DES-CDC3-SHA, KRB5-DE5, CBC3-SHA
smtpd_tls_dh1024_param_file = /etc/courier/dhparams.pem
virtual_transport = virtual
virtual_mailbox_domains = proxy:mysql:$config_directory/postfixadmin/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = proxy:mysql:$config_directory/postfixadmin/mysql_virtual_mailbox_maps.cf
virtual_alias_maps = proxy:mysql:$config_directory/postfixadmin/mysql_virtual_alias_maps.cf
virtual_mailbox_limit_maps = proxy:mysql:$config_directory/postfixadmin/mysql_virtual_mailbox_limit_maps.cf
proxy_read_maps =
   $virtual_mailbox_domains
   $virtual_mailbox_maps
   $virtual_alias_maps
   $virtual_mailbox_limit_maps
virtual_minimum_uid = 2000
virtual_gid_maps = static:2000
virtual_uid_maps = static:2000
virtual_mailbox_base = /
smtpd_relay_restrictions = permit_mynetworks,permit_sasl_authenticated,defer_unauth_destination
milter_protocol = 2
milter_default_action = accept
smtpd_milters = inet:localhost:12301
non_smtpd_milters = inet:localhost:12301
compatibility_level = 3.6
policy-spf_time_limit = 3600s
```

Here is my master.cf

```
smtp      inet  n       -       y       -       -       smtpd
smtps inet n - y - - smtpd
 -o syslog_name=postfix/smtps
 -o smtpd_tls_wrappermode=yes
 -o smtpd_sasl_auth_enable=yes

pickup    unix  n       -       y       60      1       pickup
cleanup   unix  n       -       y       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       y       1000?   1       tlsmgr
rewrite   unix  -       -       y       -       -       trivial-rewrite
bounce    unix  -       -       y       -       0       bounce
defer     unix  -       -       y       -       0       bounce
trace     unix  -       -       y       -       0       bounce
verify    unix  -       -       y       -       1       verify
flush     unix  n       -       y       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp
relay     unix  -       -       y       -       -       smtp
        -o syslog_name=postfix/$service_name
showq     unix  n       -       y       -       -       showq
error     unix  -       -       y       -       -       error
retry     unix  -       -       y       -       -       error
discard   unix  -       -       y       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       y       -       -       lmtp
anvil     unix  -       -       y       -       1       anvil
scache    unix  -       -       y       -       1       scache
postlog   unix-dgram n  -       n       -       1       postlogd
maildrop  unix  -       n       n       -       -       pipe
  flags=DRXhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FRX user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}
smtp-amavis   unix   -   -   n   -   4   smtp
    -o syslog_name=postfix/amavis
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20
    -o smtp_tls_security_level=none
127.0.0.1:10025   inet   n   -   n   -   -   smtpd
   -o content_filter=
   -o local_recipient_maps=
   -o relay_recipient_maps=
   -o smtpd_restriction_classes=
   -o smtpd_helo_restrictions=
   -o smtpd_sender_restrictions=
   -o smtpd_recipient_restrictions=permit_mynetworks,reject
   -o mynetworks=127.0.0.0/8
   -o strict_rfc821_envelopes=yes
policy-spf unix    -       n       n       -       0     spawn
      user=nobody argv=/usr/bin/policyd-spf
```

I'm running postfix-mysql 3.6.4

Thanks!
hanji

---

### Post by SeijiSensei on 2023-02-16
What's the content of /etc/aliases? It should read
```

admin:     \admin,droid

```
The backslash tells Postfix to treat admin as an actual account as well as the admin alias. Be sure to run the "newaliases" command after making changes to this file.

---

