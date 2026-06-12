---
title: "Yet Another Postfix + Sasl Problem!"
date: 2006-08-22
forum: Server Platforms
---

### Post by terigox on 2006-08-22
Hey everyone, I've read several how tos including Flurdy's and 
[http://www.ubuntuforums.org/showthread.php?t=69337](http://www.ubuntuforums.org/showthread.php?t=69337)

Both of which were great and had much similar info. But for some reason I am still getting a problem authenticating for sending mail, I can receive mail fine and send from localhost!

Here are some messages from my mail.log
```
Aug 22 11:17:34 keera postfix/smtpd[7946]: TLS connection established from uslec-66-255-131-12.cust.uslec.net[66.255.131.12]: TLSv1 with cipher RC4-SHA (128/128 bits)
Aug 22 11:17:34 keera postfix/smtpd[7946]: warning: SASL authentication failure: Password verification failed
Aug 22 11:17:34 keera postfix/smtpd[7946]: warning: uslec-66-255-131-12.cust.uslec.net[66.255.131.12]: SASL PLAIN authentication failed
Aug 22 11:17:34 keera postfix/smtpd[7946]: lost connection after AUTH from uslec-66-255-131-12.cust.uslec.net[66.255.131.12]
Aug 22 11:17:34 keera postfix/smtpd[7946]: disconnect from uslec-66-255-131-12.cust.uslec.net[66.255.131.12]

```

And ls -l /var/spool/postfix/var/run/saslauthd/
I tried to chown this directory, but I guess I really didn't understand what its problem was.
```
jason@keera:/var/log$ ls -al /var/spool/postfix/var/run/saslauthd/
total 12
drwxr-xr-x 2 root sasl 4096 2006-08-22 11:17 .
drwxr-xr-x 3 root root 4096 2006-08-13 20:32 ..
srwxrwxrwx 1 root sasl    0 2006-08-22 11:17 mux
-rw------- 1 root sasl    0 2006-08-22 11:17 mux.accept
-rw------- 1 root sasl    5 2006-08-22 11:17 saslauthd.pid
```

My /etc/default/saslauthd looks like:
```
# This needs to be uncommented before saslauthd will be run automatically
START=yes

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

PARAMS="-m /var/spool/postfix/var/run/saslauthd"

#PWDIR="/var/spool/postfix/var/run/saslauthd"
#PARAMS="-m ${PWDIR}"
#PIDFILE="${PWDIR}/saslauthd.pid"

MECHANISMS="pam"

```

Some relevant lines of my /etc/postfix/main.cf
```
smtpd_tls_auth_only = yes
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
...
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = terigo.com

```

So some of the things I've read talked about the chroot problem, and I thought I addressed that, but it just doesn't want to listen :)

Anyone have any suggestions or other things to try?! Thanks a bunch! :biggrin:

---

### Post by terigox on 2006-08-22
So I think I have figured out this problem already... all I needed to do was take a break for lunch :) It turns out in my /etc/postfix/sasl directory, I still had a copy of my smtp.sql.conf.bak which I thought by renaming would not be used. But aparently sasl or postfix was still using it! So I removed that file, restarted postfix and saslauthd and seems to be working great!

It seems as though there were still some errors from sasl complaining about some SQL parameters missing, turns out by restarting mysql those went away. All is running good now :)

---

