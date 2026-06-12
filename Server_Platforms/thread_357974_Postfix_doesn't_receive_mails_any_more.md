---
title: "Postfix doesn't receive mails any more"
date: 2007-02-10
forum: Server Platforms
---

### Post by farao on 2007-02-10
Hi All,

On feb 3 my Ubuntu 6.06 LTS server stopped delivering inbound mail to my users. The mail gets in, but it won't show up in my mailboxes (I use the ISPConfig hosting panel).
Outbound mail works, but inbound won't budge.
If i do a lookup on my dns-records, I get the external IP returned. Firefox uses the hosts-file to display pages drom the internal server, but somwhow Postfix immediately looks outside my network.
I also posted this on the ispconfig forum, but no luck so far.
On feb3 I did an apt-upgrade, but no dns-stuff came in then. Please help, I'm at a loss.

---

### Post by gombadi on 2007-02-10
Are you able to provide some more information.

>The mail gets in, but it won't show up in my mailboxes

How do you know the mail gets in?
Won't show up in my mailboxes - Where is it sitting?

Can you let us know of any errors in /var/log/syslog that may be relevant.

---

### Post by farao on 2007-02-10
Hi, when sending mail, it simply arrives at its destination.
When sending mail within the server (which hosts multiple domains), mail simply goes nowhere.
Mail sent to the domain from outside my LAN gets bounced with an error 554, too many hops, and this error comes from the backup mailserver.
errorlogs say nothing:
```

Feb 10 20:22:04 atlas postfix/smtp[19980]: connect to manaxa.com[194.109.228.119]: Connection timed out (port 25)
Feb 10 20:22:05 atlas postfix/smtp[19980]: C3B301D4194: to=<mnx_ikke@atlas.manaxa.com>, orig_to=<ikke@manaxa.com>, relay=relay.transip.nl[80.69.67.19], delay=31, status=sent (250 Ok: queued as 39B973C1CC0)
Feb 10 20:22:05 atlas postfix/qmgr[6172]: C3B301D4194: removed
Feb 10 20:22:05 atlas postfix/smtpd[19856]: connect from relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:05 atlas postfix/smtpd[19856]: 6022C1D4194: client=relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:05 atlas postfix/cleanup[19866]: 6022C1D4194: message-id=<45CE1B3E.5070908@stecher.org>
Feb 10 20:22:05 atlas postfix/qmgr[6172]: 6022C1D4194: from=<mendel@stecher.org>, size=4071, nrcpt=1 (queue active)
Feb 10 20:22:05 atlas postfix/smtpd[19856]: disconnect from relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:22 atlas postfix/smtp[19869]: connect to manaxa.com[194.109.228.119]: Connection timed out (port 25)
Feb 10 20:22:23 atlas postfix/smtp[19869]: 69C5B1D4193: to=<info_imok@atlas.manaxa.com>, relay=relay.transip.nl[80.69.67.19], delay=31, status=sent (250 Ok: queued as A45D43C1257)
Feb 10 20:22:23 atlas postfix/qmgr[6172]: 69C5B1D4193: removed
Feb 10 20:22:23 atlas postfix/smtpd[19856]: connect from relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:23 atlas postfix/smtpd[19856]: 34AC41D4193: client=relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:23 atlas postfix/cleanup[19866]: 34AC41D4193: message-id=<001201c74d48$461d2e10$00000000@pc3ecb3c468a1b>
Feb 10 20:22:23 atlas postfix/qmgr[6172]: 34AC41D4193: from=<disaster@ebninc.com>, size=16064, nrcpt=1 (queue active)
Feb 10 20:22:23 atlas postfix/smtpd[19856]: disconnect from relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:23 atlas postfix/smtp[19869]: 34AC41D4193: to=<info_imok@atlas.manaxa.com>, relay=relay.transip.nl[80.69.67.19], delay=0, status=sent (250 Ok: queued as 428AE3C18BB)
Feb 10 20:22:23 atlas postfix/qmgr[6172]: 34AC41D4193: removed
Feb 10 20:22:23 atlas postfix/smtpd[19856]: connect from relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:23 atlas postfix/smtpd[19856]: A07C01D4193: client=relayout1.transip.nl[80.69.67.35]
Feb 10 20:22:23 atlas postfix/cleanup[19866]: A07C01D4193: message-id=<001201c74d48$461d2e10$00000000@pc3ecb3c468a1b>
Feb 10 20:22:23 atlas postfix/qmgr[6172]: A07C01D4193: from=<disaster@ebninc.com>, size=16687, nrcpt=1 (queue active)
Feb 10 20:22:23 atlas postfix/smtpd[19856]: disconnect from relayout1.transip.nl[80.69.67.35]
```

