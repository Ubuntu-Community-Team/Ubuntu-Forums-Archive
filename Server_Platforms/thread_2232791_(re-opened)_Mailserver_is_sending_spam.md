---
title: "(re-opened) Mailserver is sending spam"
date: 2014-07-04
forum: Server Platforms
---

### Post by Jesse Degger on 2014-07-04
Hi everybody,

I hope I posted this in the right section, my apologies if I didn't.

Since a few weeks my mailserver seems to be sending out spam and I can't figure out how they're able to do that.

Could some of you help me on my journey to find out what's going on? 

I am willing to share configuration and logs files. My current mail queue: [http://pastebin.com/SpuRwsa2](http://pastebin.com/SpuRwsa2)

With kind regards,

Jesse

---

### Post by lisati on 2014-07-04
Your email server might be acting as an open relay. Ideally it should only accept incoming mail from the outside world for domains it handles.

---

### Post by volkswagner on 2014-07-04
Try [MxToolbox.com's test]("http://mxtoolbox.com/diagnostic.aspx").  It will run several test, one of which checks for open relay.

---

### Post by Jesse Degger on 2014-07-04
Thanks for the quick responses, there doesn't seem to be a problem with open relaying:

[IMG]http://updo.nl/file/457e3602.png[/IMG]

(Offtopic question: are those connection times not very slow?)

Any other possibilities?

------

Addition: found this outgoing mail:

[FONT=lucida console][FONT=courier new]Return-Path: <info@obfustcated.nl>
Received: from localhost (unknown [62.80.161.250])
    by freenet9 (Postfix) with ESMTPA id ADD974D0A77
    for <tonia-fenderico@live.it>; Thu,  3 Jul 2014 10:47:04 -0400 (EDT)
Message-ID: <887234C00BDFF112CECB823FBB584A47@uqez>
Reply-To: "Honey" <r@69revoluciones.com>
From: "Honey" <info@obfustcated.nl>
To: "Celeste" <tonia-fenderico@live.it>
Subject: Sono molto solitaria!
Date: Thu, 3 Jul 2014 15:46:34 +0100
MIME-Version: 1.0
Content-Type: multipart/mixed;
    boundary="----=_NextPart_000_162F_01CF96D5.F7B812F0"
X-Priority: 3
X-MSMail-Priority: Normal
X-Mailer: Microsoft Windows Live Mail 15.4.3538.513
X-MimeOLE: Produced By Microsoft MimeOLE V15.4.3538.513[/FONT]

[/FONT]
[FONT=arial]info@obfustcated.nl is one of my own addresses. Another:

[FONT=courier new]eturn-Path: <info@obfustcated.nl>
Received: (qmail 26724 invoked by uid 64020); 3 Jul 2014 19:38:38 +0200
Received: from unknown (HELO localhost) (recepce@hoteleuropa.cz@37.143.14.167)
  by vs691.server4u.cz with ESMTPA; 3 Jul 2014 17:38:34 -0000
Message-ID: <41BBF78EB6624CAF73763F82F6E27E35@mrhn>
Reply-To: "Honey" <qehlpfef@gruszynskiforassembly.com>
From: "Honey" <info@obfustcated.nl>
To: <cfonsati@email.it>
Subject: tu sei quello che stavo cercando!
Date: Thu, 3 Jul 2014 18:38:34 +0100
MIME-Version: 1.0
Content-Type: multipart/mixed;
    boundary="----=_NextPart_000_0904_01CF96ED.FEA622B0"
X-Priority: 3
X-MSMail-Priority: Normal
X-Mailer: Microsoft Windows Live Mail 16.4.3528.331
X-MimeOLE: Produced By Microsoft MimeOLE V16.4.3528.331

[/FONT]Something else: I saw this:

[FONT=courier new]Jul  4 14:15:14 obfustcated postfix/anvil[28380]: statistics: max connection rate 2/60s for (smtp:81.91.85.191) at Jul  4 14:08:50
Jul  4 14:15:14 obfustcated postfix/anvil[28380]: statistics: max connection count 1 for (smtp:81.91.85.191) at Jul  4 14:08:32
Jul  4 14:15:14 obfustcated postfix/anvil[28380]: statistics: max cache size 1 at Jul  4 14:08:32
[/FONT]
Does that mean that IP is successfully connected to my SMTP server?
[/FONT]

---

### Post by SeijiSensei on 2014-07-04
Sending spam addressed from a domain you own through your server is a common trick.  Unless you have legitimate external users sending from "info@obfuscated.nl," you should block such mail using the various Postfix anti-spam methods.  One server I manage uses both the "helo_access" and "sender_access" maps for this purpose.

In main.cf I have these entries:
```

smtpd_client_restrictions = reject_unknown_client_hostname,
                            check_sender_access pcre:/etc/postfix/sender_access,
                            sleep 3, reject_unauth_pipelining

smtpd_delay_reject = no

smtpd_sender_restrictions = reject_unknown_sender_domain,
                            check_sender_access pcre:/etc/postfix/sender_access

smtpd_helo_required = yes
smtpd_helo_restrictions =   check_helo_access pcre:/etc/postfix/helo_access

# relaying
smtpd_relay_restrictions =  reject_unauth_destination

```
The files sender_access and helo_access contain rules that use "Perl-compatible regular expressions," the "pcre:" prefix shown above.  The two files serve different purposes though some of the rules are common to both.  Sender_access concerns the "From:" field in the message, while helo_access applies to the "envelope sender," the address the remote SMTP server sends when it begins the session.  That's the address that appears in the "Return-Path:" header at the top of every message.

So in your case, I'd add the check_sender_access and check_helo_access directives, and create corresponding files to block things you don't want.  For instance, both files might include:
```

/obfuscated\.nl/     REJECT

```
which blocks any external host from sending mail claiming it is from your domain.  If you have valid external users in that domain, then you probably need to be more specific:
```

/info@obfuscated\.nl/     REJECT

```
or, better,
```

/user1@obfuscated\.nl/  OK
/user2@obfuscated\.nl/  OK
/obfuscated\.nl/        REJECT

```
That accepts mail from your legitimate senders and blocks everything else.

I recommend reading the manual page "[man 5 access]("http://www.postfix.org/access.5.html")" and the other pages it references.

The "sleep 3, reject_unauth_pipelining" directives are also very useful.  They insert a three-second delay between when the remote server connects and when Postfix displays its "welcome" banner.  Spamming servers rarely wait for the banner and just start pumping their crap out as soon as they connect.  These directives reject such "unauthorized pipelining" and disconnect from any machine that fails to wait for the banner.  You should read the discussions of "reject_unknown_client_hostname" and "reject_unknown_sender_domain" as well.  Most spamming attempts against this server fail because of reject_unknown_client_hostname.  Usually these are machines that have no reverse DNS records at all.

By the way, if your server is on a legitimate business-class connection, or your ISP is indifferent to whether you can host servers, then you might want to discuss fixing your reverse DNS entry so it matches the forward entry.  Only your ISP can make that change unless, as seems unlikely, your ISP has "[delegated]("http://www.ietf.org/rfc/rfc2317.txt")" to you the ability to create PTR records for your IP subnet.

---

### Post by Jesse Degger on 2014-07-05
> **SeijiSensei said:**
> Sending spam addressed from a domain you own through your server is a common trick.  Unless you have legitimate external users sending from "info@obfuscated.nl," you should block such mail using the various Postfix anti-spam methods.  One server I manage uses both the "helo_access" and "sender_access" maps for this purpose.

In main.cf I have these entries:
```

smtpd_client_restrictions = reject_unknown_client_hostname,
                            check_sender_access pcre:/etc/postfix/sender_access,
                            sleep 3, reject_unauth_pipelining

smtpd_delay_reject = no

smtpd_sender_restrictions = reject_unknown_sender_domain,
                            check_sender_access pcre:/etc/postfix/sender_access

smtpd_helo_required = yes
smtpd_helo_restrictions =   check_helo_access pcre:/etc/postfix/helo_access

# relaying
smtpd_relay_restrictions =  reject_unauth_destination

```
The files sender_access and helo_access contain rules that use "Perl-compatible regular expressions," the "pcre:" prefix shown above.  The two files serve different purposes though some of the rules are common to both.  Sender_access concerns the "From:" field in the message, while helo_access applies to the "envelope sender," the address the remote SMTP server sends when it begins the session.  That's the address that appears in the "Return-Path:" header at the top of every message.

So in your case, I'd add the check_sender_access and check_helo_access directives, and create corresponding files to block things you don't want.  For instance, both files might include:
```

/obfuscated\.nl/     REJECT

```
which blocks any external host from sending mail claiming it is from your domain.  If you have valid external users in that domain, then you probably need to be more specific:
```

/info@obfuscated\.nl/     REJECT

```
or, better,
```

/user1@obfuscated\.nl/  OK
/user2@obfuscated\.nl/  OK
/obfuscated\.nl/        REJECT

```
That accepts mail from your legitimate senders and blocks everything else.

Thanks, this is great! I'm currently trying to install this, unfortunately I have to make some changes since I use some virtual users via a MySQL database.

My query became:

```
query = SELECT 'OK' FROM virtual_users where email='%s'
```

That seems to work :), it only gives OK when the literal address has been found in my database. I can't add the last REJECT line via MySQL but thats not required right? Since we added 'reject_unknown_sender_domain'?


> **SeijiSensei said:**
> 
I recommend reading the manual page "[man 5 access]("http://www.postfix.org/access.5.html")" and the other pages it references.

The "sleep 3, reject_unauth_pipelining" directives are also very useful.  They insert a three-second delay between when the remote server connects and when Postfix displays its "welcome" banner.  Spamming servers rarely wait for the banner and just start pumping their crap out as soon as they connect.  These directives reject such "unauthorized pipelining" and disconnect from any machine that fails to wait for the banner.  You should read the discussions of "reject_unknown_client_hostname" and "reject_unknown_sender_domain" as well.  Most spamming attempts against this server fail because of reject_unknown_client_hostname.  Usually these are machines that have no reverse DNS records at all.

Also great advice, I added both options, hope it will stop spam now :).


