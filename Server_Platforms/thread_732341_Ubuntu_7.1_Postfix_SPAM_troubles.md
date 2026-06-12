---
title: "Ubuntu 7.1 Postfix SPAM troubles"
date: 2008-03-22
forum: Server Platforms
---

### Post by scottlindner on 2008-03-22
I have been receiving SPAM on my recent Postfix installation and between the logs and message headers I cannot figure out how it's happening.  I'm new to Ubuntu and Postfix.  Previously I had been running other Linux distros using sendmail as my transport.  I'm still no genius so no hold's barred.  I would appreciate any help on this.

Some details of what's going on.  I run more than one domain.  I have a domain that I use as my primary domain called "scottsdomain.com" and my wife has a hobby domain called "wifesdomain.com".  She has been receiving SPAM to her email account on her domain at [email]wifesaccount@wifesdomain.com[/email].  Today she received an email that was sent from accounts on my primary domain that do not exist, but from an IP address that is outside of my LAN.  What I don't understand is the mail header says it was sent from three different accounts, [email]Top@scottsdomain.com[/email], [email]SEO@scottsdomain.com[/email], [email]Secrets@scottsdomain.com[/email].  None of these exist.  I find this alarming because it seems someone outside of my LAN can send email from my server.  That is definitely not what I intend.

main.cf
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

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = scottsdomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = scottsdomain.com, localhost
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = 
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,check_policy_service unix:private/policy-spf
relayhost = smtp.comcast.net
mynetworks = 127.0.0.0/8 192.168.0.0/24
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

spf-policyd_time_limit = 3600s
home_mailbox = Maildir/
smtpd_sasl_path = private/auth-client

message_size_limit = 20480000
content_filter = smtp-amavis:[127.0.0.1]:10024



SPAM message header
> Return-Path: <webmaster@promote-biz.net>
X-Original-To: [email]wifesaccount@wifesdomain.com[/email]
Delivered-To: [email]wifesaccount@wifesdomain.com[/email]
Received: from localhost (localhost [127.0.0.1])
	by scottsdomain.com (Postfix) with ESMTP id EA569169C48B
	for <wifesaccount@wifesdomain.com>; Fri, 21 Mar 2008 19:58:52 -0600 (MDT)
X-Virus-Scanned: Debian amavisd-new at scottsdomain.com
Received: from scottsdomain.com ([127.0.0.1])
	by localhost (barleywine.beer [127.0.0.1]) (amavisd-new, port 10024)
	with ESMTP id Y1sho0ciDpIU for <wifesaccount@wifesdomain.com>;
	Fri, 21 Mar 2008 19:58:37 -0600 (MDT)
Received-SPF: None () HELO client-ip=124.236.253.93; helo=promote-biz.net; envelope-from=webmaster@promote-biz.net; receiver=wifesaccount@wifesdomain.com; 
Received: from promote-biz.net (unknown [124.236.253.93])
	by scottsdomain.com (Postfix) with ESMTP id 82FF2169C47B
	for <wifesaccount@wifesdomain.com>; Fri, 21 Mar 2008 19:58:34 -0600 (MDT)
Reply-To: [email]webmaster@promote-biz.net[/email]
From: [email]Top@scottsdomain.com[/email], [email]SEO@scottsdomain.com[/email],
	[email]Secrets@scottsdomain.com[/email]
To: [email]wifesaccount@wifesdomain.com[/email]
Subject: 1000s Of Hits From Google, Yahoo, MSN And Others At $0 Cost To You !
Date: 21 Mar 2008 18:58:32 -0700
Message-ID: <20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>
MIME-Version: 1.0
Content-Type: text/plain
Content-Transfer-Encoding: 8bit



