---
title: "Postfix block spam from email@mydomain from unknown ip"
date: 2016-05-03
forum: Server Platforms
---

### Post by Seb_Boffen on 2016-05-03
I would like to block spam being sent with my domain from an unknown ip address. At the moment my postfix amavis configuration accepts these messages.

Example:

Return-Path: <email@mydomain>
X-Original-To: email@mydomain
Delivered-To: email@mydomain
Received: from localhost (localhost [127.0.0.1])
 by server.mydomain (Postfix) with ESMTP id 3C0F5480BB5
 for <email@mydomain>; Tue,  3 May 2016 16:16:57 +0200 (CEST)
X-Quarantine-ID: <0GbVUQ0mu3cv>
X-Virus-Scanned: Debian amavisd-new at server.mydomain 
X-Amavis-Alert: BAD HEADER SECTION, MIME error: error: part did not end with
 expected boundary
X-Spam-Flag: NO
X-Spam-Score: 5.557
X-Spam-Level: *****
X-Spam-Status: No, score=5.557 tagged_above=2 required=6.31
 tests=[HTML_MESSAGE=0.001, RCVD_IN_PBL=3.558, RCVD_IN_XBL=0.724,
 RDNS_NONE=1.274] autolearn=no autolearn_force=no
Received: from server.mydomain ([127.0.0.1])
 by localhost (server.mydomain [127.0.0.1]) (amavisd-new, port 10024)
 with ESMTP id 0GbVUQ0mu3cv for <email@mydomain>;
 Tue,  3 May 2016 16:16:55 +0200 (CEST)
Received: from [115.178.199.112] (unknown [115.178.199.112])
 by server.mydomain (Postfix) with ESMTP id 56C66480F12
 for <>email@mydomain; Tue,  3 May 2016 16:16:40 +0200 (CEST)
MIME-Version: 1.0
Date: Tue, 03 May 2016 21:16:59 +0700
Message-ID: <[EMAIL="A3F2389FBD8DD0075CC2288615952467CF66DE112D@boffensysteembeheer.nl"]A3F2389FBD8DD0075CC2288615952467CF66DE112D@_[COLOR=#0066cc]mydomain[/COLOR]_[/EMAIL]>
Subject: New Doc 145 Page 2
From: CamScanner <email@mydomain>
To: <email@mydomain>
Content-Type: multipart/mixed; boundary=f191a4ea46f2690866f4311cc541

I think its resolved by removing my local lan ip range from mynetworks = 127.0.0.0/8 in main.cf

---