> **SeijiSensei said:**
> 
By the way, if your server is on a legitimate business-class connection, or your ISP is indifferent to whether you can host servers, then you might want to discuss fixing your reverse DNS entry so it matches the forward entry.  Only your ISP can make that change unless, as seems unlikely, your ISP has "[delegated]("http://www.ietf.org/rfc/rfc2317.txt")" to you the ability to create PTR records for your IP subnet.
Funny thing, my ISP actually has delegated the ability to change the PTR records for your own IP subnet :). For anyone interested, I use a VPS at TransIP (Dutch though).

[IMG]http://updo.nl/file/7c07f47c.png[/IMG]

So my reverse DNS has been fixed :).



Thanks again for all the great info, you really helped me out!

---

### Post by Jesse Degger on 2014-07-05
Holy... the spam continues!! How is this possible! I really dont understand any of this:

Jul  5 10:13:02 obfuscated postfix/smtpd[23497]: 0CCDE3FC0B: client=unknown[78.188.213.180], sasl_method=PLAIN, sasl_username=jesse@obfuscated.nl
Jul  5 10:13:02 obfuscated postfix/cleanup[23563]: 0CCDE3FC0B: message-id=<44464D8E4DDB46EA2A40EA7A0135D7B1@obfuscated.nl>
Jul  5 10:13:02 obfuscated postfix/qmgr[22819]: 0CCDE3FC0B: from=<filaoroalessandro@libero.it>, size=1388, nrcpt=1 (queue active)
Jul  5 10:13:03 obfuscated postfix/smtpd[23501]: 3DCDC3FCAB: client=unknown[94.20.144.61], sasl_method=PLAIN, sasl_username=jesse@obfuscated.nl
Jul  5 10:13:07 obfuscated postfix/cleanup[23505]: 3DCDC3FCAB: message-id=<FDF50EDB79B12C717E8B623B60EBBC6B@obfuscated.nl>
Jul  5 10:13:07 obfuscated postfix/qmgr[22819]: 3DCDC3FCAB: from=<hectorblasi@libero.it>, size=1356, nrcpt=2 (queue active)

