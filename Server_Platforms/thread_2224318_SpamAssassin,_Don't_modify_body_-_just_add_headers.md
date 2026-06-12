---
title: "SpamAssassin, Don't modify body - just add headers?"
date: 2014-05-15
forum: Server Platforms
---

### Post by wolfgentleman on 2014-05-15
I am using the default SpamAssassin config files, well for the most part. The only modified part is that I made the Bayes DB directory site-wide. When SpamAssassin marks a message as spam is also messes with the message itself.
Before:
> From - Fri Apr 11 00:12:52 2014X-Mozilla-Status: 0001
X-Mozilla-Status2: 00000000
X-Mozilla-Keys:                                                                                 
Return-Path: <advertise.bz222r@gmail.com>
X-Original-To: [EMAIL="contact@twprogrammers.com"]contact@twprogrammers.com[/EMAIL]
Received: from gmail.com (unknown [125.141.199.245])
    by mail.twprogrammers.com (Postfix) with SMTP id BE89150FB7
    for <contact@twprogrammers.com>; Tue, 25 Mar 2014 06:21:21 -0500 (CDT)
Message-ID: <D3FB82B2.F722A773@gmail.com>
Date: Wed, 29 Jan 2014 06:20:58 +0200
Reply-To: "Cheap Stable FB Fans" <advertise.bz222r@gmail.com>
From: "Cheap Stable FB Fans" <advertise.bz222r@gmail.com>
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1.9) Gecko/20100317 Thunderbird/3.0.4
MIME-Version: 1.0
To: <contact@twprogrammers.com>
Subject: Get more likes on your FB Page
Content-Type: multipart/mixed;
    boundary="------------810386412445478750437375"

This is a multi-part message in MIME format.

--------------810386412445478750437375
Content-Type: text/plain;
    charset="us-ascii"
Content-Transfer-Encoding: 7bit

Buy GUARANTEED Facebook Likes/Fans, 
at the cheapest prices and become more popular!

- Safely delivered, absolutely no risk!
- Order processed within 24 hours or less!
- Manually Promoted by experts  not bots/software involved
- High-Quality service.

We offer different packages at different prices.


For Full Details please read the attached .html file











Unsubscribe option available on the footer of our website


--------------810386412445478750437375
Content-Type: application/octet-stream;
    name="FullDetails.html"
Content-Transfer-Encoding: base64
Content-Disposition: attachment;
    filename="FullDetails.html"

PGh0bWw+DQoNCjxoZWFkPg0KPE1FVEEgSFRUUC1FUVVJVj0iUmVmcmVzaCIgY29udGVudD0gIjI7
VVJMPWh0dHA6Ly93d3cuYWR2ZXJ0aXNlLWJ6cy5uZXQvZmFjZWJvb2svIj4NCjwvaGVhZD4NCg0K
PHA+PGZvbnQgZmFjZT0iVmVyZGFuYSI+TG9hZGluZyA8Yj48YSBocmVmPSJodHRwOi8vd3d3LmFk
dmVydGlzZS1ienMubmV0L2ZhY2Vib29rLyI+RnVsbA0KRGV0YWlsczwvYT4gPC9iPjwvZm9udD48
L3A+DQo8L2h0bWw+DQoNCg==

--------------810386412445478750437375--
 
And after:
> Received: from localhost by Frask.Server    with SpamAssassin (version 3.3.2);
    Sun, 11 May 2014 06:55:08 -0500
From: "Cheap Stable FB Fans" <advertise.bz222j@gmail.com>
To: <info@twprogrammers.com>
Subject: Get more likes on your FB Page
Date: Sun, 11 May 2014 20:54:47 -0700
Message-Id: <DDA351CA.18B07865@gmail.com>
X-Spam-Checker-Version: SpamAssassin 3.3.2 (2011-06-06) on Frask.Server
X-Spam-Flag: YES
X-Spam-Level: **************
X-Spam-Status: Yes, score=14.4 required=5.0 tests=DATE_IN_FUTURE_12_24,
    DKIM_ADSP_CUSTOM_MED,FREEMAIL_FROM,NML_ADSP_CUSTOM_MED,RCVD_IN_BL_SPAMCOP_NET,
    RCVD_IN_BRBL_LASTEXT,RCVD_IN_PSBL,RCVD_IN_RP_RNBL,RCVD_IN_XBL,RDNS_NONE,
    SPF_HELO_SOFTFAIL,SPF_SOFTFAIL,T_OBFU_HTML_ATTACH autolearn=unavailable
    version=3.3.2
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----------=_536F651C.34BBAC78"

