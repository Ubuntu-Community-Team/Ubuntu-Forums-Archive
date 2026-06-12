---
title: "Postfix + Spamassassin + Amavis doesn't mark emails as spam?"
date: 2009-01-14
forum: Server Platforms
---

### Post by jussir on 2009-01-14
Hey,

We have a mail-server with Ubuntu 8.04.1. We use postfix, courier, amavis, spamassassin, etc.

# postconf -n
```
append_dot_mydomain = no
biff = no
body_checks_size_limit = 0
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 0
mydestination = # Empty cause virtual domains
mydomain = mail.domain.org
myhostname = mail.domain.org
mynetworks = 82.128.XXX.XXX 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtp.isp.com
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = smtpd
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /var/ssl/domain.com.crt
smtpd_tls_key_file = /var/ssl/domain.com.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_limit = 0
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 5000
virtual_transport = virtual
virtual_uid_maps = static:5000

```

Example of clean message:
```
Return-Path: <www-data@lingonberry.canonical.com>
X-Original-To: username@domain.com
Delivered-To: username@domain.com
Received: from localhost (localhost [127.0.0.1])
    by mail.domain.org (Postfix) with ESMTP id 8258C42325;
    Wed, 14 Jan 2009 09:16:42 +0200 (EET)
X-Virus-Scanned: Debian amavisd-new at mail.domain.org
Received: from mail.domain.org ([127.0.0.1])
    by localhost (mail.domain.org [127.0.0.1]) (amavisd-new, port 10024)
    with LMTP id KOCKUKPtFKXV; Wed, 14 Jan 2009 09:16:40 +0200 (EET)
Received: from lingonberry.canonical.com (lingonberry.canonical.com [91.189.94.13])
    by mail.domain.org (Postfix) with ESMTP id 5CACF4230D
    for <username@domain.com>; Wed, 14 Jan 2009 09:16:40 +0200 (EET)
Received: by lingonberry.canonical.com (Postfix, from userid 33)
    id 2ED57584321; Wed, 14 Jan 2009 07:16:40 +0000 (GMT)
To: username@domain.com
Subject: Welcome to Ubuntu Forums!
From: "Ubuntu Forums" <site@ubuntuforums.org>
Auto-Submitted: auto-generated
Message-ID: <20090114071640.adb6b001337c@ubuntuforums.org>
MIME-Version: 1.0
Content-Type: text/plain; charset="ISO-8859-1"
Content-Transfer-Encoding: 8bit
X-Priority: 3
X-Mailer: vBulletin Mail via PHP
Date: Wed, 14 Jan 2009 07:16:40 +0000 (GMT)

```

Example of spam message:
```
Return-Path: <nelsfred@libero.it>
X-Original-To: username@domain.org
Delivered-To: username@domain.org
Received: from localhost (localhost [127.0.0.1])
    by mail.domain.org (Postfix) with ESMTP id 823B141FF4;
    Thu, 8 Jan 2009 21:22:58 +0200 (EET)
X-Quarantine-ID: <8uLTyjtvX2k5>
X-Virus-Scanned: Debian amavisd-new at mail.domain.org
Received: from mail.domain.org ([127.0.0.1])
    by localhost (mail.domain.org [127.0.0.1]) (amavisd-new, port 10024)
    with LMTP id 8uLTyjtvX2k5; Thu, 8 Jan 2009 21:22:56 +0200 (EET)
Received: from mail.cpi-zgp.cn (unknown [218.28.140.74])
    by mail.domain.org (Postfix) with SMTP id 643F641F59
    for <username@domain.org>; Thu, 8 Jan 2009 21:22:55 +0200 (EET)
Received: from User ([77.224.200.19])
    (envelope-sender <nelsfred@libero.it>)
    by 192.168.0.223 with ESMTP
    for <username@kirjakauppaliitto.fi>; Fri, 09 Jan 2009 03:00:19 +0800
Reply-To: <nelson777fred@aol.com>
From: "Nelson Alfred"<nelsfred@libero.it>
Subject: Contact us for loan
Date: Thu, 8 Jan 2009 05:00:01 +0100
MIME-Version: 1.0
Content-Type: text/plain;
    charset="Windows-1251"
Content-Transfer-Encoding: 7bit
X-Priority: 3
X-MSMail-Priority: Normal
X-Mailer: Microsoft Outlook Express 6.00.2600.0000
X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2600.0000
Message-Id: <20090108192255.643F641F59@mail.domain.org>
To: undisclosed-recipients:;

```


I don't know why but it only adds "X-Quarantine-ID: <8uLTyjtvX2k5>" if I set "**$final_spam_destiny** = D_PASS;" in **/etc/amavis/conf.d/20-debian_defaults** and it doesn't even rewrite the subject to $sa_spam_subject_tag.

I'd want it only to deliver mail to "**.Junk**" folder so that no emails are lost.

Thanks already.

---

### Post by jussir on 2009-01-16
Thanks, this was solved by adding: **@local_domains_acl = ('.');** to /etc/amavis/conf.d/20-debian_defaults

---

### Post by sergiomc on 2009-09-23
Hi, 
how does it look your email headers now ?
May you share with us a copy to compare with your first header?

SergioMC

---

