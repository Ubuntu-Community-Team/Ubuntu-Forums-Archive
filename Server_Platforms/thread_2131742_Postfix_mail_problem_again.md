---
title: "Postfix mail problem again"
date: 2013-04-02
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-02
I got it solved before, but I dont know what happend cause I have some errors again.
Here is the last thread where I got it solved [http://ubuntuforums.org/showthread.php?t=2073767](http://ubuntuforums.org/showthread.php?t=2073767)

And here are the error log from mail.log

> 
.no>, relay=local, delay=354991, delays=354990/0.41/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: 5A22E13FAB7: to=<www-data@truckstop24.no>, relay=local, delay=411697, delays=411696/0.41/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29981]: 792D713FA9C: to=<root@truckstop24.no>, relay=local, delay=127475, delays=127474/0.41/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: warning: hash:/etc/postfix/aliases: lookup of 'www-data' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29972]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29972]: warning: hash:/etc/postfix/aliases: lookup of 'www-data' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29965]: 77E061407EA: to=<root@truckstop24.no>, relay=local, delay=390693, delays=390692/0.48/0/0.1, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29970]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29970]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: 5A48513FDD8: to=<www-data@truckstop24.no>, relay=local, delay=420097, delays=420096/0.54/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: 0230414344F: to=<root@truckstop24.no>, relay=local, delay=106512, delays=106511/0.54/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29972]: 9E11E13FDD9: to=<www-data@truckstop24.no>, relay=local, delay=415896, delays=415896/0.54/0/0.12, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29965]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29965]: warning: hash:/etc/postfix/aliases: lookup of 'www-data' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: warning: hash:/etc/postfix/aliases: lookup of 'www-data' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29970]: D8A0F143532: to=<root@truckstop24.no>, relay=local, delay=241317, delays=241317/0.59/0/0.11, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29981]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29981]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29966]: 4945D140826: to=<www-data@truckstop24.no>, relay=local, delay=430298, delays=430297/0.65/0/0.11, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29965]: 9B1E213F9CF: to=<www-data@truckstop24.no>, relay=local, delay=411697, delays=411696/0.65/0/0.11, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: F1A61140A92: to=<root@truckstop24.no>, relay=local, delay=302788, delays=302787/0.65/0/0.11, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29981]: 6639F1431C1: to=<root@truckstop24.no>, relay=local, delay=43769, delays=43768/0.7/0/0.11, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: warning: hash:/etc/postfix/aliases is unavailable. open database /etc/postfix/aliases.db: No such file or directory
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: warning: hash:/etc/postfix/aliases: lookup of 'root' failed
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29968]: CC82A143528: to=<root@truckstop24.no>, relay=local, delay=279517, delays=279516/0.77/0/0.1, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 21:36:17 roger-G31T-M7 postfix/local[29973]: 8A0831407E3: to=<root@truckstop24.no>, orig_to=<root>, relay=local, delay=391627, delays=391626/0.81/0/0.08, dsn=4.3.0, status=deferred (alias database unavailable)
Apr  2 22:08:24 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31285, secured
Apr  2 22:08:24 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=44/697
Apr  2 22:08:24 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31287, secured
Apr  2 22:08:24 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=475/1948
Apr  2 22:08:24 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31289, secured
Apr  2 22:08:25 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:08:27 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31293, secured
Apr  2 22:08:27 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:08:52 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31307, secured
Apr  2 22:08:52 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:08:56 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31309, secured
Apr  2 22:08:56 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:08:58 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31313, secured
Apr  2 22:08:58 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:08:58 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31315, secured
Apr  2 22:08:59 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:09:11 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31389, secured
Apr  2 22:09:11 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=753/468
Apr  2 22:09:11 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=31391, secured
Apr  2 22:09:11 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=296/212683
Apr  2 22:09:36 roger-G31T-M7 postfix/postfix-script[31637]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:36 roger-G31T-M7 postfix/postfix-script[31658]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:09:46 roger-G31T-M7 postfix/postfix-script[31700]: stopping the Postfix mail system
Apr  2 22:09:46 roger-G31T-M7 postfix/master[1211]: terminating on signal 15
Apr  2 22:09:46 roger-G31T-M7 postfix/postfix-script[31769]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:46 roger-G31T-M7 postfix/postfix-script[31790]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:09:46 roger-G31T-M7 postfix/postqueue[31809]: warning: Mail system is down -- accessing queue directly
Apr  2 22:09:47 roger-G31T-M7 postfix/postfix-script[31879]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:47 roger-G31T-M7 postfix/postfix-script[31900]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:09:47 roger-G31T-M7 postfix/postfix-script[31918]: starting the Postfix mail system
Apr  2 22:09:47 roger-G31T-M7 postfix/master[31919]: daemon started -- version 2.9.3, configuration /etc/postfix
Apr  2 22:09:48 roger-G31T-M7 postfix/postfix-script[31988]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:48 roger-G31T-M7 postfix/postfix-script[32009]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:09:54 roger-G31T-M7 postfix/postfix-script[32113]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:54 roger-G31T-M7 postfix/postfix-script[32134]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:09:57 roger-G31T-M7 postfix/postfix-script[32239]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:09:57 roger-G31T-M7 postfix/postfix-script[32260]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:18:25 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=32590, secured
Apr  2 22:18:25 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=85/686
Apr  2 22:28:25 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=592, secured
Apr  2 22:28:25 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=85/686
Apr  2 22:36:27 roger-G31T-M7 postfix/postfix-script[941]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:36:27 roger-G31T-M7 postfix/postfix-script[967]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:36:31 roger-G31T-M7 postfix/postfix-script[1086]: warning: not owned by postfix: /var/lib/postfix/./verify_cache
Apr  2 22:36:31 roger-G31T-M7 postfix/postfix-script[1107]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Apr  2 22:38:25 roger-G31T-M7 dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=1262, secured
Apr  2 22:38:25 roger-G31T-M7 dovecot: imap(roger): Disconnected: Logged out bytes=85/686



