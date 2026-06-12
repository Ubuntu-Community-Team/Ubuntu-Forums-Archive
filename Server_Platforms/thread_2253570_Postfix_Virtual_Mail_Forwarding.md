---
title: "Postfix Virtual Mail Forwarding"
date: 2014-11-20
forum: Server Platforms
---

### Post by Dominic--- on 2014-11-20
Hello all,

I have postfix running on my Ubuntu 12.04LTS server.

On my current setup, I have created a virtual mail environment, where all the mail is stored in /home/vmail/*domain*/[I]email@address.com.
[/I]
This works very well, but for my new setup I need to forward mail.
This doesn't seem to work well with the setup I have currently running.

At the moment, the forwarding on itself works, but the e-mail isn't being dropped in the folder specified above, and the mail is being bounced:
"Nov 20 22:57:59 dwits postfix/error[31234]: 69AAA4A0FCA: **to=<xxxxx.nl/info@xxxxx.nl/**>, orig_to=<info@xxxxx.nl>, relay=none, delay=0.02, delays=0.01/0.01/0/0.01, dsn=5.1.3, **status=bounced (bad address syntax)**"

Anyone knows how to work around this? I have tried multiple vmaps to separate the e-mail addresses but that doesnt work.

The config is added below.

```

home_mailbox = Maildir/


virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_domains = xxxxx.com
virtual_alias_maps = hash:/etc/postfix/vmaps


mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_interfaces = all




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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
#smtpd_recipient_restrictions = permit_mynetworks permit
myhostname = xxxxx.nl
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = 
mynetworks = 127.0.0.0/8 37.34.xxx.xxx
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

The bold indicated format doesn't work. The forwarding with this setup **does** work.

```

**info@xxxx.nl dwits.nl/info@xxxx.nl/**
info@xxxx.com xxxxx@hotmail.com
payment@xxxxx.com info@xxxx.nl
cb1@xxxx.com info@xxxxx.nl

```

Best regards,

Dominic

---

### Post by lisati on 2014-11-20
I believe that Postfix is complaining that "dwits.nl/info@xxxx.nl/" is not a valid email address. Had you hoped for a catchall email address?

---

### Post by Dominic--- on 2014-11-20
Nope.

Like always, when I post a problem, it dont take long for I fix it myself for some reason.

I have separated the vmaps (where the e-mail addresses are stored) again, and the one who need to be forwarded configured for virtual_alias_maps.
The ones who need to be stored locally, in the /home/vmail/*domain* folders, I've assigned the vmap to virtual_mailbox_maps.

Tested it, and works very well now.

---

