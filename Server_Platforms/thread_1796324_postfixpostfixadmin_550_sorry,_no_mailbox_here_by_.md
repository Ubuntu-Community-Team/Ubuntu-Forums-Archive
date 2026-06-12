---
title: "postfix/postfixadmin: 550 sorry, no mailbox here by that name"
date: 2011-07-03
forum: Server Platforms
---

### Post by LoneWolfJack on 2011-07-03
hello forum,

so I decided to play around with postfix and SASL. I followed through the ubuntu wiki pages and everything seems to have been set up right. postfixadmin works and I can manage mailboxes from there.

the only thing is: every time I try to send a test email from one of my email addresses on a different server, I get "550 sorry, no mailbox here by that name".

the DNS settings should be correct:
```

; <<>> DiG 9.7.0-P1 <<>> mx mydomain.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6987
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 1

;; QUESTION SECTION:
;mydomain.com.			IN	MX

;; ANSWER SECTION:
mydomain.com.		86400	IN	MX	10 mail.mydomain.com.

;; AUTHORITY SECTION:
mydomain.com.		86400	IN	NS	ns1.isp.com.
mydomain.com.		86400	IN	NS	ns2.isp.com.
mydomain.com.		86400	IN	NS	ns3.isp.com.

;; ADDITIONAL SECTION:
mail.mydomain.com.	86400	IN	A	123.123.123.123

```

I never tried to set up my own postfix server before so I'm kinda at the end of my ropes. I guess somehow postfix doesn't properly communicate with postfixadmin. any way I can check that?

any help would be appreciated.

---

### Post by LoneWolfJack on 2011-07-03
main.cf
```

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

# Virtual Mailbox Domain Settings
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes

```


/etc/postfix/mysql_virtual_alias_maps.cf:
```

user = postfix
password = ------------
hosts = 127.0.0.1
dbname = postfix
table = alias
select_field = goto
where_field = address

```

---

