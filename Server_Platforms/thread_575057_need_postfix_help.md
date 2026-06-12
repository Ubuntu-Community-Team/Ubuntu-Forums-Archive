---
title: "need postfix help"
date: 2007-10-13
forum: Server Platforms
---

### Post by camrant on 2007-10-13
I am completely lost.  I can receive mail perfectly fine however I cannot send any.  I think I may be having an authentication problem because when I try to send the mail it seems that I am finding the server however it just hangs until I get a time out.

when I try to telnet this is what happens
cam@maharaja:~$ telnet camrants.com 25
Trying 67.160.115.89...
Connected to camrants.com.
Escape character is '^]'.


but it will not respond to any commands not even "quit"

below is my config file if anyone can help 

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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = camtse.homeftp.org, localhost, localhost.$mydomain, $mydomainname, $mydomain
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
virtual_alias_maps = hash:/etc/postfix/virtual
smtpd_recipient_restrictions = permin_sasl_authenticated, permit_mynetworks recect_unaut_destination
smtpd_delay_reject = no
debug_peer_list = camrants.com
smtpd_sasl_local_domain = 
smtpd-sasl_auth_enable = yes
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
inet-interfaces = all
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
tls_random_source = dev:/dev/urandom

---

### Post by bmathis on 2007-10-14
From what I can see you need a "**,**" between **permit_mynetworks** and** reject_unauth_destinatio**n (this whole line needs some major spell checking). Also** inet-interfaces = all**  needs to be** inet_interfaces = all**

---

### Post by arclight on 2007-10-15
Your main.cf needs a major spellcheck:

```
smtpd_recipient_restrictions = permin_sasl_authenticated, permit_mynetworks recect_unaut_destination
```

should probably be

```
smtpd_recipient_restrictions = permi**t**_sasl_authenticated permit_mynetworks re**j**ect_unaut**h**_destination
```

and you might want to change

```
mynetworks = 127.0.0.0/8
```

to 

```
mynetworks = 127.0.0.0/8 67.160.115.89/32
```

assuming that 67.160.115.89 is still the IP address of camtse.homeftp.org. You can safely omit the /32 part.

Commas are optional and I tend to leave them out.

My guess is that the typos in the smtpd_recipient_restrictions field are tripping you up. As an example, mine looks like:

```
smtpd_recipient_restrictions =
  permit_mynetworks
  permit_sasl_authenticated
  permit_tls_clientcerts
  hash:/etc/postfix/recipient_blacklist
  hash:/etc/postfix/access
  cidr:/etc/postfix/access_cidr
  reject_multi_recipient_bounce
  reject_non_fqdn_recipient
  reject_unknown_recipient_domain
  reject_unauth_destination
  reject_unlisted_recipient
  check_policy_service inet:127.0.0.1:10031
  permit

```

Note: The 'check_policy_service inet:127.0.0.1:10031' thing is the postfix-policyd greylisting daemon and everything else should be listed in the postfix docs.

One last thing: 'postconf -n' helps with debugging by printing out all the parameters not set to their defaults.

hth,

-- Bob

---

### Post by camrant on 2007-10-15
Wow I am not a spelling bee champ that's for sure, so many typos.  That seemed to fix part of the problem where it at least is connecting and talking to postfix now.  However now it is getting stuck at the password  part.  I am very sure I am using the right password despite my spelling problems.  Where should I look next

---

