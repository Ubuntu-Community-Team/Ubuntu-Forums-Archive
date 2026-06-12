---
title: "Dkim and Domainkeys"
date: 2010-05-02
forum: Server Platforms
---

### Post by fortune2008 on 2010-05-02
this is my mail header

```
From admin@chatalker.com Sun May  2 18:31:03 2010
X-Apparently-To: fortune.osei@yahoo.com via 68.180.199.120; Sun, 02 May 2010 11:31:06 -0700
Return-Path: <admin@chatalker.com>
X-YahooFilteredBulk: 190.93.75.216
X-YMailISG: YeGc1E4WLDvEWuk8vdk6n1hgKjPHx.0tKYmpFORf7.8eDtZ8_PNpOvIoKnszUDUl_cNvW9bbUzsqVMb7zhEMhx9XLBNYiNngkT6p74oQNH0I44Ixbo4_Itfy_2N_Uiqrv_xYzFG6xO9vt52Ep28PMuEVKQEyrf3a4GR_rNhmSBXGgTyytf1yL32GeFBulU4O0wip4Ovje3D3gzd35K2aCEZXZANv2ufzvdeCF4R3GznBEByv1AOJD573xJNb0x6gZinW1boibVlzF4O0MguDCGdekLoAJHuTCVIJ0_kr
X-Originating-IP: [190.93.75.216]
Authentication-Results: mta140.mail.ac4.yahoo.com  from=chatalker.com; domainkeys=neutral (no sig);  from=chatalker.com; dkim=pass (ok)
Received: from 127.0.0.1  (EHLO server1.chatalker.com) (190.93.75.216)
  by mta140.mail.ac4.yahoo.com with SMTP; Sun, 02 May 2010 11:31:06 -0700
Received: from localhost (localhost [127.0.0.1])
    by server1.chatalker.com (Postfix) with ESMTP id 5CB71E02BF
    for <fortune.osei@yahoo.com>; Sun,  2 May 2010 14:31:04 -0400 (AST)
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/simple; d=chatalker.com; h=
    content-transfer-encoding:content-type:content-type:mime-version
    :user-agent:from:from:subject:subject:date:date:message-id
    :received:received:received; s=mail; t=1272825063; x=1274639463;
     bh=frcCV1k9oG9oKj3dpUqdJg1PxRT2RSN/XKdLCPjaYaY=; b=CnlyOnz4368Q
    UMhWFg3dtIKoUML203Q1w7higEQeWVCnMqQaiGS72ofpDtj0AN/o0Kn5Ffy3szLM
    tdA1aGiRrCv5hocTcVWj31q+wKuVvyhdAIxGeKY/n79ubnKpfw28ZoJtN0DXK1Be
    moCFntruBgswhg7ixvA1J/opUT2zCBE=
X-Virus-Scanned: Debian amavisd-new at server1.chatalker.com
Received: from server1.chatalker.com ([127.0.0.1])
    by localhost (server1.chatalker.com [127.0.0.1]) (amavisd-new, port 10024)
    with ESMTP id QIHBZuNqXro7 for <fortune.osei@yahoo.com>;
    Sun,  2 May 2010 14:31:03 -0400 (AST)
Received: from [192.168.10.52] (localhost [127.0.0.1])
    by server1.chatalker.com (Postfix) with ESMTP id C58BDE02BD
    for <fortune.osei@yahoo.com>; Sun,  2 May 2010 14:31:03 -0400 (AST)
Received: from 192.168.10.6
        (SquirrelMail authenticated user admin@chatalker.com)
        by 192.168.10.52 with HTTP;
        Sun, 2 May 2010 14:31:03 -0400
Message-ID: <8d7b1fe3fe6e92503cb9ef1cfe8fe331.squirrel@192.168.10.52>
Date: Sun, 2 May 2010 14:31:03 -0400
Subject: hit
From: admin@chatalker.com
To: fortune.osei@yahoo.com
User-Agent: SquirrelMail/1.4.19
MIME-Version: 1.0
Content-Type: text/plain;charset=iso-8859-1
Content-Transfer-Encoding: 8bit
X-Priority: 3 (Normal)
Importance: Normal
Content-Length: 2

```

i cant get the domainkeys to be signed i used amavis to sign dkim

---

