---
title: "Can't send email to external domains"
date: 2010-01-09
forum: Server Platforms
---

### Post by madmacz on 2010-01-09
Hello! I've set up a mail server using Postfix + dovecot. It works just fine sending email to users in my domain. However, I can't send email to external domains (like gmail, yahoo, etc) different than mine. I've tried sending from a remote connection using Evolution and I get the following message on mail.log

Jan  8 10:45:20 mail postfix/smtpd[14911]: connect from unknown[]
Jan  8 10:45:21 mail postfix/smtpd[14911]: NOQUEUE: reject: RCPT from unknown[]: 550 5.1.1 <lobomacz@gmail.com>: **Recipient address rejected: User unknown in local recipient table**; from=<user@mydomain.com> to=<lobomacz@gmail.com> proto=ESMTP helo=<[10.24.4.230]>
Jan  8 10:45:21 mail dovecot: pop3-login: Login: user=<user>, method=PLAIN, rip=, lip=
Jan  8 10:45:22 mail postfix/smtpd[14911]: disconnect from unknown[]


my main.cf is


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no
readme_directory = no

smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
#smtpd_helo_required = no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/domains
relayhost = 
mynetworks = 127.0.0.0/8, 10.30.0.0/16, 192.168.0.0/24
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mydomain = mydomain.com
relay_domains = $mydestination

please help me figure out what's wrong with this.

thanks in advance,

---

### Post by madmacz on 2010-01-09
The domains I can't send or receive mail from are any domain different than mine e.g. gmail.com, yahoo.com

also, the domains listed in the file /etc/postfix/domains used by the mydestination directive are: $myhostname, $mydomain, localhost.$mydomain, yahoo.com, gmail.com, hotmail.com, localhost

I'm greatly thankful for your help, I appreciate it!

---

### Post by gombadi on 2010-01-10
> 
Jan 8 10:45:21 mail postfix/smtpd[14911]: NOQUEUE: reject: RCPT from unknown[]: 550 5.1.1 <lobomacz@gmail.com>: Recipient address rejected: User unknown in local recipient table; from=<user@mydomain.com> to=<lobomacz@gmail.com> proto=ESMTP helo=<[10.24.4.230]>


and

> 
also, the domains listed in the file /etc/postfix/domains used by the mydestination directive are: $myhostname, $mydomain, localhost.$mydomain, yahoo.com, gmail.com, hotmail.com, localhost


These indicate that you want email for yahoo.com, gmail.com, hotmail.com to be delivered to you server. Your server is looking for a user lobomacz but it can not find it so it bounces the message.

The mydestination value is only for domains that you want to receive email for - i.e. deliver to a local mailbox. My guess is you don't want these domains in your mydestination.

---

