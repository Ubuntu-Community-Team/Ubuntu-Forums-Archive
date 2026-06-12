---
title: "sendmail googlemail"
date: 2013-05-23
forum: Server Platforms
---

### Post by ako84 on 2013-05-23
hi

i am running a nginx server on lubuntu (odroid u2).
With installed "owncloud" and an gmail account as smtp server, i wanna send mails to recover login passwords (php code).
So i configured sendmail. I also configured SMTP but i dont know, if it works...
Now sending mails with "sendmail [EMAIL="mail@testserver.com"]mail@testserver.com[/EMAIL]" works fine!

But if i send mails with the php code (owncloud) i get following mail to /var/mail/root

```
  
 ----- The following addresses had permanent fatal errors -----
<lostpassword-noreply@localhost.localdomain>
    (reason: 550 Host unknown)




   ----- Transcript of session follows -----
550 5.1.2 <lostpassword-noreply@localhost.localdomain>... Host unknown (Name server: localhost.localdomain: host not found)


--r4NAQdel003234.1369304799/artesserver.localhost
Content-Type: message/delivery-status


Reporting-MTA: dns; artesserver.localhost
Received-From-MTA: DNS; localhost
Arrival-Date: Thu, 23 May 2013 12:26:39 +0200


Final-Recipient: RFC822; lostpassword-noreply@localhost.localdomain
Action: failed
Status: 5.1.2
Remote-MTA: DNS; localhost.localdomain
Diagnostic-Code: SMTP; 550 Host unknown
Last-Attempt-Date: Thu, 23 May 2013 12:26:39 +0200


--r4NAQdel003234.1369304799/artesserver.localhost
Content-Type: text/rfc822-headers
Content-Transfer-Encoding: 8bit


Return-Path: <>
Received: from artesserver.localhost (localhost [127.0.0.1])
    by artesserver.localhost (8.14.4/8.14.4/Debian-2ubuntu2) with ESMTP id r4NAQceo003232
    (version=TLSv1/SSLv3 cipher=DHE-RSA-AES256-SHA bits=256 verify=NOT)
    for <lostpassword-noreply@localhost.localdomain>; Thu, 23 May 2013 12:26:39 +0200
Received: from localhost (localhost)
    by artesserver.localhost (8.14.4/8.14.4/Submit) id r4NAQceF003231;
    Thu, 23 May 2013 12:26:38 +0200
Date: Thu, 23 May 2013 12:26:38 +0200
From: Mail Delivery Subsystem <MAILER-DAEMON@ArtesServer.localhost>
Message-Id: <201305231026.r4NAQceF003231@artesserver.localhost>
To: lostpassword-noreply@localhost.localdomain
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
    boundary="r4NAQceF003231.1369304798/artesserver.localhost"
Content-Transfer-Encoding: 8bit
Subject: Returned mail: see transcript for details
Auto-Submitted: auto-generated (failure)


--r4NAQdel003234.1369304799/artesserver.localhost--

```


I thought, that something is wrong in the hosts file
so i added
127.0.0.1    localhost.localdomain
to the hosts file

and now i get following mail to /var/mail/root

```
   ----- The following addresses had permanent fatal errors -----
<lostpassword-noreply@localhost.localdomain>
    (reason: 553 5.3.5 system config error)


   ----- Transcript of session follows -----
553 5.3.5 localhost.localdomain. config error: mail loops back to me (MX problem?)
554 5.3.5 Local configuration error
550 5.1.1 MAILER-DAEMON... User unknown


--r4NAkXY6007241.1369305993/artesserver.localhost
Content-Type: message/delivery-status


Reporting-MTA: dns; artesserver.localhost
Received-From-MTA: DNS; localhost
Arrival-Date: Thu, 23 May 2013 12:46:33 +0200


Final-Recipient: RFC822; lostpassword-noreply@localhost.localdomain
Action: failed
Status: 5.3.5
Diagnostic-Code: SMTP; 553 5.3.5 system config error
Last-Attempt-Date: Thu, 23 May 2013 12:46:33 +0200


--r4NAkXY6007241.1369305993/artesserver.localhost
Content-Type: text/rfc822-headers


Return-Path: <MAILER-DAEMON>
Received: from localhost (localhost)
    by artesserver.localhost (8.14.4/8.14.4/Debian-2ubuntu2) id r4NAkXY5007241;
    Thu, 23 May 2013 12:46:33 +0200
Date: Thu, 23 May 2013 12:46:33 +0200
From: Mail Delivery Subsystem <MAILER-DAEMON>
Message-Id: <201305231046.r4NAkXY5007241@artesserver.localhost>
To: <lostpassword-noreply@localhost.localdomain>
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
    boundary="r4NAkXY5007241.1369305993/artesserver.localhost"
Content-Transfer-Encoding: 8bit
Subject: Returned mail: see transcript for details
Auto-Submitted: auto-generated (failure)


--r4NAkXY6007241.1369305993/artesserver.localhost--



```

there are no entrys at the mail.log file

anybody could help me?

thx

---

### Post by SeijiSensei on 2013-05-23
Check the contents of /etc/mail/local-host-names and make sure there is an entry for localhost.localdomain in the list.  This file contains the list of all hostnames and domainnames that should be delivered to local mailboxes.  Restart sendmail after you make the change.

---

