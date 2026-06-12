---
title: "user creation in postfix"
date: 2011-05-03
forum: Server Platforms
---

### Post by num on 2011-05-03
I used this tutorial to setup to setup iSpconfig postfix courier:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

but i cannot send or receive email:

```
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
B450C72116A 595 Mon May 2 17:33:50 www-data@mail.greensevenstudios.com
(connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
user@greensevenstudios.com

3009C72116F 773 Mon May 2 17:37:31 user@greensevenstudios.com
(connect to 127.0.0.1[127.0.0.1]:10024: Connection refused)
user@greensevenstudios.com
```

Basically when i create users in ISPconfig, something goes wrong, mysql is running and i have postfix-mysql installed and running too. Any ideas? Please help.


my postconf:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
header_checks = regexp:/etc/postfix/header_checks
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_size_limit = 0
mime_header_checks = regexp:/etc/postfix/mime_header_checks
mydestination = mail.greensevenstudios.com, localhost, localhost.localdomain
myhostname = mail.greensevenstudios.com
mynetworks = 127.0.0.0/8 [::1]/128
myorigin = /etc/mailname
nested_header_checks = regexp:/etc/postfix/nested_header_checks
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virt                                                                                                             ual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipien                                                                                                             t_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonica                                                                                                             l_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual                                                                                                             _client.cf
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, che                                                                                                             ck_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth                                                                                                             _destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual                                                                                                             _sender.cf
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysq                                                                                                             l:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = maildrop
virtual_uid_maps = static:5000

```

please help.

---

### Post by falko on 2011-05-03
amavisd isn't running. Please (re)start it.

---

### Post by num on 2011-05-03
i did restart it and got this error:

```
root@mail:/home/server# /etc/init.d/amavis restart
Stopping amavisd: amavisd-new.
Starting amavisd: hostname: Name or service not known
amavisd-new.

```

but the thing is i did set the hostname up?

---

