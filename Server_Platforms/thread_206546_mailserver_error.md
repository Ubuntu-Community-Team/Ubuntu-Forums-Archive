---
title: "mailserver error"
date: 2006-06-30
forum: Server Platforms
---

### Post by renaissance on 2006-06-30
Hi !

 Few days ago, i was write trobles with my mailserver. Well, if i try to sent e-mail outside to my localnetwork i see error message: 
Transaction failed
Server replied: 554 <renee@mail.ee>: Relay access denied ?
Have anybody ideas how to fix it ?
I use Postfix MTA and Dovecot.

My /etc/postfix/main.cf looks inside:


# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = server.vkk.vil.ee
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = vkk.vil.ee, server.vkk.vil.ee, localhost.vkk.vil.ee, localhost
relayhost =
mynetworks = 193.40.120.192/27
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
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

---

### Post by Randomskk on 2006-06-30
This is most likely a problem more related to the other server - they have not allowed you to send a message through to them, for whatever reason.
Common reasons include not allowing IPs that to not have a valid reverse DNS (all the optonline, roadrunner etc people do this), having a black-listed IP (it's on a spam list someplace) or they simply do not allow it for whatever reason.
Try sending the email to someone else, for instance gmail are fairly good.

---

### Post by MJN on 2006-07-01
Can you give an example of what address you're trying to reach? (just the domain if you like)

---

### Post by herald on 2006-07-01
[QUOTE=renaissance]Hi !

 Few days ago, i was write trobles with my mailserver. Well, if i try to sent e-mail outside to my localnetwork i see error message: 
Transaction failed
Server replied: 554 <renee@mail.ee>: Relay access denied ?

My /etc/postfix/main.cf looks inside:

[...]
myhostname = server.vkk.vil.ee
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = vkk.vil.ee, server.vkk.vil.ee, localhost.vkk.vil.ee, localhost
relayhost =
mynetworks = 193.40.120.192/27
[...]
[/QUOTE]

You need to do a few things here.  Make sure that the name in /etc/mailname is just the domain part of the server's hostname.  IE if it's vkk.vil.ee, then just put vil.ee in the /etc/mailname.

Second, in your mydestination, only put the domain part of the "real" domains that the server will accept mail for.  Basically, it thinks that the vkk.vil.ee and server.vkk.vil.ee are actual domains that it should listen to.  When it sees something bound for vkk.vil.ee, it is expecting a DOMAIN, not a FQDN for a host.

The mynetworks (in my humble opinion) should also contain 127.0.0.1 for local looping, but that's not a show stopper.

I just un/reinstalled 3 different mail servers, 2 different pop/imap servers, and reinstalled the entire OS on my server 4 times because of this nasty little thing.  None of the config HOWTO's given by Ubuntu make this known, nor did any of the other HOWTO's I found.  Granted, it's a huge task writing a howto for someting like a mail server, because it can be configured in countless ways, but I really wish I didn't have to spend a week to figure this out.

At any rate, this should get you up and running\\:D/

---

### Post by MJN on 2006-07-02
Postfix pretty works fine at a basic level straight out of the box, and the Postfix docs (particularly [http://www.postfix.org/postconf.5.html]("http://www.postfix.org/postconf.5.html")) give you more info than you'd ever need to configure it properly.
 
I would suggest starting with the default config and reading the man pages for each directive therein - you'll then understand exactly what each directive does and how it should be configured. Then build upon this foundation adding the additional functionality (e.g. client authentication, backup MTA etc) as required. To try and do everything in one go, if the only tool in your arsenal is a scattergun, is doomed to failure at best and a compromised MTA at worst.
 
Mathew

---