-edit-
I think I got it! I noticed mails were sent via postfix/smtp and not via postfix/smtpd so I duplicated the restrictions to smtp_* instead of smtpd_*.  So far I see a lot of rejects in my logs (the servers are very busy sending spam) so that's something.

---

### Post by SeijiSensei on 2014-07-05
> **Jesse Degger said:**
> I can't add the last REJECT line via MySQL but thats not required right? Since we added 'reject_unknown_sender_domain'?

I'm not sure since I don't actually use Postfix on the servers where I deliver to mailboxes and have never used virtual hosts/users with MySQL.  I use sendmail with mbox mailboxes belonging to ordinary user accounts.  I have Postfix installed on a client's backup MX, but it just relays the mail to another server running [MailScanner]("http://www.mailscanner.info/") for processing.  (That server then forwards the cleaned mail stream to an Exchange server.)

I browsed a few of the other directives described in the [SMTPD_ACCESS_README]("http://www.postfix.org/SMTPD_ACCESS_README.html") document and found this one which might be even easier to apply in your case: [smtpd_reject_unlisted_sender](http://www.postfix.org/postconf.5.html#smtpd_reject_unlisted_sender).

> Funny thing, my ISP actually has delegated the ability to change the PTR records for your own IP subnet :). For anyone interested, I use a VPS at TransIP (Dutch though).