log files:
> $ grep EA569169C48B *
mail.info:Mar 21 19:58:52 barleywine postfix/smtpd[28890]: EA569169C48B: client=localhost[127.0.0.1]
mail.info:Mar 21 19:58:52 barleywine postfix/cleanup[28886]: EA569169C48B: message-id=<20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>
mail.info:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: from=<webmaster@promote-biz.net>, size=4473, nrcpt=1 (queue active)
mail.info:Mar 21 19:58:53 barleywine amavis[24855]: (24855-05) Passed CLEAN, [124.236.253.93] [124.236.253.93] <webmaster@promote-biz.net> -> <wifesaccount@wifesdomain.com>, Message-ID: <20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>, mail_id: Y1sho0ciDpIU, Hits: 4.257, queued_as: EA569169C48B, 15170 ms
mail.info:Mar 21 19:58:53 barleywine postfix/smtp[28887]: 82FF2169C47B: to=<wifesaccount@wifesdomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=19, delays=3.7/0.01/0/15, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=24855-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as EA569169C48B)
mail.info:Mar 21 19:58:53 barleywine postfix/local[28892]: EA569169C48B: to=<wifesaccount@wifesdomain.com>, relay=local, delay=0.09, delays=0.05/0.01/0/0.03, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
mail.info:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: removed
mail.log:Mar 21 19:58:52 barleywine postfix/smtpd[28890]: EA569169C48B: client=localhost[127.0.0.1]
mail.log:Mar 21 19:58:52 barleywine postfix/cleanup[28886]: EA569169C48B: message-id=<20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>
mail.log:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: from=<webmaster@promote-biz.net>, size=4473, nrcpt=1 (queue active)
mail.log:Mar 21 19:58:53 barleywine amavis[24855]: (24855-05) Passed CLEAN, [124.236.253.93] [124.236.253.93] <webmaster@promote-biz.net> -> <wifesaccount@wifesdomain.com>, Message-ID: <20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>, mail_id: Y1sho0ciDpIU, Hits: 4.257, queued_as: EA569169C48B, 15170 ms
mail.log:Mar 21 19:58:53 barleywine postfix/smtp[28887]: 82FF2169C47B: to=<wifesaccount@wifesdomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=19, delays=3.7/0.01/0/15, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=24855-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as EA569169C48B)
mail.log:Mar 21 19:58:53 barleywine postfix/local[28892]: EA569169C48B: to=<wifesaccount@wifesdomain.com>, relay=local, delay=0.09, delays=0.05/0.01/0/0.03, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
mail.log:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: removed
syslog.0:Mar 21 19:58:52 barleywine postfix/smtpd[28890]: EA569169C48B: client=localhost[127.0.0.1]
syslog.0:Mar 21 19:58:52 barleywine postfix/cleanup[28886]: EA569169C48B: message-id=<20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>
syslog.0:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: from=<webmaster@promote-biz.net>, size=4473, nrcpt=1 (queue active)
syslog.0:Mar 21 19:58:53 barleywine amavis[24855]: (24855-05) Passed CLEAN, [124.236.253.93] [124.236.253.93] <webmaster@promote-biz.net> -> <wifesaccount@wifesdomain.com>, Message-ID: <20080321185829.C08ABAE4C31B1233@from.header.has.no.domain>, mail_id: Y1sho0ciDpIU, Hits: 4.257, queued_as: EA569169C48B, 15170 ms
syslog.0:Mar 21 19:58:53 barleywine postfix/smtp[28887]: 82FF2169C47B: to=<wifesaccount@wifesdomain.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=19, delays=3.7/0.01/0/15, dsn=2.6.0, status=sent (250 2.6.0 Ok, id=24855-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as EA569169C48B)
syslog.0:Mar 21 19:58:53 barleywine postfix/local[28892]: EA569169C48B: to=<wifesaccount@wifesdomain.com>, relay=local, delay=0.09, delays=0.05/0.01/0/0.03, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
syslog.0:Mar 21 19:58:53 barleywine postfix/qmgr[20219]: EA569169C48B: removed


Any pointers will really help.

Cheers,
Scott

---

### Post by scottlindner on 2008-03-23
There's one point I should clarify on.   I want my postfix configuration to accept new email for delivery from clients on the LAN only.  This would stop the SPAM example I provided.  At least I think it would.

Scott

---

### Post by MJN on 2008-03-23
> **scottlindner said:**
> What I don't understand is the mail header says it was sent from three different accounts, [EMAIL="Top@scottsdomain.com"]Top@scottsdomain.com[/EMAIL], [EMAIL="SEO@scottsdomain.com"]SEO@scottsdomain.com[/EMAIL], [EMAIL="Secrets@scottsdomain.com"]Secrets@scottsdomain.com[/EMAIL].  None of these exist.  I find this alarming because it seems someone outside of my LAN can send email from my server.  That is definitely not what I intend.

