---
title: "Postfix mail server problem on Ubuntu server 9.10"
date: 2010-03-24
forum: Server Platforms
---

### Post by DarkRanger on 2010-03-24
Guys!!

Long time since I posted here as I have been back on Windows for a while. My company asked me to create an intraweb for them, so I decided to use ubuntu server as the server to host it locally.

With this comes some challenges. I've installed ubuntu server 9.10 as a LAMP server. Then I installed both the ubuntu desktop package and the Webmin package on the computer. All works well. It had PostFix installed already, so I decided to use that as the local mail server (just so the intraweb can send emails).

Anyhow, long story short, I'm struggling. The email doesn't want to send and it looks like it can't find the recipient. I'm going to post a log here, and then the config file aswell. Coz from what I can deduce in other searches, it seems to be a minor mishap with configuration. I hope someone can help me.

Here goes.

The log:

```
Mar 24 14:26:17 web postfix/pickup[1615]: C4329213DD: uid=33 from=<www-data>
Mar 24 14:26:17 web postfix/cleanup[2453]: C4329213DD: message-id=<20100324122617.C4329213DD@mail.3bm.local>
Mar 24 14:26:17 web postfix/qmgr[1616]: C4329213DD: from=<www-data@mail.3bm.local>, size=2238, nrcpt=1 (queue active)
Mar 24 14:26:18 web postfix/smtp[2456]: C4329213DD: to=<alberts@3bm.co.za>, relay=none, delay=0.32, delays=0.17/0.14/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=3bm.co.za type=AAAA: Host found but no data record of requested type)
Mar 24 14:26:18 web postfix/cleanup[2453]: 1E5BE213DE: message-id=<20100324122618.1E5BE213DE@mail.3bm.local>
Mar 24 14:26:18 web postfix/bounce[2458]: C4329213DD: sender non-delivery notification: 1E5BE213DE
Mar 24 14:26:18 web postfix/qmgr[1616]: 1E5BE213DE: from=<>, size=4178, nrcpt=1 (queue active)
Mar 24 14:26:18 web postfix/qmgr[1616]: C4329213DD: removed
Mar 24 14:26:18 web postfix/local[2459]: 1E5BE213DE: to=<www-data@mail.3bm.local>, relay=local, delay=0.18, delays=0.08/0.01/0/0.09, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Mar 24 14:26:18 web postfix/qmgr[1616]: 1E5BE213DE: removed
```

And then the configuration file:

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.3bm.local
mydomain = mail.3bm.co.za
alias_maps = $alias_database
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 3bmserver.3bm.local, mail.3bm.local, web.3bm.local, localhost.3bm.local, localhost, $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
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

Thank you so much guys!! :KS

---

### Post by jrssystemsnet on 2010-03-24
> Mar 24 14:26:18 web postfix/smtp[2456]: C4329213DD: to=<alberts@3bm.co.za>, relay=none, delay=0.32, delays=0.17/0.14/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=3bm.co.za **type=AAAA**: Host found but no data record of requested type)An AAAA record is an ipv6 host record.  Your Postfix server apparently either does not believe it has ipv4 capabilities, or is not allowed to use ipv4 capabilities.

---

### Post by jrssystemsnet on 2010-03-24
Oh wait - 3bm.co.za is *you*, isn't it?

You've got ipv6 only partially configured.  Either remove all the ipv6 addresses from Postfix's configs (use **postconf -n** to confirm, because you may end up importing some sixbone stuff from the system besides explicitly defining it in main.cf or master.cf), or properly and **fully** implement ipv6 in the DNS for your domain.

---

### Post by DarkRanger on 2010-03-24
Yes, 3bm.co.za is me.

Uhm, how would I remove ipv4 adresses from the configs?

---

### Post by KB1JWQ on 2010-03-24
Drop the inet_protocols=all line and it will work properly, presuming everything else is set correctly.

---

### Post by DarkRanger on 2010-03-24
Okay, I've removed that line. Same log error it seems...

