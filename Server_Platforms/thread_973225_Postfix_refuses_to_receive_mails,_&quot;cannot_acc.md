---
title: "Postfix refuses to receive mails, &quot;cannot access unix password database&quot;"
date: 2008-11-06
forum: Server Platforms
---

### Post by Creshal on 2008-11-06
I'm trying to build a mail server with postfix and courier-imap, mail accounts should be bound to the system's accounts, with additional aliases. But, well, postfix won't accept mails (*foo* is an alias for the user *bar*):
```
Nov  6 17:01:37 lvps87-230-10-17 postfix/master[1939]: daemon started -- version 2.2.10, configuration /etc/postfix
Nov  6 17:05:25 lvps87-230-10-17 postfix/smtpd[3174]: connect from mail-in-08.arcor-online.net[151.189.21.48]
Nov  6 17:05:25 lvps87-230-10-17 postfix/proxymap[3175]: warning: cannot access UNIX password database: Permission denied
Nov  6 17:05:25 lvps87-230-10-17 postfix/smtpd[3174]: NOQUEUE: reject: RCPT from mail-in-08.arcor-online.net[151.189.21.48]: 451 <*foo*@creshal.de>: Temporary lookup failure; from=<*****@arcor.de> to=<*foo*@creshal.de> proto=ESMTP helo=<mail-in-08.arcor-online.net>
Nov  6 17:05:25 lvps87-230-10-17 postfix/cleanup[3179]: 8866214854002: message-id=<20081106160525.8866214854002@creshal.de>
Nov  6 17:05:25 lvps87-230-10-17 postfix/qmgr[1942]: 8866214854002: from=<double-bounce@creshal.de>, size=1106, nrcpt=1 (queue active)
Nov  6 17:05:25 lvps87-230-10-17 postfix/smtpd[3174]: disconnect from mail-in-08.arcor-online.net[151.189.21.48]
Nov  6 17:05:25 lvps87-230-10-17 postfix/local[3180]: 8866214854002: to=<*bar*@creshal.de>, orig_to=<postmaster>, relay=local, delay=0, status=bounced (unknown user: "*bar*")
Nov  6 17:05:25 lvps87-230-10-17 postfix/bounce[3181]: warning: 8866214854002: undeliverable postmaster notification discarded
Nov  6 17:05:25 lvps87-230-10-17 postfix/qmgr[1942]: 8866214854002: removed
```

main.cf:```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
delay_warning_time = 4h
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = creshal.de
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = yaki-syndicate.de creshal.de mail.creshal.de
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = 
inet_interfaces = all
inet_protocols = ipv4
sender_canonical_maps = hash:/etc/postfix/sender_canonical
home_mailbox = Maildir/
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
``` The local_recipient_maps-entry should be correct, according to the Readme, and postfix is started with root privileges... so why isn't it working? :(

Edit: *bump*

---

### Post by Creshal on 2008-11-09
*bump*

---

### Post by Philio on 2008-11-09
Not sure if this is what you want to hear but you can easily achieve this with exim and using /etc/aliases.

The default exim configuration should handle local delivery then you can just stick your mail aliases in /etc/aliases.

---

### Post by CrucifiedEgo on 2008-11-09
Try cranking up the logging and let us know what shows up.  edit /etc/postfix/master.cf and add -v after the first smtpd.  if you don't find anything useful, try -v -v or -v -v -v (NOTE: Your logfiles will get really big really fast with any -v's, so only use this for brief testing.)

@Philio, Postfix handles this out of the box as well with /etc/aliases.  That's why this is such an odd behavior.

---

### Post by Creshal on 2008-11-11
Well, found one bug. The "proxy:"-Entry was wrong, however, ist still doesn't work. *sigh*
But I still don't get it why not...

