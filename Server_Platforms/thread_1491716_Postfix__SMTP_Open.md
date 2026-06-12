---
title: "Postfix  SMTP Open?"
date: 2010-05-23
forum: Server Platforms
---

### Post by kevin2i on 2010-05-23
Curious if someone could take a look at my Postfix install - I'm worried that the SMTP side is not secured.  

I can log in from my MUA (mac mail) without SSL or password authentication. 

I used a few different tutorials to get it set up (the pop3s seems to work fine with SSL on port 995).  I would research this more - hate asking 'newbie' level questions - but I don't want an open SMTP connection. :confused:

Most of the conf files and logs can be found here: rvlvx.com/postfix

Here is main.cf - 
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = mail.rvlvx.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost,mail.rvlvx.com
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client

mtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtpd_tls_auth_only = yes
# missing use tls 2.2 or lower
#smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
# virtual mailboxes
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
soft_bounce = yes

---

### Post by lisati on 2010-05-23
After a few moments thought, a couple of suggestions based on my server's settings to help tighten things up a bit:

Add the following line to enforce rfc821 standards:
```
strict_rfc821_envelopes = yes
```
Change your smtpd_recipient_restrictions line to read:
```
smtpd_recipient_restrictions = reject_invalid_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain,  reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination,  reject_rbl_client bl.spamcop.net
```

This will help limit who can access your network from the outside while allowing connections from within your network. It will also do a little bit of spam blocking as well.
(I'm not sure how to explain all of them quickly: I've based my server's settings on advice found in a number of different tutorials.)

---

### Post by kevin2i on 2010-05-24
I added the above, but it doesn't make a difference. I can log on from another computer to the server and send mail - for example this works without any authentication:

telnet mail.server.com 25
ehlo localhost
sent from: <me@junk.com>
rcpt to: <email@domain.com>
data
hello
.
Since this works, I assume everything is open - 
I just closed my port 25 for now.

conf and log files [http://rvlvx.com/postfix](http://rvlvx.com/postfix)
Thanks for looking!

---