this is from the mail.warn log:
```
Feb 10 04:34:17 atlas postfix/smtpd[3231]: warning: 203.187.206.34: hostname 34-206-187-203.static.youtele.com verification failed: Name or service not known
Feb 10 10:41:18 atlas postfix/smtpd[22689]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 11:52:51 atlas imaplogin: DISCONNECTED, ip=[::ffff:62.244.183.178], time=0
Feb 10 16:20:40 atlas postfix/smtpd[7920]: warning: 203.236.248.79: hostname 203-236-248-79.rev.nextel.co.kr verification failed: Name or service not known
Feb 10 16:33:13 atlas postfix/smtpd[8509]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 16:37:18 atlas postfix/smtpd[8441]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 16:37:30 atlas postfix/smtpd[8457]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 16:45:51 atlas imaplogin: DISCONNECTED, user=mnx_ikke, ip=[::ffff:10.0.0.33], headers=0, body=0, time=68705
Feb 10 16:45:52 atlas imaplogin: DISCONNECTED, user=mnx_ikke, ip=[::ffff:10.0.0.33], headers=0, body=0, time=756
Feb 10 16:45:52 atlas imaplogin: DISCONNECTED, user=sto_mendel, ip=[::ffff:10.0.0.33], headers=0, body=0, time=68413, starttls=1
Feb 10 16:45:52 atlas imaplogin: DISCONNECTED, user=sto_mendel, ip=[::ffff:10.0.0.33], headers=0, body=0, time=68711, starttls=1
Feb 10 16:58:04 atlas postfix/qmgr[6172]: warning: premature end-of-input on private/rewrite socket while reading input attribute name
Feb 10 16:58:04 atlas postfix/qmgr[6172]: warning: problem talking to service rewrite: Connection reset by peer
Feb 10 17:02:24 atlas postfix/smtpd[9063]: warning: premature end-of-input on private/rewrite socket while reading input attribute name
Feb 10 17:02:24 atlas postfix/smtpd[9063]: warning: problem talking to service rewrite: Connection reset by peer
Feb 10 17:02:26 atlas postfix/qmgr[6172]: warning: premature end-of-input on private/rewrite socket while reading input attribute name
Feb 10 17:02:26 atlas postfix/qmgr[6172]: warning: problem talking to service rewrite: Connection reset by peer
Feb 10 17:22:41 atlas imaplogin: DISCONNECTED, user=mnx_ikke, ip=[::ffff:10.0.0.59], headers=0, body=0, time=1800, starttls=1
Feb 10 17:42:04 atlas postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)
Feb 10 17:42:18 atlas postfix/postfix-script: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Feb 10 17:44:33 atlas postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)
Feb 10 19:21:05 atlas imaplogin: DISCONNECTED, ip=[::ffff:216.63.195.252], time=0
Feb 10 20:08:27 atlas postfix/smtpd[19264]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 20:21:34 atlas postfix/smtpd[19856]: warning: 10.0.0.33: address not listed for hostname atlas.manaxa.com
Feb 10 20:54:12 atlas postfix/smtpd[21208]: warning: 87.3.60.107: hostname host107-60-dynamic.3-87-r.retail.telecomitalia.it verification failed: Name or service not known
Feb 10 22:36:08 atlas postfix/smtpd[26592]: warning: 200.90.192.124: hostname 90-192-124.adsl.cust.tie.cl verification failed: Name or service not known
```
it's the 10.0.0.33 warnings that have me baffled: it almost seems like my server is looking up its hosts from outside DNS, instead of the hosts file.
If you want, I can post main.cf, master.cf and more log-stuff?

