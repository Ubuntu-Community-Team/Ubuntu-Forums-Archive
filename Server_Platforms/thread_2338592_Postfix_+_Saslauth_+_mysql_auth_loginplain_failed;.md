---
title: "Postfix + Saslauth + mysql auth login/plain failed; cram-md5/digest-md5 success"
date: 2016-09-29
forum: Server Platforms
---

### Post by samdet on 2016-09-29
Hello,

 I am able to connect to my smtp server using md5 methods. At least postfix admin success to send mail when these methods are available. But when I tried to connect through the Microsoft outlook app, it failed:
 SASL PLAIN authentication failed: authentication failure
 SASL LOGIN authentication failed: authentication failure
 It doesn't try md5 methods...

 /etc/postfix/main.cf:
 ```
alias_database = hash:/etc/aliases
 alias_maps = hash:/etc/aliases
 append_dot_mydomain = no
 biff = no
 broken_sasl_auth_clients = yes
 compatibility_level = 2
 default_destination_concurrency_limit = 5
 disable_vrfy_command = yes
 home_mailbox = Maildir/
 inet_interfaces = all
 inet_protocols = all
 mailbox_command =
 mailbox_size_limit = 0
 mydestination = localhost, $myhostname, localhost.$mydomain
 mydomain = domain.xyz
 myhostname = mail.domain.xyz
 mynetworks = [127.0.0.0]/8 [::ffff:127.0.0.0]0/104 ::1/128 
 myorigin = /etc/mailname
 readme_directory = no
 recipient_delimiter = +
 relay_destination_concurrency_limit = 1
 relayhost =
 smtp_tls_note_starttls_offer = yes
 smtp_tls_security_level = may
 smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
 smtpd_banner = $myhostname ESMTP {reverse_proxy} ${mail_name} (Ubuntu)
 smtpd_data_restrictions = reject_unauth_pipelining
 smtpd_helo_required = yes
 smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_re
 cipient, permit
 smtpd_sasl_auth_enable = yes
 smtpd_sasl_local_domain = $myhostname
 smtpd_sasl_security_options = noanonymous
 smtpd_sender_login_maps = mysql:/etc/postfix/mysql_virtual_user_maps.cf
 smtpd_sender_restrictions = reject_unknown_sender_domain, reject_sender_login_mismatch, permit
 smtpd_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
 smtpd_tls_ask_ccert = yes
 smtpd_tls_cert_file = /etc/ssl/private/ssl-chain-mail-detalhouet.xyz.pem
 smtpd_tls_ciphers = high
 smtpd_tls_key_file = /etc/ssl/private/ssl-key-decrypted-mail-detalhouet.xyz.key
 smtpd_tls_loglevel = 1
 smtpd_tls_received_header = yes
 smtpd_tls_security_level = may
 smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
 smtpd_tls_session_cache_timeout = 3600s
 tls_random_source = dev:/dev/urandom
 unknown_address_reject_code = 550
 unknown_client_reject_code = 550
 unknown_hostname_reject_code = 550
 virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
 virtual_gid_maps = static:5000
 virtual_mailbox_base = /home/vmail
 virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
 virtual_mailbox_limit = 51200000
 virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
 virtual_minimum_uid = 5000
 virtual_transport = virtual
 virtual_uid_maps = static:5000
```

 /etc/default/saslauthd
 ```
START=yes
 PWDIR="/var/spool/postfix/var/run/saslauthd"
 PARAMS="-m ${PWDIR}"
 PIDFILE="${PWDIR}/saslauthd.pid"
 DESC="SASL Authentication Daemon"
 NAME="saslauthd"
 MECHANISMS="pam"
 MECH_OPTIONS=""
 THREADS=5
 OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
```

 /etc/pam.d/smtp
 ```
auth required pam_mysql.so user=user passwd=password host=127.0.0.1 db=db table=mailbox usercolumn=username passwdcolumn=password
account sufficient pam_mysql.so user=user passwd=password host=127.0.0.1 db=db table=mailbox usercolumn=username passwdcolumn=password
```

 /etc/postfix/sasl/smtpd.conf:
 ```
pwcheck_method: saslauthd
 mech_list: CRAM-MD5 DIGEST-MD5 PLAIN LOGIN
 log_level: 7
 allow_plaintext: true
 auxprop_plugin: sql
 sql_engine: mysql
 sql_hostnames: 127.0.0.1
 sql_user: user
 sql_passwd: password
 sql_database: db
 sql_select: select password from mailbox where username='%u@%r' and active = 1
```


 The logs confirm that postfix admin success to login (only when one md5 methods is available)
 That the sql request are done and are correct.

 The passwords are not encrypted (They were but authentification was failing in any case, but that's a problem for an other day)

 I have tried both methods plain and login in telnet localhost: failed.

 I don't know what I missed...

 Thank you.

---

### Post by samdet on 2016-10-24
Hey, anyone can help please?

---

### Post by howefield on 2016-10-24
Thread moved to the "*Server Platforms*" forum, you might have better luck here.

---

### Post by samdet on 2016-11-18
Thank you, I hope it will come. :)

---

