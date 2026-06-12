---
title: "Issues with mailserver (Postfix)"
date: 2013-01-10
forum: Server Platforms
---

### Post by ericje627 on 2013-01-10
Hello,

Recently I installed a mailserver onto my Ubuntu 12.04LTS 64 bit server system. I've installed and configured everything according to this community provided guide [https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer").
When finished, I experienced a few issues with my mailserver.
- I'm unable to send e-mail from my notebook (Using Outlook 2010) and from my phone neither. It's working from localhost (webmail).
- When sending an e-mail (as user eric) from webmail (Roundcube) the e-mailaddress is set to [email]eric@mail.vaert.be[/email] but I would like to change this to [email]eric@vaert.be[/email] because I'm not receiving email from receipents who reply directely to my message.
As MTA I'm using postfix and I use Dovecot as POP/IMAP server.
Dovecot server is working fine.

Postfix uses the saslauth authentication system, but when I'm trying to loging with my system account (user: eric pass: ***) my authentication gets rejected.

So I actually want to change the [email]eric@mail.vaert.be[/email] to [email]eric@vaert.be[/email] and make it possible to login to Postfix from a remote host.

I appreciate your help in advance
Eric.

Attachment:
My Postfix conf:
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = vaert.be
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = vaert.be, localhost.be, , localhost
mynetworks = [::1]/128#127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = $myhostname 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
always_bcc = bcc@vaert.be
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_client_restrictions = permit_sasl_authenticated
myorigin = vaert.be
relayhost = 
inet_interfaces = all

```

---

### Post by SeijiSensei on 2013-01-11
Your "mynetworks" directive restricts connections to the localhost interface.  See [http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from](http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from) for details.

---

