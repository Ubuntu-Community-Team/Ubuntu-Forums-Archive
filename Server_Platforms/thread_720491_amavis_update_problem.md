---
title: "amavis update problem"
date: 2008-03-10
forum: Server Platforms
---

### Post by prodsacnetworking on 2008-03-10
-Hi, 

I updated my mail server (Ubuntu 6.06LTS, Postfix (flurdy's installation)

and now, when client receives emails from their website (php mail) the email is flagged as bad header and in the email it's: 

any ideas??



X-Amavis-Alert: BAD HEADER MIME error: error: unexpected end of preamble

:
:
:
:
Return-Path: <apache@www.domain.com>
X-Original-To: [email]info@domain.com[/email]
Delivered-To: [email]user@domain.com[/email]
Received: from localhost (localhost [127.0.0.1])
	by mail.domain.com (Postfix) with ESMTP id 581FBD9C35C
	for <info@domain.com>; Mon, 10 Mar 2008 11:28:53 -0400 (EDT)
Received: from mail.domain.com ([127.0.0.1])
	by localhost (morpheus.domain.com [127.0.0.1]) (amavisd-new, port 10024)
	with ESMTP id 02727-03 for <info@domain.com>;
	Mon, 10 Mar 2008 11:28:53 -0400 (EDT)
Received: from smith.domain.com (smith.prodsacnetworking.com [XX.XXX.XXX.3])
	by mail.domain.com (Postfix) with ESMTP id 271C6D9C308
	for <info@domain.com>; Mon, 10 Mar 2008 11:28:53 -0400 (EDT)
Received: by smith.domain.com (Postfix, from userid 80)
	id E41B9102390; Mon, 10 Mar 2008 11:28:52 -0400 (EDT)
To: [email]info@domain.com[/email]
Subject: =?UTF-8?B?U3VnZ8OocmVyIHVuIGxpZW4=?=
From: Eric<user@domain.com>
Reply-To: Eric<user@domain.com>
Message-ID: < [email]TheSystem@www.domain.qc.ca[/email]>
X-Mailer: PHP v5.2.0
MIME-Version: 1.0
Content-Type: multipart/related; boundary="78868564e42b92115b71ea9fea1956b2"
Mime-Version: 1.0
Content-Transfer-Encoding: BASE64
Date: Mon, 10 Mar 2008 11:28:52 -0400 (EDT)
X-Amavis-Alert: BAD HEADER MIME error: error: unexpected end of preamble

LS03ODg2ODU2NGU0MmI5MjExNWI3MWVhOWZlYTE5NTZiMg0KQ29udGVudC1UeXBlOiBtdWx0aXBh
cnQvYWx0ZXJuYXRpdmU7IGJvdW5kYXJ5PSI3ODg2ODU2NGU0MmI5MjExNWI3MWVhOWZlYTE5NTZi
Ml9odG1sYWx0Ig0KLS03ODg2ODU2NGU0MmI5MjExNWI3MWVhOWZlYTE5NTZiMl9odG1sYWx0DQpD
b250ZW50LVR5cGU6IHRleHQvaHRtbDsgY2hhcnNldD1pc28tODg1OS0xDQpDb250ZW50LVRyYW5z
ZmVyLUVuY29kaW5nOiA4Yml0DQo8aHRtbD48dGFibGU+PHRyPjx0ZCBjb2xzcGFuPTI+PGI+TXVu
aWNpcGFsaXTDqSBkZSBNYW5kZXZpbGxlPC9iPjwvdGQ+PC90cj48dHI+PHRkIGNvbHNwYW49Mj4m
bmJzcDs8L3RkPjwvdHI+PHRyPjx0ZCBhbGlnbj1yaWdodCB3aWR0aD0xODA+PGI+Tm9tICA6PC9i
PjwvdGQ+PHRkPkVyaWM8L3RkPjwvdHI+PHRyPjx0ZCBhbGlnbj1yaWdodD48Yj5BZHJlc3NlIMOp
bGVjdHJvbmlxdWUgOjwvYj48L3RkPjx0ZD48YSBocmVmPW1haWx0bzplbWlsbG1vcmVAcXVlYmVj
ZGV2LmNvbT5lbWlsbG1vcmVAcXVlYmVjZGV2LmNvbTwvYT48L3RkPjwvdHI+PHRyPjx0ZCBhbGln
bj1yaWdodD48Yj5TdWpldCA6PC9iPjwvdGQ+PHRkPlN1Z2fDqHJlciB1biBsaWVuPC90ZD48L3Ry
Pjx0cj48dGQgYWxpZ249cmlnaHQgdmFsaWduPXRvcD48Yj5NZXNzYWdlIDo8L2I+PC90ZD48dGQ+
dGVzdDxiciAvPgo8YnIgLz4KZHNmPGJyIC8+CkY8YnIgLz4KU0RGPGJyIC8+CkRGPC90ZD48L3Ry
PjwvdGFibGU+PC9odG1sPg0KDQotLTc4ODY4NTY0ZTQyYjkyMTE1YjcxZWE5ZmVhMTk1NmIyX2h0
bWxhbHQtLQ0KDQotLTc4ODY4NTY0ZTQyYjkyMTE1YjcxZWE5ZmVhMTk1NmIyLS0NCg0K

---

### Post by MJN on 2008-03-10
Can you post some more samples? Preferably without any encoding?

The header is suggesting a multipart message, but the body is not.

Mathew

---

### Post by Mr. C. on 2008-03-11
Amavis alerts on various bad headers.  It is safe to ignore, or you can disable that notifications in amavis.

---

