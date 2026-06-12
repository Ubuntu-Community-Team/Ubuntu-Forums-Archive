---
title: "Postfix comes with no SASL autentication error"
date: 2016-03-31
forum: Server Platforms
---

### Post by kacper4 on 2016-03-31
Hello. I've read some threads about this problem, but i couldn't find solution for me.
When i try to login to mail acc i can't. I've this error in logs:
```
Mar 31 18:29:38 ubuntu postfix/smtpd[10446]: fatal: no SASL authentication mechanisms
```

I made email 3 times and always same error.

postconf -n:
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = foto-grafik.biz, ubuntu, localhost.localdomain, localhost
myhostname = ubuntu
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_domains = /etc/postfix/virtual_domains
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_uid_maps = static:5000

```

doveconf -n:
```

# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.16.0-67-generic i686 Ubuntu 14.04.4 LTS ext4
disable_plaintext_auth = no
log_path = /var/log/dovecot
mail_location = maildir:/var/mail/vhosts/%d/%n/
namespace inbox {
  inbox = yes
  location =
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix =
}
passdb {
  driver = pam
}
protocols = imap
ssl = no
ssl_cert = </etc/dovecot/dovecot.pem
ssl_key = </etc/dovecot/private/dovecot.pem
userdb {
  driver = passwd
}
protocol lda {
  auth_socket_path = /var/run/dovecot/auth-master
  hostname = host.foto-grafik.biz
  mail_plugin_dir = /usr/lib/dovecot/modules/
  mail_plugins = cmusieve
  postmaster_address = postmaster@foto-grafik.biz
}

```

And some logs of postfix:
```