and the postfix main.cf file

> 
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
mynetworks = 79.161.88.51/24, 127.0.0.1/8
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_non_fqdn_recipient, reject_unknown_recipient_domain, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, pcre:/etc/postfix/helo_checks, check_sender_mx_access, cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, check_relay_domains, permit
smtpd_client_restrictions = permit_mynetworks, reject


---

### Post by AvengerX9 on 2013-04-03
anyone knows whats going on here ?

---

### Post by Azrayal on 2013-04-05
Hi, 

Looks like an ownership issue with postfix. 

Check the ownership of /var/lib/postfix 

ls -lrt /var/lib/ | grep postfix 

If it is the issue try:
chown postfix:postfix -R /var/lib/postfix
/etc/init.d/postfix restart

---

### Post by AvengerX9 on 2013-04-05
I changed the Mynetworks line to this

> mynetworks = 127.0.0.0/8 79.161.88.0/32

and it works :)

---

### Post by darkod on 2013-04-06
Just out of interest, what is the gateway of the server, the IP of the gateway?

That 79.161.88.0/32 value looks wrong to me, but it works for you. I must be getting something wrong. :)

---

### Post by AvengerX9 on 2013-04-06
this is the ip of the gateway 79.161.88.51, I tried using 79.161.88.0/24 but it didnt work and I looked on the postfix url and just tried an example from the mynetwork section and it works

---

### Post by darkod on 2013-04-06
Thanks. Good that it works. But I'm oficially still very confused. The way I have understood it, the /32 mask means only that specific IP, only the one specified. And your gateway is not the .0 it's the .51. So, your server is definitely not getting the mails through .0.

In fact, the .0 and .255 are not used as far as I know, their purpose is different.

If it worked with 79.161.88.51/32 I would understand that since that would mean only one IP, the .51.
Or if it worked with 79.161.88.0/24 I would understand it too, since that covers all IPs from .1 to .254 where your gateway .51 belongs.

But none of that worked and instead the .0/32 worked.

---