```
Mar 24 16:28:34 web postfix/pickup[5692]: B3D51213E7: uid=33 from=<www-data>
Mar 24 16:28:34 web postfix/cleanup[5808]: B3D51213E7: message-id=<20100324142834.B3D51213E7@mail.3bm.local>
Mar 24 16:28:34 web postfix/qmgr[5693]: B3D51213E7: from=<www-data@mail.3bm.local>, size=2238, nrcpt=1 (queue active)
Mar 24 16:28:35 web postfix/smtp[5810]: B3D51213E7: to=<alberts@3bm.co.za>, relay=none, delay=0.35, delays=0.2/0.15/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=3bm.co.za type=A: Host found but no data record of requested type)
Mar 24 16:28:35 web postfix/cleanup[5808]: 0BD2D213EE: message-id=<20100324142835.0BD2D213EE@mail.3bm.local>
Mar 24 16:28:35 web postfix/bounce[5812]: B3D51213E7: sender non-delivery notification: 0BD2D213EE
Mar 24 16:28:35 web postfix/qmgr[5693]: 0BD2D213EE: from=<>, size=4167, nrcpt=1 (queue active)
Mar 24 16:28:35 web postfix/qmgr[5693]: B3D51213E7: removed
Mar 24 16:28:35 web postfix/local[5813]: 0BD2D213EE: to=<www-data@mail.3bm.local>, relay=local, delay=0.16, delays=0.08/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Mar 24 16:28:35 web postfix/qmgr[5693]: 0BD2D213EE: removed
```

---

### Post by jrssystemsnet on 2010-03-24
you've got DNS resolution problems on that box, apparently.

**cat /etc/resolv.conf**, find the dns servers you're using for resolution, then **dig @server.from.your.resolvconf MX 3bm.co.za** and post results here.

---

### Post by DarkRanger on 2010-03-24
Here we go:

```
> dig @196.192.0.10 MX 3bm.co.za

; <<>> DiG 9.6.1-P2 <<>> @196.192.0.10 MX 3bm.co.za
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44457
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;3bm.co.za.			IN	MX

;; AUTHORITY SECTION:
3bm.co.za.		3600	IN	SOA	3bmserver.3bm.local. hostmaster.3bm.local. 3 900 600 86400 3600

;; Query time: 0 msec
;; SERVER: 196.192.0.10#53(196.192.0.10)
;; WHEN: Wed Mar 24 16:37:30 2010
;; MSG SIZE  rcvd: 93
```

---

### Post by KB1JWQ on 2010-03-24
Yeah, I can hit that MX record just fine from here, something on the OP's end is hosed.

Good catch, jrssystemsnet; my initial (wrong) thought was that the remote system only supported ipv6 traffic!

---

### Post by jrssystemsnet on 2010-03-24
To clarify, DarkRanger: that server, 192.168.0.10, has its own local copy of the zone for 3bm.co.za, which is 1. different from the public DNS info for 3bm.co.za (which may or may not be what you actually intend) and 2. does not include any MX information.

Your Postfix server is looking for an MX record for 3bm.co.za, and when it finds that none is available for the domain, bouncing the message because there is nowhere to deliver it to.

---

### Post by KB1JWQ on 2010-03-24
Slight clarification: When it can't find an MX record, it defaults to using the A record-- but you don't have one of those either, and is why postfix logs complain about the lack of A record.

---

### Post by DarkRanger on 2010-03-24
> **jrssystemsnet said:**
> that server, 192.168.0.10, has its own local copy of the zone for 3bm.co.za

Yes.

> **jrssystemsnet said:**
> which is 1. different from the public DNS info for 3bm.co.za (which may or may not be what you actually intend) and 2. does not include any MX information.

Your Postfix server is looking for an MX record for 3bm.co.za, and when it finds that none is available for the domain, bouncing the message because there is nowhere to deliver it to.

I have no idea. Is it supposed to be different, how do I find this out (seeing as we have a dumbass for an IT admin. ;) )

And how can I fix this should something be wrong?

---

### Post by jrssystemsnet on 2010-03-24
Well, you have two choices:

1. get rid of the local zone for 3bm.co.za

2. add an MX record and an A record for 3bm.co.ca to your local zone for it

To advise you any further than that, I'd need more information about what your situation is and what you're actually trying to achieve. (is this a local mailserver only, or this supposed to be the ACTUAL mailserver for [email]accounts@3bm.co.za[/email], etc etc)

