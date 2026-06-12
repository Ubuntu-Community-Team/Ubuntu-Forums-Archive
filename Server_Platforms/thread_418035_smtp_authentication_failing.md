---
title: "smtp authentication failing"
date: 2007-04-22
forum: Server Platforms
---

### Post by adza on 2007-04-22
hi there, i am really at the end of this one... for the last couple of hours i can't for the life of me figure out why my evolution client (on desktop) doesn't hit the smtp server properly. The passwords are correct because it receives mail alright, however when i try to send mail, the error is Bad Authentication response from server..

the main.cf file is below.....


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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = adza.homedns.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = adza.homedns.org, localhost.homedns.org, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/


the smptd.conf file is also like such...
pwcheck_method: saslauthd
mech_list: plain login


i can't think of why this doesn't work.... i've been all over the net.... !!!! please help!

---

### Post by heimo on 2007-04-22
I don't have answer to your questions, but I can point to a wonderful guide, which I've used to successfully setup mail server, which I'm using with evolution (*.
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

*) And just when I sent this, I remember that I'm not using it as SMTP server (for outgoing mail). I believe I used to do before.

---

### Post by BoneKracker on 2007-04-22
These are probably obvious things you already checked, but just in case:

verify you are using the correct port
verify you are using an acceptable authentication method

---

### Post by adza on 2007-04-22
finally!!! well i had to add this line saslauthd_path: /var/run/saslauthd/mux to the smtpd.conf file, for those that are interested..... what an afternoon!!! (i think i deleted that line earlier whilst screwing around - doh!@)

---

### Post by heimo on 2007-04-22
I know _so_ well what you're talking about. I've been messing around with mail server settings, wondering, debugging, listening to network traffic, telneting around and speaking smtp - and when pieces come together and it starts working, it's a wonderful relief. "Now I'm not gonna touch it for next two years."

---

### Post by adza on 2007-04-22
*****Edit******* the previous example only sort of worked, it passed auth in evolution.. still wasn't sending mail however... i have now altered to send the smtp via my isp mail server... working like a charm! :)

---