---

### Post by gombadi on 2007-02-10
Are you sure you are not able to receive email from outside your LAN?

```

lroger@bt:~$ swaks -t hidden@manaxa.com -f hidden@pobox.com
=== Trying manaxa.com:25...
=== Connected to manaxa.com.
<-  220 atlas.manaxa.com ESMTP Postfix (Ubuntu)
 -> EHLO bt.gombadi.com
<-  250-atlas.manaxa.com
<-  250-PIPELINING
<-  250-SIZE 10240000
<-  250-VRFY
<-  250-ETRN
<-  250-STARTTLS
<-  250-AUTH LOGIN PLAIN
<-  250-AUTH=LOGIN PLAIN
<-  250 8BITMIME
 -> MAIL FROM:<hidden@pobox.com>
<-  250 Ok
 -> RCPT TO:<hidden@manaxa.com>
<-  250 Ok
 -> DATA
<-  354 End data with <CR><LF>.<CR><LF>
 -> Date: Sun, 11 Feb 2007 09:04:02 +1100
 -> To: hidden@manaxa.com
 -> From: hidden@pobox.com
 -> Subject: test Sun, 11 Feb 2007 09:04:02 +1100
 -> X-Mailer: swaks v20050625.8 jetmore.org/john/code/#swaks
 -> 
 -> This is a test mailing
 -> 
 -> .
<-  250 Ok: queued as 91E641D4194
 -> QUIT
<-  221 Bye
=== Connection closed by foreign host.

```

---

### Post by gombadi on 2007-02-10
Just another thing -

>Feb 10 20:22:04 atlas postfix/smtp[19980]: connect to manaxa.com[194.109.228.119]: Connection timed out (port 25)

The server atlas seems to be trying to connect to manaxa.com on 194.109.228.119
According to the connection I made atlas is at 194.109.228.119 so it is trying to connect to itself by its external ip address. Is atlas behind an adsl router?

If so then it may not be able to connect to itself and it will give the above connection timed out message and then pass the message to the backup email server.
The backup email server is able to connect to atlas so passes the message bact to atlas who then tries to connect to itself and fails so passes back to the backup email server ... and off around the loop again.

---

### Post by farao on 2007-02-11
that's just it: How do I break the loop?!
I know it connects correctly, the mail just doesn't show up in my mailbox.
If I telnet to my server, everything responds as expected. dnsreport says everything is in order, and the mailcheck gives me no clues either.
The server is behind a router, with a NAT-table that says everything on port25 should be forwarded to the server. The fact that you could connect to it, proves it works, it must be something with the lookups on the server itself, but what?

---

### Post by gombadi on 2007-02-11
What is the mydestination line in /etc/postfix/main.cf

That controls what domains the machine thinks it is the destination for and therefore will not try and forward email to.
Your at least should have atlas.manaxa.com and manaxa.com

---

### Post by fcosentino on 2007-02-11
Don't know if it is related, but after the latest updates my Sambar Pro 6.4 server stopped working for SMTP on port 25 as well.

I can't send and receive eMails. Transaction starts but then it stops and times out.

Using same version on Windows XP works fine.

---

### Post by farao on 2007-02-11
Main.cf:
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = atlas.manaxa.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = atlas.manaxa.com, localhost.manaxa.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
#home_mailbox = Maildir/
#mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
#inet_protocols = all
inet_protocols = ipv4
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,check_policy_service inet:127.0.0.1:60000
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1
local_recipient_maps = 
#relay_domains = $mydestination
inet_interfaces = all

```

And the /etc/postfix/local-host-names contains the domains manaxa.com, atlas.manaxa.com, [www.manaxa.com](www.manaxa.com), ftp etcetera, they're all there.

---

### Post by farao on 2007-02-13
Solved:
By adding the parameter
```
smtp_host_lookup = native,dns
```
to my main.cf, it works again. Now if only I understood why I need this parameter all of a sudden... but I'm not complaining.

---

