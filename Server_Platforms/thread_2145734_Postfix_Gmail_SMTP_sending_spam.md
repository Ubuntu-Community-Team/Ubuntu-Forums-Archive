---
title: "Postfix Gmail SMTP sending spam"
date: 2013-05-16
forum: Server Platforms
---

### Post by alienprdkt on 2013-05-16
First let me start off that I am running Zentyal 3.0 (have wrote to their forums as well without any luck :(, so here I am :)

I had recently encountered an issue where my server was sending out replies to all of my retrieved email via imap from Gmail. Nothing but an error was being sent here was an email that one of my coworkers sent me:

```
[COLOR=#000000][FONT=dejavu sans mono]from:[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono] Mail Delivery System <info@nexwrx.com>[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]to:[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono] email_feedback_handler@mta-inbound.cluster3.convio.net[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]date:[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono] Tue, May 14, 2013 at 8:36 AM[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]subject:[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono] Undelivered Mail Returned to Sender[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=dejavu sans mono]This is the mail system at host LAMP1.NEXWRX.LOCAL.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]I'm sorry to have to inform you that your message could not[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]be delivered to one or more recipients. It's attached below.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]For further assistance, please send mail to postmaster.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]If you do so, please include this problem report. You can[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]delete your own text from the attached returned message.[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]                   The mail system[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]<jmituzas@nexwrx.local>: delivery temporarily suspended: lost connection with[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    127.0.0.1[127.0.0.1] while receiving the initial server greeting[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Final-Recipient: rfc822; jmituzas@nexwrx.local[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Original-Recipient: rfc822;jmituzas@nexwrx.local[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Action: failed[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Status: 4.4.2[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Diagnostic-Code: X-Postfix; delivery temporarily suspended: lost connection[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    with 127.0.0.1[127.0.0.1] while receiving the initial server greeting[/FONT][/COLOR]
```

here was the attached header
```
[COLOR=#000000][FONT=dejavu sans mono]Return-Path: <email_feedback_handler@mta-inbound.cluster3.convio.net>[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from localhost (localhost.localdomain [127.0.0.1])[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]by LAMP1.NEXWRX.LOCAL (Postfix) with ESMTP id 8A9971505AC[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]for <jmituzas@nexwrx.local>; Thu,  9 May 2013 08:18:10 -0400 (EDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Virus-Scanned: by amavisd-new-2.6.5 (20110407) (Debian) at NEXWRX.LOCAL[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Spam-Flag: NO[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Spam-Score: 0.973[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Spam-Level: [/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Spam-Status: No, score=0.973 required=5 tests=[HTML_MESSAGE=0.001,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]RCVD_IN_DNSWL_NONE=-0.0001, SPF_SOFTFAIL=0.972] autolearn=no[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from LAMP1.NEXWRX.LOCAL ([127.0.0.1])[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]by localhost (LAMP1.NEXWRX.LOCAL [127.0.0.1]) (amavisd-new, port 10024)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]with ESMTP id aeRgpvnX5Fkp for <jmituzas@nexwrx.local>;[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]Thu,  9 May 2013 08:18:06 -0400 (EDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from LAMP1.NEXWRX.LOCAL (localhost.localdomain [127.0.0.1])[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]by LAMP1.NEXWRX.LOCAL (Postfix) with ESMTP id 2C83D15037F[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]for <[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]BLANKFORSECURITY[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]@nexwrx.local>; Thu,  9 May 2013 08:01:54 -0400 (EDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Delivered-To: m.nexwrx@gmail.com[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from qc-in-f108.1e100.net [173.194.76.108][/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]by LAMP1.NEXWRX.LOCAL with IMAP (fetchmail-6.3.21)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]    [/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]for <[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]BLANKFORSECURITY[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]@nexwrx.local> (single-drop); Thu, 09 May 2013 08:01:54 -0400 (EDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: by 10.58.171.41 with SMTP id ar9csp80852vec; Tue, 19 Mar 2013[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] 14:09:04 -0700 (PDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Received: by 10.220.103.7 with SMTP id i7mr4736413vco.7.1363727343974; Tue,[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] 19 Mar 2013 14:09:03 -0700 (PDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from mail-24-ewr.dyndns.com (mxout-032-ewr.mailhop.org.[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] [216.146.33.32]) by mx.google.com with ESMTP id[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] e9si18182922vcp.11.2013.03.19.14.09.03; Tue, 19 Mar 2013 14:09:03 -0700 (PDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received-SPF: softfail (google.com: domain of transitioning[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] email_feedback_handler@mta-inbound.cluster3.convio.net does not designate[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] 216.146.33.32 as permitted sender) client-ip=216.146.33.32;[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Authentication-Results: mx.google.com; spf=softfail (google.com: domain of[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] transitioning email_feedback_handler@mta-inbound.cluster3.convio.net does not[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] designate 216.146.33.32 as permitted sender)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] smtp.mail=email_feedback_handler@mta-inbound.cluster3.convio.net[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from scan-21-ewr.mailhop.org (scan-21-ewr.local [10.0.141.243]) by[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] mail-24-ewr.dyndns.com (Postfix) with ESMTP id B01515CBFA4 for[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] <BLANKFORSECURITY@nexwrx.com>; Tue, 19 Mar 2013 21:09:03 +0000 (UTC)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Mail-Handler: MailHop by DynDNS[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Originating-IP: 69.48.252.163[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from mta-c3poola1.cluster3.convio.net[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] (mta-c3poola1.cluster3.convio.net [69.48.252.163]) by mail-24-ewr.dyndns.com[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] (Postfix) with ESMTP id 6407E5CED2D for <BLANKFORSECURITY@nexwrx.com>; Tue, 19 Mar[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] 2013 21:08:59 +0000 (UTC)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Received: from 10.0.31.217 (10.0.31.59) by mta-c3poola1.cluster3.convio.net id[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] h939um1argke for <[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]BLANKFORSECURITY[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]@nexwrx.com>; Tue, 19 Mar 2013 16:08:56 -0500[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] (envelope-from <email_feedback_handler@mta-inbound.cluster3.convio.net>)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Message-ID: <13499914.1363727336316.JavaMail.www@app339>[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Date: Tue, 19 Mar 2013 15:59:24 -0500 (CDT)[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]From: TechSoup By the Cup <btc@e.techsoup.org>[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Reply-To: TechSoup By the Cup <btc@e.techsoup.org>[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]To: BLANKFORSECURITY@nexwrx.com[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Subject: Windows MultiPoint Server; Libraries on the Edge; Reach for the Cloud[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Mime-Version: 1.0[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Content-Type: multipart/alternative;[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono] boundary="----=_Part_9884711_7948315.1363727336315"[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]Organization: TechSoup Global[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-campaignid: Convio-poola-tsg-17041[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-Gateway: c3poola1[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]XData: 1010,4Myn4eQ@4KKQ4@Kyt4@i-Wwjq-e[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]X-ConvioDeliveryGroup: poola[/FONT][/COLOR]
```

I have deleted the user, and stopped postfix but when I had restarted my mailq was piling up 2 per second with replies from emails. Virus? Maybe, I have no idea.

anyways it was sending out hundreds of these per hour (surprised I didn't get blacklisted!)

After hrs of trying to resolve the issue I have decided to do a fresh install of the server. Question is how can I prevent something like this from happening again.

[COLOR=#000000][FONT=Helvetica]Looks like a fresh install tonight since I can't figure out how to start postfix without it sending replies to every email that was retrieved!?[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Any ideas on how I can prevent something like this from happening again would be greatly "ungodly" appreciated![/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Thanks in advance[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-05-16
The traffic you're seeing is likely a bunch of nondeliverable replies from the servers to which the spam messages were sent.  It will subside.

As for not allowing this to happen again, you should configure Postfix to accept only mail intended for your domain.

---

