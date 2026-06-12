---
title: "Postfix problem"
date: 2009-02-20
forum: Server Platforms
---

### Post by whaase on 2009-02-20
I set up our mail server and it is fully functional with Squirrel Mail installed as well. 

The issue I am having is the outgoing mail always comes as [email]user@server.domain.com[/email] 

I'm trying to get it to change to [email]user@domain.com[/email]

I've tried just about every option I can google. 

I know I could just set the users reply-too address, but that would be a huge pain with 100's of users.

What am I missing? How can I fix it?

---

### Post by spiderbatdad on 2009-02-20
i believe vitual alaises are set in the main.cf or using postconf -e
for example:
```
sudo postconf -e "virtual_alias_domains = server.domain.com  domain.com"

```
More here: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

The only other thing that occurs to me is whether you are using mysql database, and how maildir is defined there.

---

### Post by E_K on 2009-02-20
check /etc/postfix/main.cf

---

### Post by whaase on 2009-02-20
> **spiderbatdad said:**
> i believe vitual alaises are set in the main.cf or using postconf -e
for example:
```
sudo postconf -e "virtual_alias_domains = server.domain.com  domain.com"

```
More here: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

The only other thing that occurs to me is whether you are using mysql database, and how maildir is defined there.

No mysql. I used this site to set everything up [http://www.howtoforge.com/perfect-server-ubuntu-8.10]("http://www.howtoforge.com/perfect-server-ubuntu-8.10")

I tried the 

```
sudo postconf -e "virtual_alias_domains = server.domain.com  domain.com"

```

Still sending from server.domain.com

---

### Post by spiderbatdad on 2009-02-20
could you post your main.cf?

---

### Post by whaase on 2009-02-20
> **spiderbatdad said:**
> could you post your main.cf?

Sure can

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhost = server.domain.ca
mydomain = domain.ca
myorigin = $mydomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = domain.ca, server.domain.ca, localhost.domain.ca, localhost.localdomain, localhost
relayhost = somerelayhost.net
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
append_at_myorigin = no
append_dot_mydomain = no
virtual_alias_domains = server.domain.ca domain.ca

```

---

### Post by spiderbatdad on 2009-02-20
Before anythng else try: sudo postconf -e "virtual_alias_maps = hash:/etc/postfix/virtual"

try removing server.domain.ca from mydestination? Sorry. not an expert at this and certain mailservers take a lot of tinkering.

---

### Post by whaase on 2009-02-20
> **spiderbatdad said:**
> Before anythng else try: sudo postconf -e "virtual_alias_maps = hash:/etc/postfix/virtual"

try removing server.domain.ca from mydestination? Sorry. not an expert at this and certain mailservers take a lot of tinkering.

Nope. I'm going nuts. I can't believe its this hard? No one uses a FQDN for a outgoing mail address.

---

### Post by spiderbatdad on 2009-02-20
the problem may lie in /etc/mailname or the mydomain setting. check out flurdy's guide, which is pretty thorough...just scroll down a little to the postfix configuration under "MTA"
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

