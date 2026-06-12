---
title: "postfix bouncing external mail/ internal mail working ubuntu 12.04"
date: 2013-04-12
forum: Server Platforms
---

### Post by michaelit on 2013-04-12
Hi all,

I have just taken over a ubuntu server 12.04 with postfix/dovecot mail system

all was great for the first week, Now post fix is bouncing all external mail back to sender ive check everything and it looks ok.

Can i please have assistance with this.

I will post all logs etc when i get to work in the morning.

Please tell me all logs needed to find problem(s)

Many thanks in advance

Mike.

---

### Post by michaelit on 2013-04-12
```
postfix/smtp[92007]: E6F4160085: to=[EMAIL="nigelh@myserver"]nigelh@myserver[/EMAIL], orig_to=<nigel.hosking@seedoils.co.nz>, relay=smtp.xtra.co.nz[xxx.xx.xxx.x]:25, delay=0.42, delays=0.05/0.01/0.27/0.1, dsn=5.0.0, status=bounced (host smtp.xtra.co.nz[xxx.xx.xxx.x] said: 550 Invalid recipient: [EMAIL="nigelh@myserver"]nigelh@myserver[/EMAIL] (in reply to RCPT TO command))
```

---

### Post by michaelit on 2013-04-12
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mydomain.co.nz
alias_maps = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
myorigin = /etc/mailname
mydestination = mydomain.co.nz, mydomain.co.nz, localhost.co.nz, localhost
relayhost = 
mynetworks = 127.0.0.0/8 192.0.0.0/8
# [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24
#mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_restriction_classes = check_greylist
check_greylist = check_policy_service inet:127.0.0.1:60000
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
#check_recipient_restrictions = permit_mynetworks,
#                               permit_sasl_authenticated,
#                               reject_unauth_destination,
#                               check_client_access hash:/etc/postfix/client_blacklist 
                              
mime_header_checks = regexp:/etc/postfix/mime_header_checks.regexp
inet_interfaces = all
#  check_policy_service inet:127.0.0.1:60000,message_size_limit = 20240000
relayhost = smtp.xtra.co.nz
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
```

---

### Post by lisati on 2013-04-12
I've added CODE tags to your posts to aid readability.

The problem could be that you've got this line in your main.cf file:
```
relayhost = smtp.xtra.co.nz
```

If you want your outgoing mail to go through Telecom's servers (well, Yahoo's, actually), you need to use send.xtra.co.nz, with your XTRA account name as a username, and your XTRA password as a password. 

Edit: If Telecom has asked you to go through their servers, you should be able to use the following:
```
relayhost = smtp.officemail.co.nz:587
``` 
If they haven't made such a request, you could try commenting out your relayhost line(s) by putting "#" at the start and then restarting postfix.

---

### Post by michaelit on 2013-04-12
Thankyou for the reply, wouldnt commenting out the relayhost stop mail for mobile users?

---

### Post by lisati on 2013-04-12
> **michaelit said:**
> Thankyou for the reply, wouldnt commenting out the relayhost stop mail for mobile users?

My understanding is that the relayhost parameter tells postfix where to deliver outgoing mail; if you comment it out, Postfix will try to deliver the email directly to the recipient's email provider. 

From [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html) :
> The next-hop destination of non-local mail; overrides non-local domains in recipient addresses.

---

### Post by michaelit on 2013-04-12
Edited stoped/started postfix to no avail

is there a space between # relayhost? or #relayhost

tried both ways no go.

telnet

telnet mail.mydomain.co.nz 25                               
Trying xxx.xx.xx.xx...                                                          
 telnet: Unable to connect to remote host: Connection refused

---

