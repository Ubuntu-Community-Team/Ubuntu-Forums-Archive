---
title: "Amavis,spamassassin, postfix"
date: 2010-01-25
forum: Server Platforms
---

### Post by LarsEriksson on 2010-01-25
im using the above mentioned setup, but we are still recieving a lot of spam mails, i cant really see what differs the mails that are stopped by the server and those that are passed.
But i would say about half of the mails go through.
When i test (spamassasin -t mailfile) it is recognized as spam.
```
root@DOMAIN:/home/vmail/DOMAIN.se/laeri/cur# spamassassin -t 1264419235.V821I128fcecM600341.DOMAIN\:2\, 
Received: from localhost by DOMAIN.DOMAIN
	with SpamAssassin (version 3.2.5);
	Mon, 25 Jan 2010 12:34:41 +0100
From: mm@DOMAIN.se
To: laeri@DOMAIN.se
Subject: [SPAM] Re[3]: Replica Rolex models
Date: Mon, 25 Jan 2010 12:33:55 +0100
Message-Id: <4b5d81a3.Cb3bkv3PshE3Kk2m%mm@DOMAIN.se>
X-Spam-Flag: YES
X-Spam-Checker-Version: SpamAssassin 3.2.5 (2008-06-10) on DOMAIN.DOMAIN
X-Spam-Level: ********************
X-Spam-Status: Yes, score=20.7 required=5.0 tests=ALL_TRUSTED,FS_REPLICA,
	RAZOR2_CF_RANGE_51_100,RAZOR2_CF_RANGE_E8_51_100,RAZOR2_CHECK,REPLICA_WATCH,
	SUBJ_RE_NUM,URIBL_AB_SURBL,URIBL_BLACK,URIBL_JP_SURBL,URIBL_OB_SURBL,
	URIBL_RHS_DOB,URIBL_SBL,URIBL_WS_SURBL autolearn=spam version=3.2.5
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----------=_4B5D81D1.81933360"

This is a multi-part message in MIME format.

------------=_4B5D81D1.81933360
Content-Type: text/plain; charset=iso-8859-1
Content-Disposition: inline
Content-Transfer-Encoding: 8bit

Spam detection software, running on the system "DOMAIN.DOMAIN", has
identified this incoming email as possible spam.  The original message
has been attached to this so you can view it (if it isn't spam) or label
similar future email.  If you have any questions, see
the administrator of that system for details.

Content preview:  Return-Path: <lazpgvlrcaweaaaaa@DOMAIN.se> X-Original-To:
   mailbox@DOMAIN.se Delivered-To: laeri@DOMAIN.se Received: from localhost
   (localhost.DOMAIN [127.0.0.1]) by DOMAIN.se (Postfix) with ESMTP id 32BF84E215
   for <mailbox@DOMAIN.se>; Sat, 23 Jan 2010 18:27:05 +0100 (CET) X-Virus-Scanned:
   Debian amavisd-new at DOMAIN.se Received: from DOMAIN.se ([127.0.0.1])
  by localhost (DOMAIN.se [127.0.0.1]) (amavisd-new, port 10024) with ESMTP
   id iqNOebHIBn3S for <mailbox@DOMAIN.se>; Sat, 23 Jan 2010 18:27:05 +0100
   (CET) Received: from c-67-182-49-105.hsd1.ca.comcast.net (c-67-182-49-105.hsd1.ca.comcast.net
   [67.182.49.105]) by DOMAIN.se (Postfix) with SMTP id C64484DF43 for <mailbox@DOMAIN.se>;
   Sat, 23 Jan 2010 18:27:02 +0100 (CET) To: <mailbox@DOMAIN.se> Subject: change
   your preferences From: Lionel Strickland <mailbox@DOMAIN.se> MIME-Version:
   1.0 Content-Type: text/html; charset="ISO-8859-1" Content-Transfer-Encoding:
   7bit Message-Id: <20100123172703.C64484DF43@DOMAIN.se> Date: Sat, 23 Jan
   2010 18:27:02 +0100 (CET) [...] 

Content analysis details:   (20.7 points, 5.0 required)

 pts rule name              description
---- ---------------------- --------------------------------------------------
 1.6 URIBL_AB_SURBL         Contains an URL listed in the AB SURBL blocklist
                            [URIs: suddentreat.com]
 2.1 URIBL_WS_SURBL         Contains an URL listed in the WS SURBL blocklist
                            [URIs: suddentreat.com]
 2.9 URIBL_JP_SURBL         Contains an URL listed in the JP SURBL blocklist
                            [URIs: suddentreat.com]
 2.1 URIBL_OB_SURBL         Contains an URL listed in the OB SURBL blocklist
                            [URIs: suddentreat.com]
 0.9 URIBL_RHS_DOB          Contains an URI of a new domain (Day Old Bread)
                            [URIs: suddentreat.com]
 2.0 URIBL_BLACK            Contains an URL listed in the URIBL blacklist
                            [URIs: suddentreat.com]
-1.4 ALL_TRUSTED            Passed through trusted hosts only via SMTP
 1.2 FS_REPLICA             Subject says "replica"
 3.4 REPLICA_WATCH          BODY: Message talks about a replica watch
 1.5 RAZOR2_CF_RANGE_E8_51_100 Razor2 gives engine 8 confidence level
                            above 50%
                            [cf: 100]
 0.5 RAZOR2_CHECK           Listed in Razor2 (http://razor.sf.net/)
 0.5 RAZOR2_CF_RANGE_51_100 Razor2 gives confidence level above 50%
                            [cf: 100]
 2.5 URIBL_SBL              Contains an URL listed in the SBL blocklist
                            [URIs: suddentreat.com]
 1.0 SUBJ_RE_NUM            Subject is faking 'The Bat!' responses
```

