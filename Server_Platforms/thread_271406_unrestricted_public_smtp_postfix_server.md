---
title: "unrestricted public smtp postfix server"
date: 2006-10-04
forum: Server Platforms
---

### Post by hypermegachi on 2006-10-04
hey guys, i'm having a hard time finding any tutorial or documentation about how to open up postfix to the world.

i can access the server on the internal network, but i am unable to access it over the internet.

what setting in the config should i be changing?

the idea is to have it public with forced SASL authentication.

thanks.

---

### Post by sonic2000gr on 2006-10-04
Looks like you need to read [this article]("http://www.howtoforge.com/perfect_setup_debian_sarge_p4"). It is based on debian but not much difference here. It is exactly what you need, and my mail server runs thanks to this excellent article.

---

### Post by hypermegachi on 2006-10-06
> **sonic2000gr said:**
> Looks like you need to read [this article]("http://www.howtoforge.com/perfect_setup_debian_sarge_p4"). It is based on debian but not much difference here. It is exactly what you need, and my mail server runs thanks to this excellent article.

i followed this article to the dot...but it wouldn't work.  i'm still unable to access the server outside of the local network.  here's my main.cf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = some_name.mycompany.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = some_name.mycompany.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter =
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

inet_protocols = all

```

do you think maybe my hostname has something to do with it?  my server doesn't have a real hostname (only accessible through the ip address).

---

### Post by hypermegachi on 2006-10-06
whew!!!!  got it!

after a lot more searching and a lot more frustration, i got it working.

notice how in the /etc/default/saslauthd we need to change the path?  also notice we need to do the same to /etc/init.d/saslauthd?  well, that's because debian ships postfix in a chrooted environment.  default, it is not chrooted.

so, my server would mess up the authentication when i was messing around that.  i ended up leaving it chrooted.  otherwise, you have to edit master.cf.

ultimately, master.cf was the problem (which very few tutorials mention).  you need to uncomment all the smtps lines, submission, and options.

---

