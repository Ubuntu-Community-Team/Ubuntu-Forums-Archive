---
title: "mail() function"
date: 2008-08-19
forum: Server Platforms
---

### Post by magpy on 2008-08-19
Hi all

I am configuring a mail server using ubuntu 6.06.  I followed the
serverguide instructions.  When I tried to run a simple php mail() function I received this e-mail message after running the 'mailq' command:

 
<<<_START_MESSAGE_

Reporting-MTA: dns; cadava
X-Postfix-Queue-ID: AB0009906D2
X-Postfix-Sender: rfc822; [email]xxxxx@mail.cadava.com[/email]
Arrival-Date: Sun, 17 Aug 2008 23:15:21 +0100 (BST)

Final-Recipient: rfc822; [email]me@mail.cadava.com[/email]
Original-Recipient: rfc822; me
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; unknown user: "xx"

Final-Recipient: rfc822; [email]xxxxxxx_x@hotmail.com[/email]
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; host mx3.hotmail.com[65.54.244.200] said: 550
DY-001 Mail rejected by Windows Live Hotmail for policy reasons. We
generally do not accept email from dynamic IP's as they are not typically
used to deliver unauthenticated SMTP e-mail to an Internet mail server.
[http://www.spamhaus.org](http://www.spamhaus.org) maintains lists of dynamic and residential IP
addresses. If you are not an email/network admin please contact your
E-mail/Internet Service Provider for help. Email/network admins, please
visit [http://postmaster.live.com](http://postmaster.live.com) for email delivery information and support
(in reply to MAIL FROM command)

Final-Recipient: rfc822; [email]tel@mail.cadava.com[/email]
Original-Recipient: rfc822; tel
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; unknown user: "tel"

--AB0009906D2.1219011322/cadava
Content-Description: Undelivered Message
Content-Type: message/rfc822

Received: by cadava (Postfix, from userid 1000)
id AB0009906D2; Sun, 17 Aug 2008 23:15:21 +0100 (BST)
To: [email]me@mail.cadava.com[/email], [email]tel@mail.cadava.com[/email]
Subject: that is great
Cc: [email]ultimathule_6@hotmail.com[/email]
Message-Id:
Date: Sun, 17 Aug 2008 23:15:21 +0100 (BST)
From: [email]xxxxx@mail.cadava.com[/email] (xxxxx xxxxxxxx)



--AB0009906D2.1219011322/cadava--

__END_MESSAGE_

Could anyone expand on what it means?  Cheers!!  I have checked the  spamhaus web site listed in the error message and I am not listed there.  My ISP 'pipex' service 'pipex-lite' supports a mail server with static IP.  So I am not sure why the block took place.

---