and this is what mail.log says:
```
Jan 25 13:11:03 DOMAIN amavis[3052]: (03052-17) Passed CLEAN, <mm@DOMAIN.se> -> <laeri@DOMAIN.se>, Message-ID: <4b5d8a57.gd8xMBRhPW0T8EB4%mm@DOMAIN.se>, mail_id: bgx2Yrnt9GkH, Hits: -, size: 3529, queued_as: 3E4864DE99, 95 ms
```

All the spam-mails that are tagged as "Passed CLEAN" get "Hits: -", i.e. no score, in the mail.log-file.

What is wrong here?

---

### Post by Roger_Smith on 2010-01-25
Is there anything prior to that log entry that says what amavis tried to do or did do? The only time I really see scores like that is if the email or some attachment was too big and it just bypassed amavis to avoid wasting time on it. 

You may need to enable more detailed logging in the /etc/amavis/conf.d/50-user to get some more details as to what amavis is trying to do. 

```

$log_level = 5;

```

---

### Post by noway2 on 2010-01-25
I think you need to adjust the settings in Amavis.  This should be under /etc/amavis/conf.d/.  The file will then be eithe 20- or 21-.

In order to get amavis to quarantine the spam and send you notification, you need these options:

$spam_admin = "user\@domain";
#$spam_quarantine_to = "user\@domain";
$spam_quarantine_to = 'spam-quarantine';

This will cause it to quarantine spam messages with a spam score greater than the required (5.0) and send notification to the user@domain.

You may also want to try grey listing using postgrey.

---

### Post by LarsEriksson on 2010-01-26
Ok i think ive got it, thanks to $log_level = 5;
I had whitlisted our domain in /var/lib/amavis/whitelist  like this:
domain.se

so all mail that had *@domain.se as sender was whitelisted.

I guess that solution for whitelisting really sucks, since anyone can send with whatever "from" address they want.
Does anyone have a better solution for whitelisting mails from our "own" users?

(where domain.se is our domain, where we all got mails, ie [email]lars.eriksson@domain.se[/email])

What is gray listing?
And, what file is used by amavis in Ubuntu 9.10, <20-debian_defaults> or <21-ubuntu_defaults> ?



Edit:
Never mind, ive read up on graylisting and postgrey, and installed it. The spam count(handled by Amavis) since ive installed it is on 0 :)   (the other questions still stays)
Thanks for the tip!

---

### Post by LarsEriksson on 2010-01-29
Since ive activated greylisting (postgrey), some of the clients get a reply from the server when they send a mail to someone in our domain.
I.e. [email]user1@DOMAIN.se[/email] sends mail to [email]user2@DOMAIN.se[/email], [email]user1@DOMAIN.se[/email] will get this reply(from system administrator):
```
450 4.2.0 <user2@DOMAIN.se>: Recipient address rejected: Greylisted, see http://postgrey.schwekert.ch/help/DOMAIN.se.html
```

How can i make this completely silent, i dont want to send a error message to anyone who tries to mail someone here.

---

### Post by noway2 on 2010-01-31
I am not sure if you can.  if it were completely silent, the messages would simply be dropped or discarded.  The 400 level error code is defined as a 'temporary' error with the indication that the server should retry.  It seems that some systems report this error code back to the originating sender and some do not.  Personally, I have never gotten report of this error back.  

Greylisting works by bouncing the email with a temporary error code, to cause compliant mail systems to resend.  The good news is that this should only happen the first time someone sends you mail from a particular domain.

---