This is a multi-part message in MIME format.

------------=_536F651C.34BBAC78
Content-Type: text/plain; charset=iso-8859-1
Content-Disposition: inline
Content-Transfer-Encoding: 8bit

Spam detection software, running on the system "Frask.Server", has
identified this incoming email as possible spam.  The original message
has been attached to this so you can view it (if it isn't spam) or label
similar future email.  If you have any questions, see
@@CONTACT_ADDRESS@@ for details.

Content preview:  Buy GUARANTEED FB Likes/Fans, at the cheapest prices and become
   more popular! - Safely delivered, absolutely no risk! - Order processed within
   24 hours or less! - Manually Promoted by experts not bots/software involved
   - High-Quality service. [...] 

Content analysis details:   (14.4 points, 5.0 required)

 pts rule name              description
---- ---------------------- --------------------------------------------------
 0.0 FREEMAIL_FROM          Sender email is commonly abused enduser mail provider
                            (advertise.bz222j[at]gmail.com)
 1.2 RCVD_IN_BL_SPAMCOP_NET RBL: Received via a relay in bl.spamcop.net
               [Blocked - see <http://www.spamcop.net/bl.shtml?211.43.211.41>]
 0.7 RCVD_IN_XBL            RBL: Received via a relay in Spamhaus XBL
                            [211.43.211.41 listed in zen.spamhaus.org]
 1.6 RCVD_IN_BRBL_LASTEXT   RBL: RCVD_IN_BRBL_LASTEXT
                            [211.43.211.41 listed in bb.barracudacentral.org]
 1.3 RCVD_IN_RP_RNBL        RBL: Relay in RNBL,
                            [https://senderscore.org/blacklistlookup/](https://senderscore.org/blacklistlookup/)
                            [211.43.211.41 listed in bl.score.senderscore.com]
 2.7 RCVD_IN_PSBL           RBL: Received via a relay in PSBL
                            [211.43.211.41 listed in psbl.surriel.com]
 0.0 DKIM_ADSP_CUSTOM_MED   No valid author signature, adsp_override is
                            CUSTOM_MED
 1.0 SPF_SOFTFAIL           SPF: sender does not match SPF record (softfail)
 2.5 DATE_IN_FUTURE_12_24   Date: is 12 to 24 hours after Received: date
 0.9 SPF_HELO_SOFTFAIL      SPF: HELO does not match SPF record (softfail)
 0.0 T_OBFU_HTML_ATTACH     BODY: HTML attachment with non-text MIME type
 1.3 RDNS_NONE              Delivered to internal network by a host with no rDNS
 1.2 NML_ADSP_CUSTOM_MED    ADSP custom_med hit, and not from a mailing list

The original message was not completely plain text, and may be unsafe to
open with some email clients; in particular, it may contain a virus,
or confirm that your address can receive spam.  If you wish to view
it, it may be safer to save it to a file and open it with an editor.


------------=_536F651C.34BBAC78
Content-Type: message/rfc822; x-spam-type=original
Content-Description: original message before SpamAssassin
Content-Disposition: attachment
Content-Transfer-Encoding: 8bit

Return-Path: <advertise.bz222j@gmail.com>
X-Original-To: [EMAIL="info@twprogrammers.com"]info@twprogrammers.com[/EMAIL]
Received: from gmail.com (unknown [211.43.211.41])
    by mail.twprogrammers.com (Postfix) with SMTP id 663DD50FC7
    for <info@twprogrammers.com>; Sun, 11 May 2014 06:54:59 -0500 (CDT)
Message-ID: <DDA351CA.18B07865@gmail.com>
Date: Sun, 11 May 2014 20:54:47 -0700
From: "Cheap Stable FB Fans" <advertise.bz222j@gmail.com>
User-Agent: Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; fr-FR; rv:1.7.10) Gecko/20050716 Thunderbird/1.0.6
X-Accept-Language: en-us
MIME-Version: 1.0
To: <info@twprogrammers.com>
Subject: Get more likes on your FB Page
Content-Type: multipart/mixed;
    boundary="------------055068663637112273544376"

This is a multi-part message in MIME format.

--------------055068663637112273544376
Content-Type: text/plain;
    charset="us-ascii"
Content-Transfer-Encoding: 7bit

Buy GUARANTEED FB Likes/Fans, 
at the cheapest prices and become more popular!

- Safely delivered, absolutely no risk!
- Order processed within 24 hours or less!
- Manually Promoted by experts  not bots/software involved
- High-Quality service.

We offer different packages at different prices.


For Full Details please read the attached .html file











Unsubscribe option available on the footer of our website


--------------055068663637112273544376
Content-Type: application/octet-stream;
    name="FullDetails.html"
Content-Transfer-Encoding: base64
Content-Disposition: attachment;
    filename="FullDetails.html"

PGh0bWw+DQoNCjxoZWFkPg0KPE1FVEEgSFRUUC1FUVVJVj0iUmVmcmVzaCIgY29udGVudD0gIjI7
VVJMPWh0dHA6Ly93d3cuYWR2ZXJ0aXNlLWJ6cy5uZXQvZmFjZWJvb2svIj4NCjwvaGVhZD4NCg0K
PHA+PGZvbnQgZmFjZT0iVmVyZGFuYSI+TG9hZGluZyA8Yj48YSBocmVmPSJodHRwOi8vd3d3LmFk
dmVydGlzZS1ienMubmV0L2ZhY2Vib29rLyI+RnVsbA0KRGV0YWlsczwvYT4gPC9iPjwvZm9udD48
L3A+DQo8L2h0bWw+DQoNCg==

--------------055068663637112273544376--


------------=_536F651C.34BBAC78-- 

By the way, the message above were 2 different copies. One was sent to contact@, the other to info@. So they aren't identical, but they are sent by the same company and all that. The reason I did it this way is because one is from before I got SpamAssassin working, the other is after.

So how do I make it just add the X-Spam* headers and not completely change the message?

---

### Post by SeijiSensei on 2014-05-23
Try these:
> 
report_header { 0 | 1 } (default: 0)

    By default, SpamAssassin will include its report in the body of suspected spam. Enabling this causes the report to go in the headers instead. Using 'use_terse_report' with this is recommended.

use_terse_report { 0 | 1 } (default: 0)

    By default, SpamAssassin uses a fairly long report format. Enabling this uses a shorter format which includes all the information in the normal one, but without the superfluous explanations.


See [http://search.cpan.org/~msergeant/Mail-SpamAssassin-2.43/lib/Mail/SpamAssassin/Conf.pm#SETTINGS](http://search.cpan.org/~msergeant/Mail-SpamAssassin-2.43/lib/Mail/SpamAssassin/Conf.pm#SETTINGS) and search for "report".  You can also define a custom report.  Setting it to an empty string might solve your problem.

---

### Post by wolfgentleman on 2014-05-23
I just added it to my /usr/share/spamassassin/local.cf file at the bottom. That is where I was supposed to put it right? I restarted the SpamAssassin daemon, so now I just wait I guess. Actually I will send myself a spam message and report back in a few moments.

Update:
It didn't seem to do anything:
> Received: from localhost by Frask.Server	with SpamAssassin (version 3.3.2);
	Fri, 23 May 2014 15:17:17 -0500
From: Patrick <pwthomas95@satx.rr.com>
To: [email]admin@twprogrammers.com[/email]
Subject: C h e a p - F a c e b o o k - F a n s
Date: Fri, 23 May 2014 15:17:32 -0500
Message-Id: <537FACDC.408@satx.rr.com>
X-Spam-Checker-Version: SpamAssassin 3.3.2 (2011-06-06) on Frask.Server
X-Spam-Flag: YES
X-Spam-Level: ******
X-Spam-Status: Yes, score=6.5 required=5.0 tests=GAPPY_SUBJECT,SPF_PASS,
	SUBJECT_FUZZY_CHEAP,T_RP_MATCHES_RCVD,URIBL_DBL_SPAM,URIBL_WS_SURBL
	autolearn=no version=3.3.2
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----------=_537FACCD.E555FE9B"

This is a multi-part message in MIME format.

------------=_537FACCD.E555FE9B
Content-Type: text/plain; charset=iso-8859-1
Content-Disposition: inline
Content-Transfer-Encoding: 8bit

Spam detection software, running on the system "Frask.Server", has
identified this incoming email as possible spam.  The original message
has been attached to this so you can view it (if it isn't spam) or label
similar future email.  If you have any questions, see
@@CONTACT_ADDRESS@@ for details.

Content preview:  Buy GUARANTEED Facebook Likes/Fans, at the cheapest prices
   and become more popular! - Safely delivered, absolutely no risk! - Order
  processed within 24 hours or less! - Manually Promoted by experts not bots/software
   involved - High-Quality service. [...] 

Content analysis details:   (6.5 points, 5.0 required)

 pts rule name              description
---- ---------------------- --------------------------------------------------
 1.8 SUBJECT_FUZZY_CHEAP    Attempt to obfuscate words in Subject:
-0.0 T_RP_MATCHES_RCVD      Envelope sender domain matches handover relay
                            domain
-0.0 SPF_PASS               SPF: sender matches SPF record
 1.7 URIBL_DBL_SPAM         Contains an URL listed in the DBL blocklist
                            [URIs: advertise-bzs.net]
 1.7 URIBL_WS_SURBL         Contains an URL listed in the WS SURBL blocklist
                            [URIs: advertise-bzs.net]
 1.3 GAPPY_SUBJECT          Subject: contains G.a.p.p.y-T.e.x.t



------------=_537FACCD.E555FE9B
Content-Type: message/rfc822; x-spam-type=original
Content-Description: original message before SpamAssassin
Content-Disposition: inline
Content-Transfer-Encoding: 8bit

Return-Path: <pwthomas95@satx.rr.com>
X-Original-To: [email]admin@twprogrammers.com[/email]
Received: from cdptpa-oedge-vip.email.rr.com (cdptpa-outbound-snat.email.rr.com [107.14.166.229])
	by mail.twprogrammers.com (Postfix) with ESMTP id F384C50FC9
	for <admin@twprogrammers.com>; Fri, 23 May 2014 15:17:11 -0500 (CDT)
Received: from [70.114.11.49] ([70.114.11.49:54410] helo=[192.168.1.30])
	by cdptpa-oedge01 (envelope-from <pwthomas95@satx.rr.com>)
	(ecelerity 3.5.0.35861 r(Momo-dev:tip)) with ESMTP
	id B5/19-31957-7CCAF735; Fri, 23 May 2014 20:17:11 +0000
Message-ID: <537FACDC.408@satx.rr.com>
Date: Fri, 23 May 2014 15:17:32 -0500
From: Patrick <pwthomas95@satx.rr.com>
Reply-To: #1 Social Marketing <mike.sfsd4f564s6df45dsgala@gmail.com>
Organization: Timberwolf Programmers
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:24.0) Gecko/20100101 Thunderbird/24.5.0
MIME-Version: 1.0
To: [email]admin@twprogrammers.com[/email]
Subject: C h e a p - F a c e b o o k - F a n s
X-Enigmail-Version: 1.6
Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit
X-RR-Connecting-IP: 107.14.168.118:25
X-Cloudmark-Score: 0

Buy GUARANTEED Facebook Likes/Fans, at the cheapest prices and become
more popular!

- Safely delivered, absolutely no risk!
- Order processed within 24 hours or less!
- Manually Promoted by experts  not bots/software involved
- High-Quality service.

We offer different packages at different prices.
USA Fans / English speaking worldwide fans.


For Full Details please visit our website:
[http://www.advertise-bzs.net/facebook/](http://www.advertise-bzs.net/facebook/)











Unsubscribe option available on the footer of our website





------------=_537FACCD.E555FE9B-- 

---

### Post by SeijiSensei on 2014-05-25
How about creating an empty report?  Following [this](http://kb.mediatemple.net/questions/1369/How+do+I+change+the+SpamAssassin+template+for+messages+recognized+as+spam%3F#dv), perhaps if you add
```

clear_report_template
report

```
you can get an empty template.  You might try just using "clear_report_template" without any "report" lines as well.

---

### Post by wolfgentleman on 2014-05-25
> **SeijiSensei said:**
> How about creating an empty report?  Following [this]("http://kb.mediatemple.net/questions/1369/How+do+I+change+the+SpamAssassin+template+for+messages+recognized+as+spam%3F#dv"), perhaps if you add
```

clear_report_template
report

```
you can get an empty template.  You might try just using "clear_report_template" without any "report" lines as well.
Well, that's better than before, but it's still not quiet "unmodified".
> 

C h e a p - F a c e b o o k - F a n s.eml[HR][/HR]

[TABLE="class: header-part1, width: 100%"]
[TR]
[TD]Subject: 
C h e a p - F a c e b o o k - F a n s[/TD]
[/TR]
[TR]
[TD]From: 
REMOVED <REMOVED@satx.rr.com>[/TD]
[/TR]
[TR]
[TD]Date: 
5/25/2014 3:17 PM[/TD]
[/TR]
[/TABLE]
[TABLE="class: header-part2, width: 100%"]
[TR]
[TD]To: 
[EMAIL="admin@twprogrammers.com"]admin@twprogrammers.com[/EMAIL][/TD]
[/TR]
[/TABLE]

> [FONT=-moz-fixed]The original message was not completely plain text, and may be unsafe to[/FONT][FONT=-moz-fixed]open with some email clients; in particular, it may contain a virus,
or confirm that your address can receive spam.  If you wish to view
it, it may be safer to save it to a file and open it with an editor.

[/FONT]

ForwardedMessage.eml[HR][/HR]

[TABLE="class: header-part1, width: 100%"]
[TR]
[TD]Subject: 
Boost your Rankings with our High PR Dofollow Backlinks[/TD]
[/TR]
[TR]
[TD]From: 
"Cheap SEO Packs" <mike.sfsd4f564s6df45dsva@gmail.com>[/TD]
[/TR]
[TR]
[TD]Date: 
5/25/2014 2:38 PM[/TD]
[/TR]
[/TABLE]
[TABLE="class: header-part2, width: 100%"]
[TR]
[TD]To: 
<info@twprogrammers.com>[/TD]
[/TR]
[/TABLE]

Then the original message.

---

### Post by SeijiSensei on 2014-05-29
I'm afraid I'm out of ideas here.  Have you considered posting to the spamassassin-users mailing list?

As we may have discussed before, I use [MailScanner]("http://www.mailscanner.info/") for these tasks.  It creates an additional header with the SA scores but does not modify the message body.
```

X-MailScanner-SpamCheck: not spam, SpamAssassin (notcached, score=2.465,
	required 4, BAYES_60 1.50, SPF_SOFTFAIL 0.67, TO_NO_REAL_NAME 0.30)
X-MailScanner-SpamScore: ss

```

---

### Post by wolfgentleman on 2014-05-29
> **SeijiSensei said:**
> I'm afraid I'm out of ideas here.  Have you considered posting to the spamassassin-users mailing list?
OK, well thank you for your time. I think I will use the mailing list and post the solution here, if any, so thanks for suggesting it.

> **SeijiSensei said:**
> 
As we may have discussed before, I use [MailScanner]("http://www.mailscanner.info/") for these tasks.  It creates an additional header with the SA scores but does not modify the message body.
```

X-MailScanner-SpamCheck: not spam, SpamAssassin (notcached, score=2.465,
	required 4, BAYES_60 1.50, SPF_SOFTFAIL 0.67, TO_NO_REAL_NAME 0.30)
X-MailScanner-SpamScore: ss

```
I'm just hesitant about changing it, because I just got it up and running.

---

### Post by wolfgentleman on 2014-06-02
I posted to the SpamAssassin mailing list as suggested and I got my answer!
```
report_safe 0
```

---

