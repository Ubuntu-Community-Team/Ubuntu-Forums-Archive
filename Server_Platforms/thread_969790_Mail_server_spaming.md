---
title: "Mail server spaming?"
date: 2008-11-03
forum: Server Platforms
---

### Post by kpzani on 2008-11-03
Hi all

I have a hardy server running postfix.  It doesnt accept smtp connections from outside my network and collects mail from my isp via fetchmail.  I have had a few emails which look like they come from my server 

headers -
```

Return-Path: <buk@bradleymotivation.com>
X-Original-To: kriszani@localhost
Delivered-To: kriszani@localhost
Received: from dumbledore.hogwarts.local (localhost [127.0.0.1])
	by dumbledore.hogwarts.local (Postfix) with ESMTP id 89D2DCB62C5
	for <kriszani@localhost>; Mon,  3 Nov 2008 22:06:48 +0000 (GMT)
Envelope-to: kriszani@iscavision.com,
 kriszani@iscavision.com
Delivery-date: Mon, 03 Nov 2008 22:06:01 +0000
Received: from tintern2.dsvr.co.uk [212.69.199.79]
	by dumbledore.hogwarts.local with POP3 (fetchmail-6.3.8)
	for <kriszani@localhost> (single-drop); Mon, 03 Nov 2008 22:06:48 +0000 (GMT)
Received: from [85.172.49.228] (helo=home-dbd219661e)
	by tintern2.dsvr.co.uk with esmtp (Exim 4.62)
	(envelope-from <buk@bradleymotivation.com>)
	id 1Kx7YH-0005Xz-Uo; Mon, 03 Nov 2008 22:06:01 +0000
Received: from [85.172.49.228] by inbound.homesteadmail.com; Mon, 3 Nov 2008 14:05:36 -0800
Message-ID: <01c93dbd$3e4b3800$e431ac55@buk>
From: PayPal@dumbledore.hogwarts.local, service@intl.paypal.x.com
To: <kriszani@iscavision.com>
Subject: Getting Started with your PayPal Anti-Fraud Protection
Date: Mon, 3 Nov 2008 14:05:36 -0800
MIME-Version: 1.0
Content-Type: multipart/alternative;
	boundary="----=_NextPart_000_0007_01C93DBD.3E4B3800"
X-Priority: 3
X-MSMail-Priority: Normal
X-Mailer: Microsoft Outlook Express 6.00.2900.2180
X-MimeOLE: Produced By Microsoft MimeOLE V6.00.2900.2180
Delivered-To: kriszani@tintern2.dsvr.co.uk

This is a multi-part message in MIME format.

------=_NextPart_000_0007_01C93DBD.3E4B3800
Content-Type: text/plain;
	charset="us-ascii"
Content-Transfer-Encoding: quoted-printable

```

my server's hostname is dumbledore.hogwarts.local

so my question is, does the guy sending this know what my server name is already.  or is it likely that postfix or fetchmail sees a malformed address e.g. Paypal and sticks the domain name on the end.

all comments appreciated.

Kris

---

### Post by lavinog on 2008-11-03
I am guessing it was automatically attached. I wonder why though. It seems that it will cause problems for spam blockers.

---

### Post by kpzani on 2008-11-04
yup that was my gut instinct too.  but it's purely a guess.

any ideas how i could check the logs for this.

i looked in the mail.info but all i see is two related lines as its passed to me from fetchmail.

cheers

Kris

---