---

### Post by DarkRanger on 2010-03-24
> **jrssystemsnet said:**
> To advise you any further than that, I'd need more information about what your situation is and what you're actually trying to achieve. (is this a local mailserver only, or this supposed to be the ACTUAL mailserver for [email]accounts@3bm.co.za[/email], etc etc)

Well, situation is this: I'm writing an intraweb for the company. I have forms on the intraweb and these forms, upon submittal, get mailed to a certain @3bm.co.za adress. The @3bm.co.za adresses already exist, mine is alberts at that adress. The 3bm server is our Microsoft Exchange Server 2003.  That is the 196.192.0.10 address server in previous replies.

I'm not sure what else you need to know. But if you ask, I'll be more specific. I'm leaving office now, so I'll reply sometime by Friday (not coming in tomorrow as I am writing some tests, still a student).

Thanks for your help so far guys. This is by far the most help I've gotten regarding this. :D

---

### Post by KB1JWQ on 2010-03-24
In this situation I'd set the server to listen only on localhost, define a relayhost of your exchange server via

relayhost = [your.exchange.server]

restart postfix, and call it a day.

---

### Post by jrssystemsnet on 2010-03-24
> **KB1JWQ said:**
> In this situation I'd set the server to listen only on localhost, define a relayhost of your exchange server via

```
relayhost = [your.exchange.server]
```

restart postfix, and call it a day.This.

---

### Post by DarkRanger on 2010-03-24
so I just need to add that line of code in my postfix config file? And change your.exchange.server to mail.3bm.co.za (seeing as this is our exchange server). Or should it be mail.3bm.local?

---

### Post by jrssystemsnet on 2010-03-24
mail.3bm.local, assuming that is a working intranet DNS record that the machine will be able to resolve to the inside address of your Exchange server.

---

### Post by KB1JWQ on 2010-03-24
But if it doesn't, don't sweat it-- just TEST FIRST.

---

### Post by DarkRanger on 2010-03-25
> **jrssystemsnet said:**
> mail.3bm.local, assuming that is a working intranet DNS record that the machine will be able to resolve to the inside address of your Exchange server.

It doesn't work. I get an error:

```
Error while checking current Postfix configuration. Please manually fix Postfix configuration.

postfix: fatal: myhostname and relayhost parameter settings must not be identical: mail.3bm.local
```

---

### Post by jrssystemsnet on 2010-03-25
Exactly what it says on the tin.  Rename this machine, it shouldn't be "mail.3bm.local", you already have one of those.

---

### Post by DarkRanger on 2010-03-29
Sorry, I think you misunderstand, or I just left out one small detail when I told you about the error ;)

I can't even save the config file now. Because I get this error in Webmin after I do the change you suggested and then try to save it. This is the config file I try to save that gives me the error.

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

relayhost = mail.3bm.local
myhostname = mail.3bm.local
alias_maps = $alias_database
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
# inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
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

---

### Post by DarkRanger on 2010-03-29
Okay, so I reinstalled ubuntu server with a guide I got off the net. This guide covered everything from setting up LDAP to Postfix. Although neither works yet, it has given me other ways of doing stuff and Postfix doesn't give error anymore. The new name for the server is ubuntu, and the ip now ends in .85, as uposed to web and .215 respectively.

