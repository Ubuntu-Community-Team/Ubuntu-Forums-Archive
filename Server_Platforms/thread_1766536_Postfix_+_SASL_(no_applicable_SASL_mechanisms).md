---
title: "Postfix + SASL (no applicable SASL mechanisms)"
date: 2011-05-24
forum: Server Platforms
---

### Post by anton_mr on 2011-05-24
Hello, i've been trying to set up Postfix on my VPS Ubuntu 10.04.2

I have Webmin 1.550 installed on it and before following a step-by-step manual tried to just install Postfix Mail server from webmin modules. It did not work so i followed this guide:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

On the step which said:
> Next edit /etc/postfix/sasl/smtpd.conf and add the following lines:

pwcheck_method: saslauthd
mech_list: plain login

I ran into the first problem: there was no such file, however there was a directory /etc/postfix/sasl/

So i googled the problem and ran into this thread:
[http://ubuntuforums.org/archive/index.php/t-242350.html](http://ubuntuforums.org/archive/index.php/t-242350.html)

There was the answer, so i just went for it and created the file with sudo pico /etc/postfix/sasl/smtpd.conf and added the lines (but already was worrying that i have sasl somewhere else but not here.


Then i followed the guide to the end and did everything appropriately as far as i know.

On the step of checking main.cf of Postfix i noticed that my main.cf is missing some lines.

Guide said this:
> The file /etc/postfix/main.cf should now look like this:


# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = server1.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server1.example.com, example.com, localhost.example.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
#Use these on Postfix 2.2.x only
#smtp_use_tls = yes
#smtpd_use_tls = yes
#For Postfix 2.3 or above use:
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom 

My main.cf said this:

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.mydomain.com, mydomain.com, localhost.mydomain.com, localhost
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
mydomain = mydomain.com
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_security_level = may
smtpd_sasl_auth_enable = yes
relayhost = 
inet_interfaces = all
inet_protocols = all
mynetworks = 127.0.0.0/8
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtp_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
myhostname = mail.mydomain.com

So i just copied what guide said and replaced example domains with my domain and kept going.


So the problem is when i do

telnet localhost 25

It goes like this:
> telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
Connection closed by foreign host.

it closed right away.
tried again.

> telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
(...there was a break so i thought i should try ehlo...)
ehlo localhost
(...long break...)
Connection closed by foreign host.


So i took the backup of main.cf that i had and restarted the postfix with it. Same ****.
From the thread above i assumed it has something to do with my main.cf but i looked into /var/log/mail.log

> May 24 21:49:36 poko postfix/master[23622]: daemon started -- version 2.7.0, configuration /etc/postfix
May 24 21:49:43 poko postfix/smtpd[23627]: connect from localhost.localdomain[127.0.0.1]
May 24 21:49:43 poko postfix/smtpd[23627]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
May 24 21:49:43 poko postfix/smtpd[23627]: fatal: no SASL authentication mechanisms
May 24 21:49:44 poko postfix/master[23622]: warning: process /usr/lib/postfix/smtpd pid 23627 exit status 1
May 24 21:49:44 poko postfix/master[23622]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling


Any help apperciated, i am pretty sure it's not only me who ran into this.

Thanks.

---

### Post by anton_mr on 2011-05-25
Still no luck for me, i'm planning to uninstall all and follow this guide:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