That's not what's happening - the spam only *appears* to be coming from those addresses, and your server. A spammer can put whatever From: address in that he likes - he's not going to put his own in hence randomly chooses address, often within the destination domain. The key thing to realise here though is that he's not using your server to do it, he's sending them from 124.236.253.93 - that's his (or most likely someone's elses) server.

You have various options to limit this, and indeed spam as a whole. Look at implementing SPF on your domain and enforcing it at your server (hence stopping your domain being spoofed, but it can have some drawbacks), general spam filtering (although I see you're using amavis, presumably with SpamAssassin so perhaps this needs training), greylisting and RBLs.

> There's one point I should clarify on. I want my postfix configuration to accept new email for delivery from clients on the LAN only.

Are you sure you want that? If so, you're not going to receive any mail from anyone else on the Internet.

Mathew

---

### Post by scottlindner on 2008-03-23
Hmm.. My "one point" wasn't clear, or maybe I'm too much of a n00b to know the difference in what you're telling me.  When I send an email, I do it from the LAN.  I don't want anyone else to be able to do that.  For incoming email I want to accept email from everyone (excluding SPAMmers).  Are these one in the same thing and I need to choose LAN only or fully open?  Or is there a difference between accepting email to be delivered to my domains, vice, accepting email to be delivered to other domains?

You made me feel quite a bit more comfortable that nothing funny is going on.  It seems like I should give SPF and some public blacklists a shot.  Is there a good reference for setting these up?

BTW.  I'm still a n00b with Postfix.  I copied the configuration verbatum for the SPAM filtering you see in my config.  I have a question you might be able to answer.  Is there a way to configure it to deliver all SPAM to a folder instead of discarding it?

Thanks for the reply!  I haven't found good place to talk about Postfix troubles yet.

Cheers,
Scott

---

### Post by MJN on 2008-03-23
> **scottlindner said:**
> For incoming email I want to accept email from everyone (excluding SPAMmers).  Are these one in the same thing and I need to choose LAN only or fully open?  Or is there a difference between accepting email to be delivered to my domains, vice, accepting email to be delivered to other domains?

You've hit the nail on the head with that last sentence - you need to accept mail from anyone (pretty much) from anywhere (again, perhaps within reason) to your local domains. You only want to restrict mail destined for other domains to be clients from your local LAN and/or those that authenticate.

> You made me feel quite a bit more comfortable that nothing funny is going on.  It seems like I should give SPF and some public blacklists a shot.  Is there a good reference for setting these up?

I'm sure there are - you'll have to look around. What I would suggest is not tackling everything at once - take it one step at a time.

> I have a question you might be able to answer.  Is there a way to configure it to deliver all SPAM to a folder instead of discarding it?

Yes, you need to set amavis to only mark spam, and not reject it. Configuring this will depend on how you've set things up. Then, with the marked mail you could use procmail to automatically move it into users' spam folders. Again though, take this one step at a time.

> Thanks for the reply!  I haven't found good place to talk about Postfix troubles yet.

Well hopefully you've come to the right place, there is a lot of Postfix experience here. At the risk of sounding like a stuck record though you will find it tough going if you try and boil the ocean in one, and you'll find it tough getting others along to help you so break the task down.

Mathew

---

### Post by scottlindner on 2008-03-24
> **MJN said:**
> You've hit the nail on the head with that last sentence - you need to accept mail from anyone (pretty much) from anywhere (again, perhaps within reason) to your local domains. You only want to restrict mail destined for other domains to be clients from your local LAN and/or those that authenticate.



I'm sure there are - you'll have to look around. What I would suggest is not tackling everything at once - take it one step at a time.



Yes, you need to set amavis to only mark spam, and not reject it. Configuring this will depend on how you've set things up. Then, with the marked mail you could use procmail to automatically move it into users' spam folders. Again though, take this one step at a time.



Well hopefully you've come to the right place, there is a lot of Postfix experience here. At the risk of sounding like a stuck record though you will find it tough going if you try and boil the ocean in one, and you'll find it tough getting others along to help you so break the task down.

Mathew

To be honest, I did not know I was making this a big thing.  I thought "fighting SPAM" sounded like a single topic.  I was not aware that it was much bigger than that.

If this is the place, then I'll try to break it down.  I'm not sure if you did it intentionally, but you did a pretty good job breaking things down for me already.  I think my first step is to set up a SPAM folder and have SPAM routed there.  Loosing valid email could be worse than receiving the SPAM.

Cheers,
Scott

---

