---
title: "Send mail from thunderbird fail"
date: 2013-07-13
forum: Server Platforms
---

### Post by mirceabondar on 2013-07-13
Hy...I have installed postfix and dovecot (roundcube for webmail it's working). Thunderbird receive e-mail but can't send. My postfix configuration is:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete versiondebug_peer_level = 2
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


readme_directory = no


# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = mail.andortipo.ro
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = andortipo, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtp_sasl_type = dovecot
smtpd_sasl_path = private/auth
root@andortipo:/etc/postfix#



```

---

### Post by SeijiSensei on 2013-07-13
> ```
mynetworks = 127.0.0.0/8
```

That restricts connections to the "localhost" interface.  To connect over the network, you need to include the correct network subnets like 192.168.1.0/24 or whatever your network uses.

See: [http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from)  and the rest of the Postfix documentation there.

---

