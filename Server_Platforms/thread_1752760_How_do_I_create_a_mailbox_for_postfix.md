---
title: "How do I create a mailbox for postfix?"
date: 2011-05-08
forum: Server Platforms
---

### Post by timpa on 2011-05-08
**EDIT: Change the topic, see post #3**

I've been following this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

And done the points up to "Advanced mail server" and are trying to test mailing [EMAIL="mail@mydomain.com"]mail@mydomain.com[/EMAIL] to [EMAIL="mail@mydomain.com"]mail@mydomain.com[/EMAIL] (yes, the same inbox) using Thunderbird, through my own DNS, from the server. 

But I get the following error: *The message can not be sent because the connection to SMTP server mydomain.com timed out.*

And when I check /var/spool/mail/virtual where the mailboxes are supposed to be stored there are none. 

So I'm wondering how I create a mailbox with postfix. 


I can add that I am quite a noob at linux but have to do this in a school project. 

I'm using ubuntu server 10.04 32bit with GUI (yes I know, I know)

---

### Post by falko on 2011-05-09
What are the outputs of ```
netstat -tap
``` and ```
iptables -L
```? Are there any errors in /var/log/mail.log?

---

### Post by timpa on 2011-05-09
Thanks.

I solved it in a different way, I installed ISPconfig instead and solved it that way.

I still don't get the mailing to work, but atleast I can create mailboxes.



**But now I have new problem, I guess I can take it in the same thread and rename it a little:**

It does not want to send mail:
This is what ISPconfig3 Monitor tells me repeatedly:

Mail Log
```
May 9 15:13:22 linuxmail postfix/smtp[2155]: 565ED61BC6: to=, relay=none, delay=439, delays=418/0.01/20/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=linuxmail.domain.com type=MX: Host not found, try again)
```

My /etc/postfix/main.cf 
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = linuxmail.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = linuxmail.domain.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 linuxmail.domain.com
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf$
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
#content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

---

### Post by falko on 2011-05-09
Did you create DNS records for linuxmail.domain.com?

---

### Post by timpa on 2011-05-09
> **falko said:**
> Did you create DNS records for linuxmail.domain.com?
Yes, but I solved that problem now.

I've successfully sent an email from one of my accounts to an outside email-domain. 

But I can't return it, nor can I send from a user from within my domain to another user within my domain (test@linuxmail.domain.com to [email]test2@linuxmail.domain.com[/email])

Now I get three different errors:

1.
```
postfix/trivial-rewrite[2521]: warning: do not list domain  linuxmail.domain.com in BOTH mydestination and  virtual_alias_domains
```
Even tho I have blocked *mydestination *with a # in etc/postfix/main.cf

2.
```
postfix/smtp[2522]: A66E361BDE: to=, relay=none, delay=0.03, delays=0.03/0/0/0, dsn=5.4.6, status=bounced (mail for linuxmail.domain.com loops back to myself)
```
hostname is FQDN, not localhost

3.
```
getmail: getmailOperationError error (POP error (-ERR Login failed.))
```

---