Log with -v active:
```
Nov 11 14:55:22 lvps87-230-10-17 postfix/master[5181]: daemon started -- version 2.2.10, configuration /etc/postfix
Nov 11 14:55:22 lvps87-230-10-17 postfix/qmgr[5184]: E40481485400C: from=<>, size=2974, nrcpt=1 (queue active)
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  mail
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  ipv4
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: name_mask: ipv4
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  creshal.de
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  creshal.de
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  Postfix
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  postfix
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  postfix
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  postdrop
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  yaki-syndicate.de creshal.de mail.creshal.de
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /etc/mailname
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /usr/lib/postfix
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /usr/sbin
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /var/spool/postfix
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  pid
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  all
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  double-bounce
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  nobody
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  hash:/etc/aliases
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  20060405
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  2.2.10
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  hash
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  deferred, defer
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $mydestination -> yaki-syndicate.de creshal.de mail.creshal.de
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $relay_domains -> yaki-syndicate.de creshal.de mail.creshal.de
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  TZ MAIL_CONFIG
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  subnet
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  +=
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  -=+
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  bounce
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  cleanup
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  defer
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  pickup
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  qmgr
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  rewrite
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  showq
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  error
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  flush
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  verify
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  trace
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand ${config_directory}/prng_exch -> /etc/postfix/prng_exch
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /etc/ssl/certs/ssl-cert-snakeoil.pem
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  /etc/ssl/private/ssl-cert-snakeoil.key
Nov 11 14:55:48 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $smtpd_tls_dcert_file -> 
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 4 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand btree:${queue_directory}/smtpd_scache -> btree:/var/spool/postfix/smtpd_scache
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $smtp_tls_cert_file -> 
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $smtp_tls_dcert_file -> 
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 2 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand btree:${queue_directory}/smtp_scache -> btree:/var/spool/postfix/smtp_scache
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 3 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  3600s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  3600s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  10s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  10s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1s
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 3 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  500s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  500s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  3600s
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 3 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  18000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  18000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: inet_addr_local: configured 3 IPv4 addresses
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $myhostname ESMTP $mail_name (Ubuntu) -> creshal.de ESMTP Postfix (Ubuntu)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  resource, software
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 2 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  permit_mynetworks, reject_unauth_destination
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 4 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  postmaster
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 2 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $virtual_maps -> 
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  hash:/etc/aliases
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand unix:passwd.byname $alias_maps -> unix:passwd.byname hash:/etc/aliases
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  noanonymous
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  smtpd
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 5 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  CONNECT GET POST
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  <>
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  postmaster
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $authorized_verp_clients -> 
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $myhostname -> creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 2 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand ${smtpd_client_connection_limit_exceptions:$mynetworks} -> 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  permit_inet_interfaces
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  
Nov 11 14:55:49 lvps87-230-10-17 last message repeated 2 times
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: expand $smtpd_sasl_security_options -> noanonymous
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  yes
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  3s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  3s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  100s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  1000s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_eval: const  300s
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: process generation: 5 (5)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: mynetworks ~? debug_peer_list
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: mynetworks ~? fast_flush_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: mynetworks ~? mynetworks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? debug_peer_list
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? fast_flush_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? mynetworks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? permit_mx_backup_networks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? qmqpd_authorized_clients
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: relay_domains ~? relay_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: permit_mx_backup_networks ~? debug_peer_list
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: permit_mx_backup_networks ~? fast_flush_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: permit_mx_backup_networks ~? mynetworks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: permit_mx_backup_networks ~? permit_mx_backup_networks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_open: unix:passwd.byname
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: dict_open: hash:/etc/aliases
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? debug_peer_list
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? fast_flush_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? mynetworks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? permit_mx_backup_networks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? qmqpd_authorized_clients
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? relay_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: smtpd_access_maps ~? smtpd_access_maps
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: attr_clnt_create: transport=local endpoint=private/tlsmgr
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: attr_clnt_connect: connected to private/tlsmgr
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr size = 32
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: bp0H8U5q+hS6XtnaY9wGIfWpk1xx4ZcGHh9Nvtiy5JI=
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = policy
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: policy
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: policy
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 3
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: fast_flush_domains ~? debug_peer_list
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_string: fast_flush_domains ~? fast_flush_domains
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: attr_clnt_create: transport=local endpoint=private/anvil
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: connection established
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: master_notify: status 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: name_mask: resource
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: name_mask: software
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: connect from mail-in-01.arcor-online.net[151.189.21.41]
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostname: mail-in-01.arcor-online.net ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostaddr: 151.189.21.41 ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: attr_clnt_connect: connected to private/anvil
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = connect
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr ident = smtp:151.189.21.41
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: count
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: count
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 1
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: rate
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: rate
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 1
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 220 creshal.de ESMTP Postfix (Ubuntu)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: EHLO mail-in-01.arcor-online.net
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-PIPELINING
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-SIZE 10240000
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-VRFY
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-ETRN
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-STARTTLS
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250 8BITMIME
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: STARTTLS
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 220 Ready to start TLS
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr size = 32
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: seed
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0IulwTmE2iip/LZLC7UWO8iKFf++aRxo9TabrsnSQ78=
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = update
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr cache_type = 2
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr cache_id = 51E5B64788859936C5FDA45A3E2B56C6B10F4589BC2AEE2A8B99F4B8A41C93C6
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr version = 9469983
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr flags = 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr session = [data 127 bytes]
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/tlsmgr: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: EHLO mail-in-01.arcor-online.net
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-PIPELINING
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-SIZE 10240000
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-VRFY
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250-ETRN
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250 8BITMIME
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: MAIL FROM:<*****@arcor.de> SIZE=5555 BODY=8BITMIME
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: extract_addr: input: <*****@arcor.de>
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: smtpd_check_addr: addr=*****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: connect to subsystem private/rewrite
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = rewrite
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr rule = local
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr address = *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: rewrite_clnt: local: *****@arcor.de -> *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = resolve
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr address = *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: transport
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: transport
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: smtp
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: nexthop
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: nexthop
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: recipient
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: recipient
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 4096
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: resolve_clnt: `*****@arcor.de' -> transp=`smtp' host=`arcor.de' rcpt=`*****@arcor.de' flags= class=default
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: ctable_locate: install entry key *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: extract_addr: result: *****@arcor.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: fsspace: .: block size 1024, blocks free 12396552
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: smtpd_check_size: blocks 1024 avail 12396552 min_free 0 msg_size_limit 10240000
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250 Ok
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: RCPT TO:<*foo*@creshal.de>
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: extract_addr: input: <*foo*@creshal.de>
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: smtpd_check_addr: addr=*foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = rewrite
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr rule = local
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr address = *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: rewrite_clnt: local: *foo*@creshal.de -> *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = resolve
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr address = *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: transport
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: transport
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: local
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: nexthop
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: nexthop
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: recipient
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: recipient
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 256
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: resolve_clnt: `*foo*@creshal.de' -> transp=`local' host=`creshal.de' rcpt=`*foo*@creshal.de' flags= class=local
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: ctable_locate: install entry key *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: extract_addr: result: *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = rewrite
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr rule = local
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr address = postmaster
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: flags
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: address
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: postmaster@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/rewrite socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: rewrite_clnt: local: postmaster -> postmaster@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: >>> START Recipient address RESTRICTIONS <<<
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: generic_checks: name=permit_mynetworks
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: permit_mynetworks: mail-in-01.arcor-online.net 151.189.21.41
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostname: mail-in-01.arcor-online.net ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostaddr: 151.189.21.41 ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: generic_checks: name=permit_mynetworks status=0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: generic_checks: name=reject_unauth_destination
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: reject_unauth_destination: *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: permit_auth_destination: *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: ctable_locate: leave existing entry key *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: generic_checks: name=reject_unauth_destination status=0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: >>> END Recipient address RESTRICTIONS <<<
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: >>> CHECKING RECIPIENT MAPS <<<
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: ctable_locate: leave existing entry key *foo*@creshal.de
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: recipient_canonical_maps: *foo*@creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: recipient_canonical_maps: *foo*: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: recipient_canonical_maps: @creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: mail_addr_find: *foo*@creshal.de -> (not found)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: canonical_maps: *foo*@creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: canonical_maps: *foo*: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: canonical_maps: @creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: mail_addr_find: *foo*@creshal.de -> (not found)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: virtual_alias_maps: *foo*@creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: virtual_alias_maps: *foo*: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: virtual_alias_maps: @creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: mail_addr_find: *foo*@creshal.de -> (not found)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: local_recipient_maps: *foo*@creshal.de: not found
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: maps_find: local_recipient_maps: hash:/etc/aliases(0,100): *foo* = *bar*
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: mail_addr_find: *foo*@creshal.de -> *bar*
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: smtpd_check_rewrite: trying: permit_inet_interfaces
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: permit_inet_interfaces: mail-in-01.arcor-online.net 151.189.21.41
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: connect to subsystem public/cleanup
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: public/cleanup socket: wanted attribute: queue_id
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: queue_id
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 9A36114854002
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: public/cleanup socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr flags = 50
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: 9A36114854002: client=mail-in-01.arcor-online.net[151.189.21.41]
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250 Ok
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: DATA
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 354 End data with <CR><LF>.<CR><LF>
Nov 11 14:55:49 lvps87-230-10-17 postfix/cleanup[5200]: 9A36114854002: message-id=<1226411740.6106.0.camel@YakiWorkstation>
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: public/cleanup socket: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/qmgr[5184]: 9A36114854002: from=<*****@arcor.de>, size=5764, nrcpt=1 (queue active)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: public/cleanup socket: wanted attribute: reason
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: reason
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: public/cleanup socket: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 250 Ok: queued as 9A36114854002
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: < mail-in-01.arcor-online.net[151.189.21.41]: QUIT
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: > mail-in-01.arcor-online.net[151.189.21.41]: 221 Bye
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostname: mail-in-01.arcor-online.net ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_hostaddr: 151.189.21.41 ~? 127.0.0.0/8
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: mail-in-01.arcor-online.net: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: match_list_match: 151.189.21.41: no match
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr request = disconnect
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: send attr ident = smtp:151.189.21.41
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: status
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute value: 0
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: private/anvil: wanted attribute: (list terminator)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: input attribute name: (end)
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: disconnect from mail-in-01.arcor-online.net[151.189.21.41]
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: master_notify: status 1
Nov 11 14:55:49 lvps87-230-10-17 postfix/smtpd[5197]: connection closed
Nov 11 14:55:49 lvps87-230-10-17 postfix/local[5201]: 9A36114854002: to=<creshal@creshal.de>, orig_to=<*foo*@creshal.de>, relay=local, delay=0, status=bounced (unknown user: "creshal")
Nov 11 14:55:49 lvps87-230-10-17 postfix/cleanup[5200]: C14BC14854004: message-id=<20081111135549.C14BC14854004@creshal.de>
Nov 11 14:55:49 lvps87-230-10-17 postfix/qmgr[5184]: 9A36114854002: removed
Nov 11 14:55:49 lvps87-230-10-17 postfix/qmgr[5184]: C14BC14854004: from=<>, size=7521, nrcpt=1 (queue active)
Nov 11 14:55:50 lvps87-230-10-17 postfix/smtp[5204]: C14BC14854004: to=<*****@arcor.de>, relay=mx.arcor.de[151.189.21.118], delay=1, status=sent (250 2.0.0 Ok: queued as 1BB871F52E3)
Nov 11 14:55:50 lvps87-230-10-17 postfix/qmgr[5184]: C14BC14854004: removed
Nov 11 14:56:01 lvps87-230-10-17 postfix/master[5181]: terminating on signal 15

```
According to the "mail_addr_find: *foo*@creshal.de -> *bar*"-line he found the user, but then just rejected it without doing anything. :confused:

---