Mar 31 18:17:02 ubuntu postfix/qmgr[937]: 67EB21C0B61: removed
Mar 31 18:18:01 ubuntu postfix/pickup[9009]: 7D2371C0B7C: uid=1000 from=<km>
Mar 31 18:18:01 ubuntu postfix/cleanup[7195]: 7D2371C0B7C: message-id=<20160331161801.7D2371C0B7C@ubuntu>
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: 7D2371C0B7C: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:18:01 ubuntu postfix/pickup[9009]: 8C2671C0B61: uid=1000 from=<km>
Mar 31 18:18:01 ubuntu postfix/cleanup[7193]: 8C2671C0B61: message-id=<20160331161801.8C2671C0B61@ubuntu>
Mar 31 18:18:01 ubuntu postfix/local[6988]: 7D2371C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.25, delays=0.12/0/0/0.13, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:18:01 ubuntu postfix/pickup[9009]: AB9571C0B87: uid=1005 from=<ts3>
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: 7D2371C0B7C: removed
Mar 31 18:18:01 ubuntu postfix/cleanup[7195]: AB9571C0B87: message-id=<20160331161801.AB9571C0B87@ubuntu>
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: 8C2671C0B61: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: AB9571C0B87: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:18:01 ubuntu postfix/pickup[9009]: BDE5B1C0B8B: uid=1005 from=<ts3>
Mar 31 18:18:01 ubuntu postfix/cleanup[7195]: BDE5B1C0B8B: message-id=<20160331161801.BDE5B1C0B8B@ubuntu>
Mar 31 18:18:01 ubuntu postfix/local[9475]: 8C2671C0B61: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.29, delays=0.17/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: 8C2671C0B61: removed
Mar 31 18:18:01 ubuntu postfix/local[9474]: AB9571C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.34, delays=0.24/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: AB9571C0B87: removed
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: BDE5B1C0B8B: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:18:01 ubuntu postfix/local[6988]: BDE5B1C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.39, delays=0.34/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:18:01 ubuntu postfix/qmgr[937]: BDE5B1C0B8B: removed
Mar 31 18:19:01 ubuntu postfix/pickup[9009]: DF5A01C0B7C: uid=1005 from=<ts3>
Mar 31 18:19:01 ubuntu postfix/cleanup[9783]: DF5A01C0B7C: message-id=<20160331161901.DF5A01C0B7C@ubuntu>
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: DF5A01C0B7C: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:19:02 ubuntu postfix/pickup[9009]: 05CEC1C0B61: uid=1000 from=<km>
Mar 31 18:19:02 ubuntu postfix/cleanup[9783]: 05CEC1C0B61: message-id=<20160331161902.05CEC1C0B61@ubuntu>
Mar 31 18:19:02 ubuntu postfix/local[9475]: DF5A01C0B7C: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.28, delays=0.18/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 05CEC1C0B61: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:19:02 ubuntu postfix/pickup[9009]: 1D2481C0B87: uid=1000 from=<km>
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: DF5A01C0B7C: removed
Mar 31 18:19:02 ubuntu postfix/cleanup[9784]: 1D2481C0B87: message-id=<20160331161902.1D2481C0B87@ubuntu>
Mar 31 18:19:02 ubuntu postfix/local[9474]: 05CEC1C0B61: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.28, delays=0.2/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 1D2481C0B87: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 05CEC1C0B61: removed
Mar 31 18:19:02 ubuntu postfix/pickup[9009]: 2F3481C0B7C: uid=1005 from=<ts3>
Mar 31 18:19:02 ubuntu postfix/cleanup[9783]: 2F3481C0B7C: message-id=<20160331161902.2F3481C0B7C@ubuntu>
Mar 31 18:19:02 ubuntu postfix/local[9475]: 1D2481C0B87: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.35, delays=0.27/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 1D2481C0B87: removed
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 2F3481C0B7C: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:19:02 ubuntu postfix/local[9474]: 2F3481C0B7C: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.44, delays=0.37/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:19:02 ubuntu postfix/qmgr[937]: 2F3481C0B7C: removed
Mar 31 18:20:01 ubuntu postfix/pickup[9009]: 59F801C0BF0: uid=1000 from=<km>
Mar 31 18:20:01 ubuntu postfix/cleanup[9784]: 59F801C0BF0: message-id=<20160331162001.59F801C0BF0@ubuntu>
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 59F801C0BF0: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:20:01 ubuntu postfix/pickup[9009]: 724FA1C0B87: uid=1005 from=<ts3>
Mar 31 18:20:01 ubuntu postfix/cleanup[9783]: 724FA1C0B87: message-id=<20160331162001.724FA1C0B87@ubuntu>
Mar 31 18:20:01 ubuntu postfix/local[9475]: 59F801C0BF0: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.23, delays=0.17/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 59F801C0BF0: removed
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 724FA1C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:20:01 ubuntu postfix/pickup[9009]: 880711C0B8B: uid=1005 from=<ts3>
Mar 31 18:20:01 ubuntu postfix/cleanup[9784]: 880711C0B8B: message-id=<20160331162001.880711C0B8B@ubuntu>
Mar 31 18:20:01 ubuntu postfix/local[9474]: 724FA1C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.34, delays=0.25/0/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 724FA1C0B87: removed
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 880711C0B8B: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:20:01 ubuntu postfix/pickup[9009]: A51541C0B61: uid=1000 from=<km>
Mar 31 18:20:01 ubuntu postfix/cleanup[9783]: A51541C0B61: message-id=<20160331162001.A51541C0B61@ubuntu>
Mar 31 18:20:01 ubuntu postfix/local[9475]: 880711C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.46, delays=0.39/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: 880711C0B8B: removed
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: A51541C0B61: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:20:01 ubuntu postfix/local[9474]: A51541C0B61: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.53, delays=0.49/0/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:20:01 ubuntu postfix/qmgr[937]: A51541C0B61: removed
Mar 31 18:21:01 ubuntu postfix/pickup[9009]: AEF5A1C0BF0: uid=1005 from=<ts3>
Mar 31 18:21:01 ubuntu postfix/cleanup[9784]: AEF5A1C0BF0: message-id=<20160331162101.AEF5A1C0BF0@ubuntu>
Mar 31 18:21:01 ubuntu postfix/pickup[9009]: C0E611C0BF3: uid=1005 from=<ts3>
Mar 31 18:21:01 ubuntu postfix/cleanup[9783]: C0E611C0BF3: message-id=<20160331162101.C0E611C0BF3@ubuntu>
Mar 31 18:21:01 ubuntu postfix/qmgr[937]: C0E611C0BF3: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:21:01 ubuntu postfix/qmgr[937]: AEF5A1C0BF0: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:21:01 ubuntu postfix/pickup[9009]: D02A71C0B87: uid=1000 from=<km>
Mar 31 18:21:01 ubuntu postfix/cleanup[9784]: D02A71C0B87: message-id=<20160331162101.D02A71C0B87@ubuntu>
Mar 31 18:21:01 ubuntu postfix/local[9475]: C0E611C0BF3: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.21, delays=0.08/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:21:01 ubuntu postfix/qmgr[937]: C0E611C0BF3: removed
Mar 31 18:21:01 ubuntu postfix/qmgr[937]: D02A71C0B87: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:21:01 ubuntu postfix/pickup[9009]: E8D5B1C0B7C: uid=1000 from=<km>
Mar 31 18:21:01 ubuntu postfix/cleanup[9783]: E8D5B1C0B7C: message-id=<20160331162101.E8D5B1C0B7C@ubuntu>
Mar 31 18:21:02 ubuntu postfix/qmgr[937]: E8D5B1C0B7C: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:21:02 ubuntu postfix/local[9475]: D02A71C0B87: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.35, delays=0.25/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:21:02 ubuntu postfix/qmgr[937]: D02A71C0B87: removed
Mar 31 18:21:02 ubuntu postfix/local[9474]: AEF5A1C0BF0: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=1.2, delays=0.08/0/0/1.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:21:02 ubuntu postfix/qmgr[937]: AEF5A1C0BF0: removed
Mar 31 18:21:03 ubuntu postfix/local[9886]: E8D5B1C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=1.7, delays=0.36/0.01/0/1.3, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:21:03 ubuntu postfix/qmgr[937]: E8D5B1C0B7C: removed
Mar 31 18:22:02 ubuntu postfix/pickup[9009]: 124A31C0BF3: uid=1000 from=<km>
Mar 31 18:22:02 ubuntu postfix/cleanup[9784]: 124A31C0BF3: message-id=<20160331162202.124A31C0BF3@ubuntu>
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 124A31C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:22:02 ubuntu postfix/pickup[9009]: 292B91C0B87: uid=1005 from=<ts3>
Mar 31 18:22:02 ubuntu postfix/cleanup[9783]: 292B91C0B87: message-id=<20160331162202.292B91C0B87@ubuntu>
Mar 31 18:22:02 ubuntu postfix/local[9475]: 124A31C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.2, delays=0.13/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:22:02 ubuntu postfix/pickup[9009]: 383311C0B7C: uid=1000 from=<km>
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 124A31C0BF3: removed
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 292B91C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:22:02 ubuntu postfix/cleanup[9784]: 383311C0B7C: message-id=<20160331162202.383311C0B7C@ubuntu>
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 383311C0B7C: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:22:02 ubuntu postfix/pickup[9009]: 46ACC1C0B8B: uid=1005 from=<ts3>
Mar 31 18:22:02 ubuntu postfix/cleanup[9783]: 46ACC1C0B8B: message-id=<20160331162202.46ACC1C0B8B@ubuntu>
Mar 31 18:22:02 ubuntu postfix/local[9474]: 292B91C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.35, delays=0.23/0/0/0.11, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 292B91C0B87: removed
Mar 31 18:22:02 ubuntu postfix/local[9475]: 383311C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.33, delays=0.23/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 383311C0B7C: removed
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 46ACC1C0B8B: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:22:02 ubuntu postfix/local[9886]: 46ACC1C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.39, delays=0.33/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:22:02 ubuntu postfix/qmgr[937]: 46ACC1C0B8B: removed
Mar 31 18:23:01 ubuntu postfix/pickup[9009]: 61E8B1C0BF0: uid=1000 from=<km>
Mar 31 18:23:01 ubuntu postfix/cleanup[9784]: 61E8B1C0BF0: message-id=<20160331162301.61E8B1C0BF0@ubuntu>
Mar 31 18:23:01 ubuntu postfix/pickup[9009]: 729E31C0B8B: uid=1005 from=<ts3>
Mar 31 18:23:01 ubuntu postfix/cleanup[9783]: 729E31C0B8B: message-id=<20160331162301.729E31C0B8B@ubuntu>
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 61E8B1C0BF0: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 729E31C0B8B: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:23:01 ubuntu postfix/local[9474]: 61E8B1C0BF0: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.19, delays=0.08/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:23:01 ubuntu postfix/local[9475]: 729E31C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.24, delays=0.14/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:23:01 ubuntu postfix/pickup[9009]: 8D3A31C0B7C: uid=1000 from=<km>
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 61E8B1C0BF0: removed
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 729E31C0B8B: removed
Mar 31 18:23:01 ubuntu postfix/cleanup[9784]: 8D3A31C0B7C: message-id=<20160331162301.8D3A31C0B7C@ubuntu>
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 8D3A31C0B7C: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:23:01 ubuntu postfix/pickup[9009]: 984A91C0B87: uid=1005 from=<ts3>
Mar 31 18:23:01 ubuntu postfix/cleanup[9783]: 984A91C0B87: message-id=<20160331162301.984A91C0B87@ubuntu>
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 984A91C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:23:01 ubuntu postfix/local[9886]: 8D3A31C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.36, delays=0.24/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 8D3A31C0B7C: removed
Mar 31 18:23:01 ubuntu postfix/local[9474]: 984A91C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.37, delays=0.27/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:23:01 ubuntu postfix/qmgr[937]: 984A91C0B87: removed
Mar 31 18:24:01 ubuntu postfix/pickup[9009]: CFB281C0BF3: uid=1000 from=<km>
Mar 31 18:24:01 ubuntu postfix/cleanup[9784]: CFB281C0BF3: message-id=<20160331162401.CFB281C0BF3@ubuntu>
Mar 31 18:24:01 ubuntu postfix/qmgr[937]: CFB281C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:24:01 ubuntu postfix/pickup[9009]: E47131C0B87: uid=1005 from=<ts3>
Mar 31 18:24:01 ubuntu postfix/cleanup[9783]: E47131C0B87: message-id=<20160331162401.E47131C0B87@ubuntu>
Mar 31 18:24:02 ubuntu postfix/local[9475]: CFB281C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.23, delays=0.16/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: CFB281C0BF3: removed
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: E47131C0B87: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:24:02 ubuntu postfix/pickup[9009]: 09FAD1C0058: uid=1005 from=<ts3>
Mar 31 18:24:02 ubuntu postfix/cleanup[9784]: 09FAD1C0058: message-id=<20160331162402.09FAD1C0058@ubuntu>
Mar 31 18:24:02 ubuntu postfix/local[9886]: E47131C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.34, delays=0.27/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:24:02 ubuntu postfix/pickup[9009]: 1BF421C0B8B: uid=1000 from=<km>
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: E47131C0B87: removed
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: 09FAD1C0058: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:24:02 ubuntu postfix/cleanup[9783]: 1BF421C0B8B: message-id=<20160331162402.1BF421C0B8B@ubuntu>
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: 1BF421C0B8B: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:24:02 ubuntu postfix/local[9474]: 09FAD1C0058: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.46, delays=0.33/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: 09FAD1C0058: removed
Mar 31 18:24:02 ubuntu postfix/local[9475]: 1BF421C0B8B: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.49, delays=0.39/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:24:02 ubuntu postfix/qmgr[937]: 1BF421C0B8B: removed
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: 3F1431C0B8B: uid=1005 from=<ts3>
Mar 31 18:25:02 ubuntu postfix/cleanup[9784]: 3F1431C0B8B: message-id=<20160331162502.3F1431C0B8B@ubuntu>
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 3F1431C0B8B: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: 554BB1C0058: uid=1000 from=<km>
Mar 31 18:25:02 ubuntu postfix/cleanup[9783]: 554BB1C0058: message-id=<20160331162502.554BB1C0058@ubuntu>
Mar 31 18:25:02 ubuntu postfix/local[9886]: 3F1431C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.27, delays=0.12/0.04/0/0.11, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 3F1431C0B8B: removed
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: 6FE111C0B87: uid=1000 from=<km>
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 554BB1C0058: from=<km@foto-grafik.biz>, size=730, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/cleanup[9784]: 6FE111C0B87: message-id=<20160331162502.6FE111C0B87@ubuntu>
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 6FE111C0B87: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: 7F0B41C0BF0: uid=1005 from=<ts3>
Mar 31 18:25:02 ubuntu postfix/cleanup[9783]: 7F0B41C0BF0: message-id=<20160331162502.7F0B41C0BF0@ubuntu>
Mar 31 18:25:02 ubuntu postfix/local[9474]: 554BB1C0058: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.34, delays=0.22/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 554BB1C0058: removed
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 7F0B41C0BF0: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: 9414C1C0058: uid=1000 from=<km>
Mar 31 18:25:02 ubuntu postfix/cleanup[9784]: 9414C1C0058: message-id=<20160331162502.9414C1C0058@ubuntu>
Mar 31 18:25:02 ubuntu postfix/local[9886]: 7F0B41C0BF0: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.36, delays=0.3/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 7F0B41C0BF0: removed
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 9414C1C0058: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/pickup[10038]: A33BD1C0B8B: uid=1005 from=<ts3>
Mar 31 18:25:02 ubuntu postfix/cleanup[9783]: A33BD1C0B8B: message-id=<20160331162502.A33BD1C0B8B@ubuntu>
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: A33BD1C0B8B: from=<ts3@foto-grafik.biz>, size=734, nrcpt=1 (queue active)
Mar 31 18:25:02 ubuntu postfix/local[9474]: 9414C1C0058: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.49, delays=0.37/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: 9414C1C0058: removed
Mar 31 18:25:02 ubuntu postfix/local[9886]: A33BD1C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.53, delays=0.43/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:02 ubuntu postfix/qmgr[937]: A33BD1C0B8B: removed
Mar 31 18:25:03 ubuntu postfix/local[9475]: 6FE111C0B87: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=1.2, delays=0.22/0/0/0.97, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:25:03 ubuntu postfix/qmgr[937]: 6FE111C0B87: removed
Mar 31 18:26:01 ubuntu postfix/pickup[10038]: B940F1C0BF3: uid=1005 from=<ts3>
Mar 31 18:26:01 ubuntu postfix/cleanup[9784]: B940F1C0BF3: message-id=<20160331162601.B940F1C0BF3@ubuntu>
Mar 31 18:26:01 ubuntu postfix/qmgr[937]: B940F1C0BF3: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:26:01 ubuntu postfix/pickup[10038]: D12871C0BF0: uid=1000 from=<km>
Mar 31 18:26:01 ubuntu postfix/cleanup[9783]: D12871C0BF0: message-id=<20160331162601.D12871C0BF0@ubuntu>
Mar 31 18:26:01 ubuntu postfix/qmgr[937]: D12871C0BF0: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:26:01 ubuntu postfix/pickup[10038]: E05051C0B8B: uid=1005 from=<ts3>
Mar 31 18:26:01 ubuntu postfix/cleanup[9784]: E05051C0B8B: message-id=<20160331162601.E05051C0B8B@ubuntu>
Mar 31 18:26:01 ubuntu postfix/local[9474]: B940F1C0BF3: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.29, delays=0.19/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:26:01 ubuntu postfix/qmgr[937]: B940F1C0BF3: removed
Mar 31 18:26:02 ubuntu postfix/local[9886]: D12871C0BF0: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.33, delays=0.25/0/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:26:02 ubuntu postfix/qmgr[937]: D12871C0BF0: removed
Mar 31 18:26:02 ubuntu postfix/pickup[10038]: 014191C0058: uid=1000 from=<km>
Mar 31 18:26:02 ubuntu postfix/qmgr[937]: E05051C0B8B: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:26:02 ubuntu postfix/cleanup[9783]: 014191C0058: message-id=<20160331162602.014191C0058@ubuntu>
Mar 31 18:26:02 ubuntu postfix/qmgr[937]: 014191C0058: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:26:02 ubuntu postfix/local[9475]: E05051C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.46, delays=0.35/0/0/0.11, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:26:02 ubuntu postfix/qmgr[937]: E05051C0B8B: removed
Mar 31 18:26:02 ubuntu postfix/local[9474]: 014191C0058: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.49, delays=0.4/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:26:02 ubuntu postfix/qmgr[937]: 014191C0058: removed
Mar 31 18:27:02 ubuntu postfix/pickup[10038]: 22B381C0BF3: uid=1000 from=<km>
Mar 31 18:27:02 ubuntu postfix/cleanup[9784]: 22B381C0BF3: message-id=<20160331162702.22B381C0BF3@ubuntu>
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 22B381C0BF3: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:27:02 ubuntu postfix/pickup[10038]: 384321C0BF0: uid=1005 from=<ts3>
Mar 31 18:27:02 ubuntu postfix/cleanup[9783]: 384321C0BF0: message-id=<20160331162702.384321C0BF0@ubuntu>
Mar 31 18:27:02 ubuntu postfix/local[9886]: 22B381C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.22, delays=0.14/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 22B381C0BF3: removed
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 384321C0BF0: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:27:02 ubuntu postfix/pickup[10038]: 55AA81C0058: uid=1000 from=<km>
Mar 31 18:27:02 ubuntu postfix/cleanup[9784]: 55AA81C0058: message-id=<20160331162702.55AA81C0058@ubuntu>
Mar 31 18:27:02 ubuntu postfix/local[9475]: 384321C0BF0: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.34, delays=0.29/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:27:02 ubuntu postfix/pickup[10038]: 6412C1C0B8B: uid=1005 from=<ts3>
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 384321C0BF0: removed
Mar 31 18:27:02 ubuntu postfix/cleanup[9783]: 6412C1C0B8B: message-id=<20160331162702.6412C1C0B8B@ubuntu>
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 55AA81C0058: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 6412C1C0B8B: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:27:02 ubuntu postfix/local[9475]: 6412C1C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.43, delays=0.33/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:27:02 ubuntu postfix/local[9474]: 55AA81C0058: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.42, delays=0.32/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 6412C1C0B8B: removed
Mar 31 18:27:02 ubuntu postfix/qmgr[937]: 55AA81C0058: removed
Mar 31 18:28:01 ubuntu postfix/pickup[10038]: A72D11C0BF3: uid=1000 from=<km>
Mar 31 18:28:01 ubuntu postfix/cleanup[9784]: A72D11C0BF3: message-id=<20160331162801.A72D11C0BF3@ubuntu>
Mar 31 18:28:01 ubuntu postfix/pickup[10038]: BC9AA1C0B87: uid=1005 from=<ts3>
Mar 31 18:28:01 ubuntu postfix/cleanup[9783]: BC9AA1C0B87: message-id=<20160331162801.BC9AA1C0B87@ubuntu>
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: BC9AA1C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: A72D11C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:28:01 ubuntu postfix/pickup[10038]: CD4F31C0058: uid=1000 from=<km>
Mar 31 18:28:01 ubuntu postfix/cleanup[9784]: CD4F31C0058: message-id=<20160331162801.CD4F31C0058@ubuntu>
Mar 31 18:28:01 ubuntu postfix/local[9475]: A72D11C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.31, delays=0.18/0.01/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:28:01 ubuntu postfix/local[9886]: BC9AA1C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.32, delays=0.18/0/0/0.13, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: A72D11C0BF3: removed
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: BC9AA1C0B87: removed
Mar 31 18:28:01 ubuntu postfix/pickup[10038]: E8B631C0B87: uid=1005 from=<ts3>
Mar 31 18:28:01 ubuntu postfix/cleanup[9783]: E8B631C0B87: message-id=<20160331162801.E8B631C0B87@ubuntu>
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: CD4F31C0058: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:28:01 ubuntu postfix/qmgr[937]: E8B631C0B87: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:28:02 ubuntu postfix/local[9474]: CD4F31C0058: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.48, delays=0.34/0/0/0.14, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:28:02 ubuntu postfix/local[9475]: E8B631C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.49, delays=0.34/0/0/0.14, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:28:02 ubuntu postfix/qmgr[937]: CD4F31C0058: removed
Mar 31 18:28:02 ubuntu postfix/qmgr[937]: E8B631C0B87: removed
Mar 31 18:29:02 ubuntu postfix/pickup[10038]: 1ADAA1C0BF3: uid=1005 from=<ts3>
Mar 31 18:29:02 ubuntu postfix/cleanup[9784]: 1ADAA1C0BF3: message-id=<20160331162902.1ADAA1C0BF3@ubuntu>
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 1ADAA1C0BF3: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:29:02 ubuntu postfix/pickup[10038]: 2FF601C0B87: uid=1000 from=<km>
Mar 31 18:29:02 ubuntu postfix/cleanup[9783]: 2FF601C0B87: message-id=<20160331162902.2FF601C0B87@ubuntu>
Mar 31 18:29:02 ubuntu postfix/local[9886]: 1ADAA1C0BF3: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.22, delays=0.14/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 1ADAA1C0BF3: removed
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 2FF601C0B87: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:29:02 ubuntu postfix/pickup[10038]: 421AC1C0BF0: uid=1000 from=<km>
Mar 31 18:29:02 ubuntu postfix/cleanup[9784]: 421AC1C0BF0: message-id=<20160331162902.421AC1C0BF0@ubuntu>
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 421AC1C0BF0: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:29:02 ubuntu postfix/pickup[10038]: 551331C0B7C: uid=1005 from=<ts3>
Mar 31 18:29:02 ubuntu postfix/cleanup[9783]: 551331C0B7C: message-id=<20160331162902.551331C0B7C@ubuntu>
Mar 31 18:29:02 ubuntu postfix/local[9474]: 2FF601C0B87: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.35, delays=0.21/0.01/0/0.13, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 2FF601C0B87: removed
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 551331C0B7C: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:29:02 ubuntu postfix/local[9886]: 551331C0B7C: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.44, delays=0.38/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:29:02 ubuntu postfix/qmgr[937]: 551331C0B7C: removed
Mar 31 18:29:03 ubuntu postfix/local[9475]: 421AC1C0BF0: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=1.3, delays=0.24/0/0/1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:29:03 ubuntu postfix/qmgr[937]: 421AC1C0BF0: removed
Mar 31 18:29:38 ubuntu postfix/smtpd[10442]: connect from DIR-826L.chello.pl[89.65.194.138]
Mar 31 18:29:38 ubuntu postfix/smtpd[10442]: warning: SASL: Connect to private/auth failed: No such file or directory
Mar 31 18:29:38 ubuntu postfix/smtpd[10442]: fatal: no SASL authentication mechanisms
Mar 31 18:29:38 ubuntu postfix/smtpd[10446]: connect from DIR-826L.chello.pl[89.65.194.138]
Mar 31 18:29:38 ubuntu postfix/smtpd[10446]: warning: SASL: Connect to private/auth failed: No such file or directory
Mar 31 18:29:38 ubuntu postfix/smtpd[10446]: fatal: no SASL authentication mechanisms
Mar 31 18:29:39 ubuntu postfix/master[933]: warning: process /usr/lib/postfix/smtpd pid 10442 exit status 1
Mar 31 18:29:39 ubuntu postfix/master[933]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Mar 31 18:29:39 ubuntu postfix/master[933]: warning: process /usr/lib/postfix/smtpd pid 10446 exit status 1
Mar 29 01:40:02 ubuntu postfix/submission/trivial-rewrite[10453]: message repeated 100 times: [ warning: do not list domain foto-grafik.biz in BOTH mydestination and virtual_alias_domains]
Mar 31 18:30:01 ubuntu postfix/pickup[10038]: 6E5601C0BF3: uid=1000 from=<km>
Mar 31 18:30:01 ubuntu postfix/cleanup[9784]: 6E5601C0BF3: message-id=<20160331163001.6E5601C0BF3@ubuntu>
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 6E5601C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:30:01 ubuntu postfix/pickup[10038]: 861BF1C0B8B: uid=1000 from=<km>
Mar 31 18:30:01 ubuntu postfix/cleanup[9783]: 861BF1C0B8B: message-id=<20160331163001.861BF1C0B8B@ubuntu>
Mar 31 18:30:01 ubuntu postfix/local[9474]: 6E5601C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.2, delays=0.12/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 861BF1C0B8B: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:30:01 ubuntu postfix/pickup[10038]: 98ABA1C0B87: uid=1005 from=<ts3>
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 6E5601C0BF3: removed
Mar 31 18:30:01 ubuntu postfix/cleanup[9784]: 98ABA1C0B87: message-id=<20160331163001.98ABA1C0B87@ubuntu>
Mar 31 18:30:01 ubuntu postfix/local[9886]: 861BF1C0B8B: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.27, delays=0.21/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 861BF1C0B8B: removed
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 98ABA1C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:30:01 ubuntu postfix/pickup[10038]: AE3081C0B7C: uid=1005 from=<ts3>
Mar 31 18:30:01 ubuntu postfix/cleanup[9783]: AE3081C0B7C: message-id=<20160331163001.AE3081C0B7C@ubuntu>
Mar 31 18:30:01 ubuntu postfix/local[9475]: 98ABA1C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.39, delays=0.33/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: 98ABA1C0B87: removed
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: AE3081C0B7C: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:30:01 ubuntu postfix/local[9474]: AE3081C0B7C: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.41, delays=0.36/0/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:30:01 ubuntu postfix/qmgr[937]: AE3081C0B7C: removed
Mar 31 18:31:01 ubuntu postfix/pickup[10038]: C7A421C0BF3: uid=1000 from=<km>
Mar 31 18:31:01 ubuntu postfix/cleanup[9784]: C7A421C0BF3: message-id=<20160331163101.C7A421C0BF3@ubuntu>
Mar 31 18:31:01 ubuntu postfix/qmgr[937]: C7A421C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:31:01 ubuntu postfix/pickup[10038]: DE6401C0B7C: uid=1000 from=<km>
Mar 31 18:31:01 ubuntu postfix/cleanup[9783]: DE6401C0B7C: message-id=<20160331163101.DE6401C0B7C@ubuntu>
Mar 31 18:31:01 ubuntu postfix/local[9475]: C7A421C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.23, delays=0.17/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:31:01 ubuntu postfix/qmgr[937]: C7A421C0BF3: removed
Mar 31 18:31:01 ubuntu postfix/qmgr[937]: DE6401C0B7C: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:31:02 ubuntu postfix/pickup[10038]: 000781C0B8B: uid=1005 from=<ts3>
Mar 31 18:31:02 ubuntu postfix/cleanup[9784]: 000781C0B8B: message-id=<20160331163102.000781C0B8B@ubuntu>
Mar 31 18:31:02 ubuntu postfix/local[9886]: DE6401C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.29, delays=0.22/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:31:02 ubuntu postfix/qmgr[937]: DE6401C0B7C: removed
Mar 31 18:31:02 ubuntu postfix/qmgr[937]: 000781C0B8B: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:31:02 ubuntu postfix/pickup[10038]: 192C81C0B7C: uid=1005 from=<ts3>
Mar 31 18:31:02 ubuntu postfix/cleanup[9783]: 192C81C0B7C: message-id=<20160331163102.192C81C0B7C@ubuntu>
Mar 31 18:31:02 ubuntu postfix/local[9475]: 000781C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.39, delays=0.32/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:31:02 ubuntu postfix/qmgr[937]: 000781C0B8B: removed
Mar 31 18:31:02 ubuntu postfix/qmgr[937]: 192C81C0B7C: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:31:02 ubuntu postfix/local[9474]: 192C81C0B7C: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.46, delays=0.41/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:31:02 ubuntu postfix/qmgr[937]: 192C81C0B7C: removed
Mar 31 18:31:19 ubuntu postfix/anvil[10447]: statistics: max connection rate 2/60s for (smtp:89.65.194.138) at Mar 31 18:29:38
Mar 31 18:31:19 ubuntu postfix/anvil[10447]: statistics: max connection count 2 for (smtp:89.65.194.138) at Mar 31 18:29:38
Mar 31 18:31:19 ubuntu postfix/anvil[10447]: statistics: max cache size 1 at Mar 31 18:29:38
Mar 31 18:32:02 ubuntu postfix/pickup[10038]: 2CA6E1C0BF3: uid=1000 from=<km>
Mar 31 18:32:02 ubuntu postfix/cleanup[9784]: 2CA6E1C0BF3: message-id=<20160331163202.2CA6E1C0BF3@ubuntu>
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 2CA6E1C0BF3: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:32:02 ubuntu postfix/pickup[10038]: 423591C0B7C: uid=1000 from=<km>
Mar 31 18:32:02 ubuntu postfix/cleanup[9783]: 423591C0B7C: message-id=<20160331163202.423591C0B7C@ubuntu>
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 423591C0B7C: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:32:02 ubuntu postfix/pickup[10038]: 5240A1C0B87: uid=1005 from=<ts3>
Mar 31 18:32:02 ubuntu postfix/cleanup[9784]: 5240A1C0B87: message-id=<20160331163202.5240A1C0B87@ubuntu>
Mar 31 18:32:02 ubuntu postfix/local[9886]: 2CA6E1C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.29, delays=0.17/0/0/0.12, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 2CA6E1C0BF3: removed
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 5240A1C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:32:02 ubuntu postfix/pickup[10038]: 66CB51C0B8B: uid=1005 from=<ts3>
Mar 31 18:32:02 ubuntu postfix/cleanup[9783]: 66CB51C0B8B: message-id=<20160331163202.66CB51C0B8B@ubuntu>
Mar 31 18:32:02 ubuntu postfix/local[9475]: 5240A1C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.34, delays=0.28/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 5240A1C0B87: removed
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 66CB51C0B8B: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:32:02 ubuntu postfix/local[9886]: 66CB51C0B8B: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.43, delays=0.37/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:32:02 ubuntu postfix/qmgr[937]: 66CB51C0B8B: removed
Mar 31 18:32:03 ubuntu postfix/local[9474]: 423591C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=1.5, delays=0.21/0/0/1.2, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:32:03 ubuntu postfix/qmgr[937]: 423591C0B7C: removed
Mar 31 18:33:01 ubuntu postfix/pickup[10038]: 8E8931C0BF3: uid=1005 from=<ts3>
Mar 31 18:33:01 ubuntu postfix/cleanup[9784]: 8E8931C0BF3: message-id=<20160331163301.8E8931C0BF3@ubuntu>
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: 8E8931C0BF3: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:33:01 ubuntu postfix/pickup[10038]: A289B1C0B8B: uid=1000 from=<km>
Mar 31 18:33:01 ubuntu postfix/cleanup[9783]: A289B1C0B8B: message-id=<20160331163301.A289B1C0B8B@ubuntu>
Mar 31 18:33:01 ubuntu postfix/local[9475]: 8E8931C0BF3: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.23, delays=0.15/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: 8E8931C0BF3: removed
Mar 31 18:33:01 ubuntu postfix/pickup[10038]: B4DDA1C0B7C: uid=1000 from=<km>
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: A289B1C0B8B: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:33:01 ubuntu postfix/cleanup[9784]: B4DDA1C0B7C: message-id=<20160331163301.B4DDA1C0B7C@ubuntu>
Mar 31 18:33:01 ubuntu postfix/local[9474]: A289B1C0B8B: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.31, delays=0.24/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: A289B1C0B8B: removed
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: B4DDA1C0B7C: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:33:01 ubuntu postfix/pickup[10038]: CDD971C0B87: uid=1005 from=<ts3>
Mar 31 18:33:01 ubuntu postfix/cleanup[9783]: CDD971C0B87: message-id=<20160331163301.CDD971C0B87@ubuntu>
Mar 31 18:33:01 ubuntu postfix/local[9475]: B4DDA1C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.4, delays=0.34/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: CDD971C0B87: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: B4DDA1C0B7C: removed
Mar 31 18:33:01 ubuntu postfix/local[9886]: CDD971C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.43, delays=0.39/0/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:33:01 ubuntu postfix/qmgr[937]: CDD971C0B87: removed
Mar 31 18:34:01 ubuntu postfix/pickup[10038]: EAA0F1C0BF3: uid=1000 from=<km>
Mar 31 18:34:01 ubuntu postfix/cleanup[9784]: EAA0F1C0BF3: message-id=<20160331163401.EAA0F1C0BF3@ubuntu>
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: EAA0F1C0BF3: from=<km@foto-grafik.biz>, size=718, nrcpt=1 (queue active)
Mar 31 18:34:02 ubuntu postfix/pickup[10038]: 0D6AB1C0B87: uid=1005 from=<ts3>
Mar 31 18:34:02 ubuntu postfix/cleanup[9783]: 0D6AB1C0B87: message-id=<20160331163402.0D6AB1C0B87@ubuntu>
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 0D6AB1C0B87: from=<ts3@foto-grafik.biz>, size=627, nrcpt=1 (queue active)
Mar 31 18:34:02 ubuntu postfix/pickup[10038]: 1C3A71C0BF0: uid=1005 from=<ts3>
Mar 31 18:34:02 ubuntu postfix/cleanup[9784]: 1C3A71C0BF0: message-id=<20160331163402.1C3A71C0BF0@ubuntu>
Mar 31 18:34:02 ubuntu postfix/local[9475]: EAA0F1C0BF3: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.27, delays=0.16/0/0/0.1, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: EAA0F1C0BF3: removed
Mar 31 18:34:02 ubuntu postfix/local[9474]: 0D6AB1C0B87: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.3, delays=0.21/0/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 0D6AB1C0B87: removed
Mar 31 18:34:02 ubuntu postfix/pickup[10038]: 324601C0B7C: uid=1000 from=<km>
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 1C3A71C0BF0: from=<ts3@foto-grafik.biz>, size=722, nrcpt=1 (queue active)
Mar 31 18:34:02 ubuntu postfix/cleanup[9783]: 324601C0B7C: message-id=<20160331163402.324601C0B7C@ubuntu>
Mar 31 18:34:02 ubuntu postfix/local[9886]: 1C3A71C0BF0: to=<ts3@foto-grafik.biz>, orig_to=<ts3>, relay=local, delay=0.39, delays=0.32/0/0/0.07, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 1C3A71C0BF0: removed
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 324601C0B7C: from=<km@foto-grafik.biz>, size=623, nrcpt=1 (queue active)
Mar 31 18:34:02 ubuntu postfix/local[9474]: 324601C0B7C: to=<km@foto-grafik.biz>, orig_to=<km>, relay=local, delay=0.47, delays=0.41/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Mar 31 18:34:02 ubuntu postfix/qmgr[937]: 324601C0B7C: removed

```

And logs from dovecot:
```

Mar 31 18:29:38 imap-login: Info: Aborted login (no auth attempts in 0 secs): user=<>, rip=89.65.194.138, lip=192.168.0.150, session=<DyPCxFov6QBZQcKK>
Mar 31 18:29:38 imap-login: Info: Aborted login (no auth attempts in 0 secs): user=<>, rip=89.65.194.138, lip=192.168.0.150, session=<ISrCxFov6wBZQcKK>

```

---

