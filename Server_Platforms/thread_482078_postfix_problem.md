---
title: "postfix problem"
date: 2007-06-23
forum: Server Platforms
---

### Post by phar0z on 2007-06-23
I'm experiencing a little problem while setting up Postfix.

First of all my ISP blocks port 25, so I changed the port to 5025. Ofcourse I've opened 5025 on my NAT.

The first uncommented line in my master.cf file is :
5025      inet  n       -       -       -       -       smtpd

My main.cf file looks like this:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
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

myhostname = amdstation.phar0zlinux.net
mydomain = phar0zlinux.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = phar0zlinux.net, localhost, localhost.phar0zlinux.net, localhost
relayhost = uit.telenet.be
mynetworks = 127.0.0.0/8, 192.168.0.104
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = $mydomain
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
home_mailbox = Maildir/
mailbox_command = procmail -a "$EXTENSION"
local_recipients_maps = $alias_maps
sender_canonical = hash:/etc/postfix/sender_canonical
recipient_canonical_maps = hash:/etc/postfix/recipient_canonical

Notice here that I used local_recipients_maps = in the past which fixed the Relay acces denied error, but not now.

And my /etc/aliases file:

# Added by installer for initial user
mansondude: pieterjan

I have both users pieterjan and mansondude on my server as UNIX users.

So When I try to send an e-mail the next thing is happening:

12 root@ubuntux $ telnet 213.118.217.78 5025
Trying 213.118.217.78...
Connected to 213.118.217.78.
Escape character is '^]'.
220 amdstation.phar0zlinux.net ESMTP Postfix (Ubuntu)
ehlo ubuntux
250-amdstation.phar0zlinux.net
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: ***@gmail.com
250 2.1.0 Ok
rcpt to: ***@gmail.com
554 5.7.1 <***@gmail.com>: Relay access denied

(Ofcourse I replaced the real addresses by *** here, I don't want more spam)

And when I'm doing tail -f /var/log/mail.log on the server I receive:

Jun 23 14:26:45 amdstation postfix/smtpd[5943]: connect from dD576D94E.access.telenet.be[213.118.217.78]
Jun 23 14:26:56 amdstation postfix/smtpd[5943]: NOQUEUE: reject: RCPT from dD576D94E.access.telenet.be[213.118.217.78]: 554 5.7.1 <***@gmail.com>: Relay access denied; from=<***@gmail.com> to=***@gmail.com> proto=ESMTP helo=<ubuntux>
Jun 23 14:31:56 amdstation postfix/smtpd[5943]: timeout after RCPT from dD576D94E.access.telenet.be[213.118.217.78]   

How can I fix this problem? Thanks

---

### Post by Mr. C. on 2007-06-23
Postfix refuses to deliver or relay mail for which it is not configured.

You are trying to send mail to a recipient at gmail.com, but your server is not gmail.com, nor configured to be final destination or transport for gmail.com.

Do you want your email to remain local on your server, or do you want it forwarded to gmail ?

MrC

---

### Post by phar0z on 2007-06-24
I want it forwarded to gmail, shall I a make .forward file in my /home/$USER?

I know the mydestination variable is right, because the mydestination is only used for local transport.

So to make it clear, I just want my system is capable to send emails throughout my server to gmail.com users without the Relay access denied error. :)

In the past I saw this error before and I fixed it then with inserting local_recipients_map = in main.cf

---

### Post by phar0z on 2007-06-24
Finally I've found out the solution for my relay acces denied error :D

First I've had this in my main.cf file:

mynetworks = 127.0.0.0/8, 192.168.0.104

Notice here I only wrote  my local IP address, so after when I have added my WAN IP address it  works.

So to avoid any mistakes, here is the mynetworks line now:

mynetworks = 127.0.0.0/8, 192.168.0.104, 213.118.217.78

---

### Post by Mr. C. on 2007-06-24
I see that you have your problem cleared up.

A .forward file is only used by the local transport and only *after* email has been accepted for a *local* user.

Your postfix machine appears to have a WAN IP address, so it would need that WAN IP in mynetworks, as you've discovered.

MrC

---

### Post by phar0z on 2007-06-24
Thank you for the information concerning a .forward file ;)

---

