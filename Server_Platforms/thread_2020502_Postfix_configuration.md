---
title: "Postfix configuration"
date: 2012-07-08
forum: Server Platforms
---

### Post by BalleClorin on 2012-07-08
Hello!
My company is running an Exchange server which I don't dare to put on the net, so instead I have two Ubuntu servers running on separate locations acting as the domains primary and secondary MX hosts. This setup has worked just fine for a long time, but recently I've been having trouble with what looks like spam-messages sent from internal users. My users keeps complaining that they recieve spam rejection messages. It seems like strangers are allowed to send to external addresses as long as the from address is local. In the pasted logs and settings, the companyname has been changes to mydomain, and mydomainsbs.maydomain.local (10.220.10.4) is the exchange server. linuxserver.mydomain.local (10.220.10.104) is the primary MX recieving all communication to port 25 on remote.mydomain.no (the primary MX host for mydomain.no). Here is an example from the logs:
 
Jul 4 13:01:47 linuxserver postfix/smtpd[23898]: 310AB411: client=unknown[113.165.62.100]
Jul 4 13:01:48 linuxserver postfix/cleanup[23904]: 310AB411: message-id=<>
Jul 4 13:01:48 linuxserver postfix/qmgr[815]: 310AB411: from=<[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>, size=1241, nrcpt=1 (queue active)
Jul 4 13:01:48 linuxserver postfix/smtpd[23898]: disconnect from unknown[113.165.62.100]
Jul 4 13:01:51 linuxserver postfix/smtp[23902]: C44D279C: to=<[EMAIL="bounces@tellinweb.info"]bounces@tellinweb.info[/EMAIL]>, relay=10.220.10.4[10.220.10.4]:25, delay=5.2, delays=0.08/0/0/5.1, dsn=5.7.1, status=bounced (host 10.220.10.4[10.220.10.4] said: 550 5.7.1 Unable to relay (in reply to RCPT TO command))
Jul 4 13:01:58 linuxserver postfix/smtp[23905]: 310AB411: to=<[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>, relay=mydomainsbs.mydomain.local[10.220.10.4]:25, delay=12, delays=1.6/0/5/5.1, dsn=5.7.1, status=bounced (host mydomainsbs.mydomain.local[10.220.10.4] said: 550 5.7.1 Message rejected as spam by Content Filtering. (in reply to end of DATA command))
Jul 4 13:01:58 linuxserver postfix/cleanup[23901]: 8E65CE33: message-id=<[EMAIL="20120704110158.8E65CE33@linuxserver.mydomain.local"]20120704110158.8E65CE33@linuxserver.mydomain.local[/EMAIL]>
Jul 4 13:01:58 linuxserver postfix/qmgr[815]: 8E65CE33: from=<>, size=3222, nrcpt=1 (queue active)
Jul 4 13:01:58 linuxserver postfix/bounce[23907]: 310AB411: sender non-delivery notification: 8E65CE33
Jul 4 13:01:58 linuxserver postfix/qmgr[815]: 310AB411: removed
Jul 4 13:01:58 linuxserver postfix/smtp[23905]: 8E65CE33: to=<[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>, relay=mydomainsbs.mydomain.local[10.220.10.4]:25, delay=0.34, delays=0.09/0/0/0.24, dsn=2.6.0, status=sent (250 2.6.0 <[EMAIL="20120704110158.8E65CE33@linuxserver.mydomain.local"]20120704110158.8E65CE33@linuxserver.mydomain.local[/EMAIL]> Queued mail for delivery)
Jul 4 13:01:58 linuxserver postfix/qmgr[815]: 8E65CE33: removed
Jul 4 13:02:01 linuxserver postfix/qmgr[815]: C44D279C: removed
 
This makes the local user recieve a bounce message:
Genererende server: linuxserver.mydomain.local
 
[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]
mydomainsbs.mydomain.local #<mydomainsbs.mydomain.local #5.7.1 smtp; 550 5.7.1 Message rejected as spam by Content Filtering.> #SMTP#
 
Opprinnelige meldingshoder:
 
Return-Path: <[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>
Received: from localhost (unknown [113.165.62.100]) by linuxserver.mydomain.local
(Postfix) with SMTP id 310AB411 for <[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>; Wed, 4 Jul 2012
13:01:46 +0200 (CEST)
From: <[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>
To: <[EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL]>
Subject: [EMAIL="haakon@mydomain.no"]haakon@mydomain.no[/EMAIL] Breitling Discount ID40463734
MIME-Version: 1.0
Content-Type: text/html; charset="ISO-8859-1"
Content-Transfer-Encoding: 7bit
 
Bacause of Outlook beeng such a lame email client some of the info above is in Norwegian, hopefully you'll understand.
 
So my question is: How do I make postfix reject all external mail that does not have a local address in TO, and if necessary reject all incomming mails that has a local address in FROM (postfix is only used for recieving mail and forwarding to exchange, not for sending mail from local users).
 
/etc/postfix/main.cf:
 
myorigin = /etc/mailname
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
myhostname = linuxserver.mydomain.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = mydomain.no, linuxserver.mydomain.local, localhost.mydomain.local, localhost
relay_domains = mydomain.no, remote.mydomain.no
relayhost = 10.220.10.4
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.220.10.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 10.220.10.104 127.0.0.1
virtual_alias_maps = hash:/etc/postfix/virtual
parent_domain_matches_subdomains = debug_peer_list smtpd_access_maps
smtpd_recipient_restrictions =
reject_unauth_destination
reject_rbl_client sbl-xbl.spamhaus.org
permit_mynetworks
relay_recipient_maps = hash:/etc/postfix/relay_recipients
transport_maps = hash:/etc/postfix/transport
 
 
Regards
Andreas Noteng

---

### Post by SeijiSensei on 2012-07-08
> **BalleClorin said:**
> My users keeps complaining that they recieve spam rejection messages. It seems like strangers are allowed to send to external addresses as long as the from address is local.

This is a very common spamming technique where messages are sent with From addresses within the target's domain.  Often, as in the case you show, the From and To addresses will be identical.

I use sendmail and block such messages in its [/etc/mail/access]("http://www.sendmail.com/sm/open_source/docs/m4/anti_spam.html") database.  For Postfix, it looks like you should read [this](http://www.postfix.org/SMTPD_ACCESS_README.html).

On my own public server, I use the hoary "Obtuse smtpd" store-and-forward SMTP daemon which has a simple but powerful rules-based method for controlling access.  The smtpd daemon does nothing but accept inbound mail and forwards it on to another server for processing if the SMTP envelope information meets the rules.  With smtpd, I can write a rule like this:

```
deny:ALL:ALL@mydomain.name:ALL
```

and any inbound mail claiming to be sent from my domain is blocked at the doorstep.  The second field can include SMTP server information; the fourth field matches the To address.

I build my implementations from source, but there was a .deb for [hardy](https://launchpad.net/ubuntu/hardy/i386/smtpd/2.0-8.1).  A link to the source .deb and the source code can be found there as well.

Where do you scan inbound mail for spam and viruses now?  I use the excellent [MailScanner]("http://www.mailscanner.info/") on a Linux box to scan all mail.  The server running smtpd forwards all mail to the box running MailScanner; only clean messages get forwarded along to the mail server with the users' accounts, in your case Exchange.

---

### Post by BalleClorin on 2012-07-15
Hello, and thanks for your reply. I was kind of expecting an email if someone replied, so I didn't check back until now..

Your solution seems like a good one, but right now I'd rather make the Postfix setup work, as I don't have time right now to fix things if I mess up. I'll give it a go in a VM this fall, when I no longer work three jobs simultaneously. Right now Exchange takes care of spam, and AVG handles virus control. It seems to work very well, but of course a setup where malicious emails never reach the vulnerable Windows boxes would be preferred.

Anyone know how to block messages from *@mydomain.com but accept messages to *@mydomain.com in Postfix?

---

### Post by SeijiSensei on 2012-07-15
Maybe you missed the link to the Postfix document in my earlier post?   [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

### Post by BalleClorin on 2012-07-16
Looks like I did...

Fixed it now. In case anyone else wonders; this is what I did:

Create /etc/postfix/sender_access:

```
mydomain.no REJECT
``````

sudo postmap hash:/etc/postfix/sender_access
```edit /etc/postfix/main.cf and add the following:

```
smtpd_sender_restrictions =
        check_sender_access hash:/etc/postfix/sender_access
```For some additional spam rejection I also added the following:

to smtpd_recipient_restrictions:
```
        reject_unknown_helo_hostname
```to smtpd_client_restrictions:
```
        reject_unknown_client_hostname
```

---

