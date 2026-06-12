---
title: "Postfix Basic Configuration"
date: 2009-04-06
forum: Server Platforms
---

### Post by Drezard on 2009-04-06
Hey guys,

I manage a couple of exchange 2003 servers and they are pretty flakey, to say the best of them. Im trying to configure a postfix server to act as a backup mail server for all of these servers.

What Im wanting is, when one of the exchange servers goes down (say example.com's mail server), the mail starts getting forwarded to the secondary mx record which is this postfix server. This postfix server then holds this mail and does NOT issue NDRs or bounces, even if the mail is over a week old. It just holds it. Once the server comes backup, this backup postfix mail server drops all of the mail to this server.

I know there is a way for postfix to do this. Just not sure exactly how to configure it.

Here is my config (That I attempted), can someone please give me some direction or pointers on what I should have.

main.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# BACKUP MX SETTINGS
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
relay_domains = example.com, example2.com
relay_recipient_maps = hash:/etc/postfix/relay_recipients

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = backupmx.commsit.com.au
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = backupmx.example.com, localhost.example.com, , localhost
relayhost =
mynetworks = 123.123.123.123/32,127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


``` 

Regards,

Daniel

---

### Post by HermanAB on 2009-04-07
Hmmm, you can likely replace *all* your Exchange servers with a *single* Citadel server:
[http://www.citadel.org](http://www.citadel.org)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

That should be easier and cheaper than fixing the mess that you got, since Citadel can handle tens of thousands of users on one machine - and it scales too.

---

