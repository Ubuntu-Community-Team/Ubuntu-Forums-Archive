---
title: "Problem with postfix"
date: 2011-12-02
forum: Server Platforms
---

### Post by egger on 2011-12-02
Hi,
I have a problem with Postfix configuration on my Ubuntu Server x64.

When I'm trying to send first email to get this error:
**451 4.3.0 <info@mydomain.com>: Temporary lookup failure**

```
telnet mail.mydomain.com 25
Trying xxx.xxx.xxx.xxx...
Connected to mail.mydomain.com.
Escape character is '^]'.
220 mail.mydomain.com ESMTP Postfix (Ubuntu)
HELO mail.food.com
250 mail.mydomain.com
MAIL FROM:<admin@mydomain.com>
250 2.1.0 Ok
RCPT TO:<info@mydomain.com>
451 4.3.0 <info@mydomain.com>: Temporary lookup failure
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

What suprises me that my mail.log file is _empty_!

main.cf:
```
postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination =
myhostname = mail.mydomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = no
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_tls_cert_file = /etc/ssl/cert/mailcert.cert
smtpd_tls_key_file = /etc/ssl/private/mailcert.key
smtpd_use_tls = yes
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-forwards.cf, mysql:/etc/postfix/mysql-email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-mailboxes.cf
virtual_uid_maps = static:5000

```

Do you have any idea what could cause this problem?

---