I use [Linode]("http://www.linode.com/"), and they offer this ability as well.  I'll be pedantic and observe that this isn't actually "delegation" in the sense of RFC2317, though.  That's designed for IP subnets like 192.168.1.128/28 (host addresses 129-143).  Your ISP, like mine, is simply offering the ability to replace the generic PTR records in its reverse DNS database with custom entries.

> Thanks again for all the great info, you really helped me out!

You're welcome.  Glad I could help.  I've been fighting spam and viruses for nearly two decades now.  It's an ongoing battle.

---

### Post by Jesse Degger on 2014-07-05
Well, I thought it was solved until my colleague pointed out we were not even able to receive any e-mail.. that's "unfortunate".

I REALLY have no idea what I am doing at this point, I just tried several configurations. I read loads and loads of postfix documentation but I don't seem to understand the logic behind how it works.

Current situation:
- I can receive e-mail (I fixed that, somehow)
- Spammers can't send e-mail
- Nobody on my mailserver can send any e-mails (not via webmail or clients)

Config:

```
##############
## TLS parameters
##############

smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database  = btree:${data_directory}/smtp_scache


##############
## GENERAL
##############

append_dot_mydomain = no


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

readme_directory = no

myhostname = obfuscated.nl
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = obfusserver, localhost.localdomain, localhost
mynetworks = 127.0.0.1, obfusserver, 141.138.139.24


mailbox_command = procmail -a "$EXTENSION"




##############
## SMTPD
##############    

smtpd_sender_restrictions    = reject_unknown_sender_domain,
                  permit_mynetworks,
                                  check_sender_access mysql:/etc/postfix/mysql-virtual-sender.cf


smtpd_helo_required        = yes
smtpd_helo_restrictions        = check_helo_access mysql:/etc/postfix/mysql-virtual-helo.cf

smtpd_client_restrictions    = reject_unauth_pipelining,
                                  reject_unknown_client_hostname,
                                 check_sender_access mysql:/etc/postfix/mysql-virtual-sender.cf
                   
smtpd_delay_reject        = no                            
smtpd_relay_restrictions     = reject_unauth_destination


smtpd_recipient_restrictions     = permit_sasl_authenticated,reject_unauth_destination,permit_mynetworks
    
    
    
    
##############
## SMTP
##############

smtp_sender_restrictions    = check_sender_access mysql:/etc/postfix/mysql-virtual-sender.cf,
                  permit_mynetworks,
                                 reject

smtp_helo_required        = yes
smtp_helo_restrictions        = check_helo_access mysql:/etc/postfix/mysql-virtual-helo.cf

#smtp_client_restrictions     = check_sender_access mysql:/etc/postfix/mysql-virtual-sender.cf,
#                                 reject_unauth_pipelining,
#                                 reject_unknown_client_hostname
                                 
smtpd_delay_reject        = no                            
smtp_relay_restrictions        = reject_unauth_destination

smtp_recipient_restrictions    = permit_sasl_authenticated,
                  reject_unauth_destination,
                  permit_mynetworks




##############
## VIRTUAL
##############

virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
virtual_transport = dovecot-spamass





##############    
## SASL
##############

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes




##############    
## OTHER
##############    

mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

dovecot_destination_recipient_limit = 1
dovecot-spamass_destination_recipient_limit = 1

message_size_limit = 100000000






##############
## MAPS
##############

header_checks = regexp:/etc/postfix/obfct/header_checks.conf
sender_dependent_default_transport_maps = hash:/etc/postfix/obfct/sender_dependent_transport_mapping.conf
transport_maps = hash:/etc/postfix/obfct/transport_mapping.conf


```

Hope somebody is able to clear some things up for me. As you can see I have a 'sort of duplicated version' of the smtpd_ restrictions also for smtp_ but that doesn't seem to work well. What is the exact difference between smtpd and smtp in this context? I understand the smtpd is the deamon but I didn't expect to have any diffrence between the deamon and the regular workers.

Really frustrated, want to burn my servers so any help is very much appreciated :)!

---

### Post by SeijiSensei on 2014-07-05
I have mynetworks = 0.0.0.0/0 to permit connections from anywhere. 

Also if you use reject_unauth_pipelining, you'll need a "sleep N" directive as well like I showed before.

If the machines you are connecting from don't have reverse DNS set up, reject_unknown_client_hostname will block them.

All my rules are of the smtpd_ form.  I don't know what smtp_ rules are intended to manage, nor do I see them mentioned in the [ACCESS]("http://www.postfix.org/SMTPD_ACCESS_README.html") document.

---

