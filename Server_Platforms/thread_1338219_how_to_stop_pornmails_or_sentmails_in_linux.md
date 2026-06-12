---
title: "how to stop pornmails or sentmails in linux"
date: 2009-11-26
forum: Server Platforms
---

### Post by mady03sam on 2009-11-26
[SIZE=4]hi frnz,
 im gettin thousands of spam mails to ma system wen im clearin d log then again im gettin stuck wid d same issue its again filled with d thousands of mails with in short time soo how to stop those mails in linux i dissconnected ma LAN and Networ cable..................... after stopin the mail services its lukin fine but give me permanent solution to stop those spam mails[/SIZE]

---

### Post by mady03sam on 2009-11-26
Reporting-MTA: dns; srinath.domain.com
Arrival-Date: Thu, 26 Nov 2009 16:08:38 +0530

Final-Recipient: RFC822; [email]scastro_dq@163.net[/email]
Action: failed
Status: 5.1.3
Diagnostic-Code: SMTP; 553 You are not authorized to send mail as <>
Last-Attempt-Date: Thu, 26 Nov 2009 16:31:00 +0530

--nAQB0lNN006732.1259233260/srinath.domain.com
Content-Type: message/rfc822

Return-Path: <MAILER-DAEMON>
Received: from localhost (localhost)
    by srinath.domain.com (8.14.3/8.14.3) id nAQAcV0u006420;
    Thu, 26 Nov 2009 16:08:38 +0530
Date: Thu, 26 Nov 2009 16:08:38 +0530
From: Mail Delivery Subsystem <MAILER-DAEMON>
Message-Id: <200911261038.nAQAcV0u006420@srinath.domain.com>
To: <scastro_dq@163.net>
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
    boundary="nAQAcV0u006420.1259231918/srinath.domain.com"
Content-Transfer-Encoding: 8bit
Subject: Warning: could not send message for past 4 hours
Auto-Submitted: auto-generated (warning-timeout)

This is a MIME-encapsulated message

--nAQAcV0u006420.1259231918/srinath.domain.com

    **********************************************
    **      THIS IS A WARNING MESSAGE ONLY      **
    **  YOU DO NOT NEED TO RESEND YOUR MESSAGE  **
    **********************************************

The original message was received at Thu, 26 Nov 2009 02:51:25 +0530
from srinath.domain.com [127.0.0.1]

   ----- Transcript of session follows -----
451 163.net: Name server timeout
451 163.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
451 990.net: Name server timeout
Warning: message still undelivered after 4 hours
Will keep trying until message is 5 days old
451 163.net: Name server timeout

--nAQAcV0u006420.1259231918/srinath.domain.com
Content-Type: message/delivery-status

Reporting-MTA: dns; srinath.domain.com
Arrival-Date: Thu, 26 Nov 2009 02:51:25 +0530

Final-Recipient: RFC822; [email]shennaohen@990.net[/email]
Action: delayed
Status: 4.4.3
Last-Attempt-Date: Thu, 26 Nov 2009 16:08:38 +0530
Will-Retry-Until: Tue, 1 Dec 2009 02:51:25 +0530

Final-Recipient: RFC822; [email]shennaogeng@990.net[/email]
Action: delayed
Status: 4.4.3
Last-Attempt-Date: Thu, 26 Nov 2009 16:08:38 +0530
Will-Retry-Until: Tue, 1 Dec 2009 02:51:25 +0530

Final-Recipient: RFC822; [email]shenmutan@990.net[/email]
Action: delayed
Status: 4.4.3
Last-Attempt-Date: Thu, 26 Nov 2009 16:08:38 +0530
Will-Retry-Until: Tue, 1 Dec 2009 02:51:25 +0530

---

### Post by Lars Noodén on 2009-11-26
Be sure to enable greylisting on your mta and make sure that your machine is not accidentally set to be an open relay.

As far as a permanent solution goes, that means that you must encourage politicians and law enforcement to shut down those advertising via spam, i.e. find out where the money would go if someone actually tried to order the item in the spam

---

### Post by mady03sam on 2009-11-27
hey buddy thanx fr ur valuable reply but tell me stepbystep how to stop those mails coz im new to dis world.................

---