The new postfix config file looks like this:

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 3bm.co.za, ubuntu, localhost.localdomain, localhost, 3bm.local
relayhost = mail.3bm.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 3bm.local
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_security_options = noanonymous
mydomain = 3bm.local
```

The problem I am experiencing now though is that it sends mails from the www-data mailbox. When I send a mail using my intraweb form, it says in the log file mail has been delivered. Although it never arrives at the intended recipient. So I went into the mailbox for www-data and found a message stating that the recipient could not be found.

The intended recipient is michaell and this is the message it sends back (for security reasons, I've changed the @-symbol to (at), so it doesn't get picked up by spam bots)

> Mail headers	View all headers | View raw message
From 	MAILER-DAEMON(at)3bm.co.za (Mail Delivery System)
To 	www-data(at)3bm.co.za
Date 	29/03/2010 16:37
Subject 	Undelivered Mail Returned to Sender
Message contents	

This is the mail system at host ubuntu.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<michaell(at)3bm.co.za>: unknown user: "michaell"


Any help regarding this?

---

### Post by DarkRanger on 2010-03-31
BUMP...

Any help??

---

### Post by jrssystemsnet on 2010-03-31
You're going to have to give us more of a picture of how the mail for 3bm.co.za is SUPPOSED to work before anybody can help.

1. what machine is SUPPOSED to handle that mail?  Where is it?  Is it the Exchange machine?

2. when you issue **dig MX 3bm.co.za** from the shell on your Postfix server, what is the output?

---

### Post by DarkRanger on 2010-04-01
> **jrssystemsnet said:**
> You're going to have to give us more of a picture of how the mail for 3bm.co.za is SUPPOSED to work before anybody can help.

1. what machine is SUPPOSED to handle that mail?  Where is it?  Is it the Exchange machine?

2. when you issue **dig MX 3bm.co.za** from the shell on your Postfix server, what is the output?

1. The server that is supposed to handle the mail is mail.3bm.co.za which is our exchange server that is here in our office (Microsoft Server 2003 Machine). Postfix is loaded on the intraweb server which is a seperate machine with a different ID that's running ubuntu server 9.10.

2. Output of that command:

```
; <<>> DiG 9.6.1-P2 <<>> MX 3bm.co.za
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18961
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;3bm.co.za.			IN	MX

;; AUTHORITY SECTION:
3bm.co.za.		3600	IN	SOA	3bmserver.3bm.local. hostmaster.3bm.local. 4 900 600 86400 3600

;; Query time: 14 msec
;; SERVER: 196.192.0.10#53(196.192.0.10)
;; WHEN: Thu Apr  1 12:50:10 2010
;; MSG SIZE  rcvd: 93

```

---

### Post by KB1JWQ on 2010-04-01
There's no MX for that box. Have you build a transport map that drops all mail there?

---

### Post by jrssystemsnet on 2010-04-01
> **KB1JWQ said:**
> There's no MX for that box. Have you build a transport map that drops all mail there?Careful, don't get sidetracked.  We've already been down this road with this guy: this Postfix server isn't SUPPOSED to catch any mail; he has an Exchange server already set up that is the proper MX for the domain.  The problem is he keeps screwing around with hostnames and DNS such that the poor Postfix box either thinks it's the MX for that domain, or else just plain doesn't know ANYTHING about the domain.

---

### Post by KB1JWQ on 2010-04-01
So all he needs to do is define a relayhost and be done with it?  Wasn't this mentioned ages ago?

---

### Post by jrssystemsnet on 2010-04-01
> **KB1JWQ said:**
> So all he needs to do is define a relayhost and be done with it?  Wasn't this mentioned ages ago?Yep.  Well, that and make sure that the Postfix box DOESN'T think it's the MX for 3bm.co.za, due mostly to hostnaming issues.

---

### Post by KB1JWQ on 2010-04-01
Fair enough.

DarkRanger: Are you clear on what you have to do?

---

### Post by DarkRanger on 2010-04-06
> **KB1JWQ said:**
> So all he needs to do is define a relayhost and be done with it?  Wasn't this mentioned ages ago?

Done that.

Here is my config file:

```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# Intraweb Host (This Machine)
myhostname = ubuntu.3bm.local
# Email Host (Exchange Server)
relayhost = mail.3bm.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, $mydomain, 3bm.co.za, ubuntu, localhost.localdomain, localhost, 3bm.local
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 3bm.local
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_security_options = noanonymous
mydomain = 3bm.local
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
```

---

### Post by DarkRanger on 2010-04-06
> **jrssystemsnet said:**
> Yep.  Well, that and make sure that the **Postfix box DOESN'T think it's the MX for 3bm.co.za**, due mostly to hostnaming issues.

How do I do that?

---

### Post by DarkRanger on 2010-04-08
Bump

---

### Post by DarkRanger on 2010-04-11
bump

---

### Post by DarkRanger on 2010-04-19
Still waiting for someone to point me in the right direction here

---

