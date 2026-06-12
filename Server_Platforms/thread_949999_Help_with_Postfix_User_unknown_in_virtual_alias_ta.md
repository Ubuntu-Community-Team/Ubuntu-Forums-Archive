---
title: "Help with Postfix: User unknown in virtual alias table?"
date: 2008-10-16
forum: Server Platforms
---

### Post by gilgsn on 2008-10-16
Hello,

I've tried everything, and I desperately need help troubleshooting my Postfix installation:

postconf -n
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_size_limit = 10485760
myhostname = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = hash:/etc/postfix/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000

/etc/postfix/virtual
domain1.com DOMAIN
domain2.com DOMAIN
domain3.com DOMAIN

/etc/postfix/vhosts
domain1.com allow
domain2.com allow
domain3.com allow

/etc/postfix/vmaps
[email]info@domain1.com[/email] domain1.com/info/
[email]support@domain1.com[/email] domain1.com/support/
[email]abuse@domain1.com[/email] domain1.com/abuse/
[email]webmaster@domain1.com[/email] domain1.com/webmaster/
[email]offer@domain1.com[/email] domain1.com/offer/
[email]info@domain2.com[/email] domain2.com/info/
[email]support@domain2.com[/email] domain2.com/support/
[email]abuse@domain2.com[/email] domain2.com/abuse/
[email]webmaster@domain2.com[/email] domain2.com/webmaster/
[email]offer@domain2.com[/email] domain2.com/offer/
[email]info@domain3.com[/email] domain3.com/info/

The vmail directories are in the right places, I did postconf on all the files, but still, it doesn't work, even when I add aliases to virtual for local delivery, like: [email]ingo@domain2.com[/email] someuser

What am I forgetting?
Thanks a bunch!

Gil.

---

