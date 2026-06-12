---
title: "Probably simple postfix problem"
date: 2009-01-03
forum: Server Platforms
---

### Post by shingalated on 2009-01-03
I am unable to send mail.
When I telnet to my postfix server to test it using
telnet localhost 25
All I get is: 
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

I do not get the 220 my.server.com ESMTP Postfix (Ubuntu) or any of the 250 messages.
according to netstat and nmap postfix is running.
I followed the how to pretty much exactly from here:
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p1]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p1")

---

### Post by zenmatrix on 2009-01-03
Check here [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

howtoforge is great but they tend to over complicate things sometimes. If you still have problems it would help to post the /etc/postfix/main.cf file.

---

### Post by HermanAB on 2009-01-03
Hmm, and once you are totally fed-up with fighting Postfix, go here and install Citadel instead.  You won't be sorry:[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Here is a guide: [http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)

Cheers,

Herman

---

### Post by shingalated on 2009-01-03
Well I tried reconfiguring postfix with the settings listed in the Ubuntu server guide, but still no 220 greeting and no response to "ehlo localhost" So I copied back the config I got from the howtoforge guide, since I would like to use virtual mysql mail users.  Here is my configuration:
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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = my.server.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = my.server.com, localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_rec$
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
mynetwork = 127.0.0.0/8


```

---

### Post by shingalated on 2009-01-04
Oops, I checked the mail log when starting postfix and I just forgot to create a config file...

---

### Post by albinootje on 2009-01-04
> **shingalated said:**
> Oops, I checked the mail log when starting postfix and I just forgot to create a config file...

So.. the problem is solved now ? If so, please mark it SOLVED :)

---

