---
title: "Spam Problem"
date: 2007-10-22
forum: Windows
---

### Post by lsutiger on 2007-10-22
Hi all! I was wondering if you could help me out with a spam problem my company has been having.

I am currently using dyndns to filter our email, and it has helped more than I imagined.

The problem I am having is that some emails do not go through the filter, they are attaching directly to our server on port 25.

We are using Windows server 2003 smtp plugin in IIS for our smtp server and a linksys/cisco router for port forwarding/firewall.

I know I could alleviate this problem by changing the ports that the email is using (from 25 to whatever), but how do I do this without changing the port on all of the email client programs? Is there a way around this?

I tried using port triggering (outside port 2525 and inside port 25) but I could not connect to the server on either port.

Any input would be appreciated.
PS - I am attaching a mail header from the one using the filter and another that was bypassed in that order. Also, I am changing our server and email addys below

Filter
```
Received: from mhfr-06-bos.mailhop.org ([63.208.196.176]) by myserver.net with Microsoft SMTPSVC(6.0.3790.1830);
	 Tue, 25 Sep 2007 14:11:50 -0500
Received: from localhost ([127.0.0.1] helo=mhfr-06-bos.mailhop.org)
	by mhfr-06-bos.mailhop.org with esmtp (Exim 4.68)
	(envelope-from <fap@mds.petra.com>)
	id 1IaFwA-000Nry-4d
	for myemail.NET; Tue, 25 Sep 2007 15:19:14 -0400
Received: from cox-24-248-248-2-static.coxinet.net ([24.248.248.2] helo=mds.petra.com)
	by mhfr-06-bos.mailhop.org with esmtp (Exim 4.68)
	(envelope-from <fap@mds.petra.com>)
	id 1IaFw9-000Nfq-Ck; Tue, 25 Sep 2007 15:19:13 -0400
Received: (from fap@localhost)
	by mds.petra.com (AIX5.3/8.13.4/8.11.0) id l8PJHqXF532496;
	Tue, 25 Sep 2007 14:17:52 -0500
Date: Tue, 25 Sep 2007 14:17:52 -0500
From: Order Confirms <sales@petra.com>
To: anemail.NET;, anemail.NET
Subject: Order Confirmation From Petra Industries
Message-ID: <20070925191752.GA827642@petra.com>
Mime-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Disposition: inline
User-Agent: Mutt/1.5.11
X-Mail-Handler: MailHop by DynDNS
X-Originating-IP: 24.248.248.2
X-Spam-Score: 0.0 (/)
Return-Path: fap@mds.petra.com
X-OriginalArrivalTime: 25 Sep 2007 19:11:51.0265 (UTC) FILETIME=[ED816510:01C7FFA7]


```


No Filter
```
Received: from adsl-218-25-192-81.adsl.iam.net.ma ([81.192.25.218]) by ourserver.net with Microsoft SMTPSVC(6.0.3790.3959);
	 Mon, 22 Oct 2007 04:26:04 -0500
Received: from [81.192.25.218] by drkeo.bases.com; Mon, 22 Oct 2007 09:33:44 +0000
Message-ID: <000601c8148e$060d0980$287feda0@rmgtdjj>
From: "jean-lou weinrich" <amy41alun@bases.com>
To: "Armando Patton" <myemail.net>
Subject: diamond Replicas, affordable prices rolex
Date: Mon, 22 Oct 2007 07:46:21 +0000
MIME-Version: 1.0
Content-Type: text/plain;
	format=flowed;
	charset="iso-8859-1";
	reply-type=original
Content-Transfer-Encoding: 7bit
X-Priority: 3
X-MSMail-Priority: Normal
X-Mailer: Microsoft Outlook Express 6.00.3790.2663
X-MimeOLE: Produced By Microsoft MimeOLE V6.00.3790.2757
Return-Path: amy41alun@bases.com
X-OriginalArrivalTime: 22 Oct 2007 09:26:05.0859 (UTC) FILETIME=[925D4730:01C8148D]


```

---

### Post by lsutiger on 2007-10-26
Bump

---

