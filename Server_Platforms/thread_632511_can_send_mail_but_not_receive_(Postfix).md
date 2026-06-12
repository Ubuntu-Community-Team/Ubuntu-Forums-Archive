---
title: "can send mail but not receive (Postfix)"
date: 2007-12-05
forum: Server Platforms
---

### Post by obeisance on 2007-12-05
Hi,

I recently installed Gutsy on a new box and installed postfix.  I can send mail with no issues but inbound mail never makes it.  Senders get the following error:
> This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    [email]sms@inertdomain.com[/email]

Technical details of permanent failure:
PERM_FAILURE: SMTP Error (state 13): 554 5.7.1 <sms@inertdomain.com>: Relay access denied


/var/log/mail.log has the following:
> Dec  5 15:24:33 cathexis postfix/smtpd[29142]: connect from nz-out-0506.google.com[64.233.162.233]
Dec  5 15:24:33 cathexis postfix/smtpd[29142]: NOQUEUE: reject: RCPT from nz-out-0506.google.com[64.233.162.233]: 554 5.7.1 <sms@inertdomain.com>: Relay access denied; from=<slamon@gmail.com> to=<sms@inertdomain.com> proto=ESMTP helo=<nz-out-0506.google.com>
Dec  5 15:24:33 cathexis postfix/smtpd[29142]: disconnect from nz-out-0506.google.com[64.233.162.233]
Dec  5 15:27:53 cathexis postfix/anvil[29144]: statistics: max connection rate 1/60s for (smtp:64.233.162.233) at Dec  5 15:24:33
Dec  5 15:27:53 cathexis postfix/anvil[29144]: statistics: max connection count 1 for (smtp:64.233.162.233) at Dec  5 15:24:33
Dec  5 15:27:53 cathexis postfix/anvil[29144]: statistics: max cache size 1 at Dec  5 15:24:33

main.cf
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = $mydomain

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

myhostname = cathexis.inertdomain.com
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = /etc/mailname
mydestination = $myhostname
relayhost =
mynetworks = 127.0.0.0/8
mynetworks_style = host
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
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom



Am I missing something glaringly obvious, which is possible since this is my first time installing Postfix?

I appreciate any input the masses can provide.

Thanks,

Stef

---

### Post by DDuong on 2007-12-05
Hello there,

This section in the main.cf might be the one causing the issue:

> 
mynetworks = 127.0.0.0/8


You will have to define the network that are allowed to relay through your mail server.  I generally set it to my own network.  For example, my main.cf consists of:

> 
mynetworks = 192.168.2.0/24


After specifying the network, do a "postfix reload" or "postfix restart" and that "should" resolve the issue :)

---

### Post by obeisance on 2007-12-05
I changed it to:

mynetworks = 127.0.0.0/8, 140.186.190.64/26

and received the same result  :/

---

### Post by crouton on 2007-12-05
Remove the public IP and add your local network IP, e.g. 192.168.1.0/8 or what not.  It should also accept interfaces (eth0, eth1)

---

### Post by MJN on 2007-12-05
It's your **mydestination** directive - add **inertdomain.com** to it (i.e. mydestination = localhost, intertdomain.com).

As things currently stand Postfix thinks it is only the final destination for cathexis.inertdomain.com (e.g. <user>@cathexis.inertdomain.com), and hence any other destination (e.g. <user>@inertdomain.com) requires relaying - in the absence of authentication this gets denied (as it should).

Mathew

---

### Post by obeisance on 2007-12-05
Thanks MJN, that did it!

~S

---

