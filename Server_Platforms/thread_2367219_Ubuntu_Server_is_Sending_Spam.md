---
title: "Ubuntu Server is Sending Spam"
date: 2017-07-27
forum: Server Platforms
---

### Post by lorenzopro000 on 2017-07-27
Hi,
i know there are a lot of posts about this topic, but after 20 days of searches i don't find a solution yet.

The provider is filtering me with a block.
I have upgrade from Ubuntu 14.04 to 16.04, but i have the same problem (probably the malicious file is in the backup files?)
I can't find who and what is sending the spam, and i don't know how i can block this.

Any suggestion will be appreciate.

This is a postcat -vq of a sample mail from my queue. Thank you.

```
postcat: name_mask: all
postcat: inet_addr_local: configured 3 IPv4 addresses
postcat: inet_addr_local: configured 3 IPv6 addresses
*** ENVELOPE RECORDS deferred/8/8377DA1094 ***
message_size:            1239             617               1               0            1239               0
message_arrival_time: Thu Jul 27 09:32:34 2017
create_time: Thu Jul 27 09:32:34 2017
named_attribute: log_ident=8377DA1094
named_attribute: rewrite_context=local
sender: www-data@MYDOMAIN.com
named_attribute: log_client_name=localhost
named_attribute: log_client_address=127.0.0.1
named_attribute: log_client_port=34314
named_attribute: log_message_origin=localhost[127.0.0.1]
named_attribute: log_helo_name=MYDOMAIN.com
named_attribute: log_protocol_name=ESMTP
named_attribute: client_name=localhost
named_attribute: reverse_client_name=localhost
named_attribute: client_address=127.0.0.1
named_attribute: client_port=34314
named_attribute: helo_name=MYDOMAIN.com
named_attribute: protocol_name=ESMTP
named_attribute: client_address_type=2

named_attribute: dsn_orig_rcpt=rfc822;xxxxxxxxx@aol.com
original_recipient: xxxxxxxxx@aol.com
recipient: xxxxxxxxx@aol.com
*** MESSAGE CONTENTS deferred/8/8377DA1094 ***
regular_text: Received: from MYDOMAIN.com (localhost [127.0.0.1])
regular_text: 	by vps00000.ovh.net (Postfix) with ESMTPS id 8377DA1094
regular_text: 	for <xxxxxxxxx@aol.com>; Thu, 27 Jul 2017 09:32:34 +0200 (CEST)
regular_text: MIME-Version: 1.0
regular_text: Date: Thu, 27 Jul 2017 9:32:34 +0200
regular_text: Message-ID: <37759548.24895977.1501140754437@MYDOMAIN.com>
regular_text: Subject: Satisfy your sweetheart quickly
regular_text: From: www-data@MYDOMAIN.com
regular_text: Reply-To: www-data@MYDOMAIN.com
regular_text: To: xxxxxxxxx@aol.com
regular_text: X-Priority: 3 (Normal)
regular_text: X-Mailer: ESMTP 1.1
regular_text: Content-Type: multipart/alternative;
regular_text: 	boundary="----=_Part_24895984_747348941.1501140754533"
regular_text: 
regular_text: ------=_Part_24895984_747348941.1501140754533
regular_text: Content-Type: text/plain; charset=UTF-8
regular_text: Content-Transfer-Encoding: quoted-printable
regular_text: 
regular_text: 
regular_text: 
regular_text: SPAM TEXT
regular_text: 
regular_text: 
regular_text: 
regular_text: 
regular_text: ------=_Part_24895984_747348941.1501140754533
regular_text: Content-Type: text/html; charset=UTF-8
regular_text: Content-Transfer-Encoding: quoted-printable
regular_text: 
regular_text: SPAM TEXT
regular_text: 
regular_text: 
regular_text: ------=_Part_24895984_747348941.1501140754533--
*** HEADER EXTRACTED deferred/8/8377DA1094 ***
[FONT=Menlo]*** MESSAGE FILE END deferred/8/8377DA1094 ***[/FONT]
```

---

### Post by mastablasta on 2017-07-27
you need to restore only known good files/backup.

someone else with more sec experience might give a better advice. but

it should be like this:
1. take it "offline" - if you think there is a need for ruther investigation you can image it.
2. reinstall
3. restore from backup (only known good files, preferably only data)
4. harden it (it helps at this point to know what the entry point was)

---

### Post by SeijiSensei on 2017-07-27
The corresponding entries in /var/log/mail.log would be more helpful.  Does this machine accept mail from external senders?  The entries you give report connections on localhost.  From the looks of things, the spam is originating on your server, not being pushed through it.  

How many people other than you use this server? 

I'd start by testing to see whether your server is an "open relay:"  [https://mxtoolbox.com/diagnostic.aspx](https://mxtoolbox.com/diagnostic.aspx)

---

### Post by lorenzopro000 on 2017-07-28
Hi, 

"[COLOR=#000000]Does this machine accept mail from external senders?"
[/COLOR]No, this server is used only for host some websites and e-commerce. It send mail like order confirmation ecc..

[COLOR=#000000]"How many people other than you use this server?"
[/COLOR]Only me.

This parts of mail.log include the message id 8377DA1094 in the first post:

```

Jul 27 09:32:34 vps00000 postfix/smtpd[15402]: disconnect from localhost[127.0.0.1] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: connect from localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: 81262A1091: client=localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/cleanup[15406]: 81262A1091: message-id=<37759548.24895977.1501140754437@MYDOMAIN.COM>
Jul 27 09:32:34 vps00000 postfix/qmgr[15204]: 81262A1091: from=<www-data@MYDOMAIN.COM>, size=1243, nrcpt=1 (queue active)
Jul 27 09:32:34 vps00000 postfix/smtpd[15402]: connect from localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: disconnect from localhost[127.0.0.1] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Jul 27 09:32:34 vps00000 postfix/smtpd[15402]: 8377DA1094: client=localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/cleanup[15406]: 8377DA1094: message-id=<37759548.24895977.1501140754437@MYDOMAIN.COM>
Jul 27 09:32:34 vps00000 postfix/qmgr[15204]: 8377DA1094: from=<www-data@MYDOMAIN.COM>, size=1239, nrcpt=1 (queue active)
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: connect from localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/smtpd[15402]: disconnect from localhost[127.0.0.1] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: 865F1A1095: client=localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/cleanup[15406]: 865F1A1095: message-id=<37759548.24895977.1501140754437@MYDOMAIN.COM>
Jul 27 09:32:34 vps00000 postfix/qmgr[15204]: 865F1A1095: from=<www-data@MYDOMAIN.COM>, size=1241, nrcpt=1 (queue active)
Jul 27 09:32:34 vps00000 postfix/smtpd[15402]: connect from localhost[127.0.0.1]
Jul 27 09:32:34 vps00000 postfix/smtpd[15407]: disconnect from localhost[127.0.0.1] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7

```

---

### Post by SeijiSensei on 2017-07-28
Since the messages are being sent as the "www-data" user, it's likely something has infected one of your sites and is sending out the spam.  Do you use any "content-management" platforms like WordPress or Joomla?  If so, have you kept them up to date with all security patches?

Do you have any forms that people can use to send email?  If so, are they designed so that all the mail goes to a specific address?  If you have a form that lets people specify the destination email address, then it will be exploited to send spam.  Any website form should be designed to send mail only to an address that you control.  Better still if the destination address is hidden inside the code that processes the form input and not exposed in the site's publicly-visible HTML.

---

### Post by TheFu on 2017-07-30
There are millions of websites hacked just like yours.  Based on the spam I see, they are running some php webapp and usually added some theme or other addons to make life easier.  

Somehow the system became compromised.  Could have been through non-secure file/directory permissions or the addons or a theme.  

First thing is to let your visitors know there is an issue and contact all impacted clients/orders since their information has probably been compromised/stolen too.

Next, disable all outbound email. Do this with both a firewall rule and by disabling the MTA.

Next, figure out what is actually sending the email. Seems you've already narrowed it down to a webapp.  If you have multiple webapps, figure out which 1 is sending.  phpmail is a common issue.

Monitor the system closely. Better than last time.  Watch for all remote access, especially via FTP and ssh and nc and telnet.  Also watch for odd web URLs that don't make sense.  Your web analytics should provide help.

If none of these things is helping, they could be scrubbing the log files in real-time.  Get the logs directly written to a remote system.

BTW, I wouldn't trust the system now.  I'd wipe it completely and reinstall everything in the base fresh, completely up-to date, only using the backups for reference.  I would not install any addons or themes.

Depending on the tools you use, there are a number of security addons which might be helpful. 

I've felt your pain.  Been hacked 3 times in my career, but nothing on a server since 2002.

---

