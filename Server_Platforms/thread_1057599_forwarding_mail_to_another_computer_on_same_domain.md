---
title: "forwarding mail to another computer on same domain"
date: 2009-02-02
forum: Server Platforms
---

### Post by eatloaf on 2009-02-02
First off, I understand very little about mail servers.  I am hoping someone can help me figure out why my mail worked properly on my 8.04 system but not on my current 8.10 system.

I had to do a fresh install.  This is not an upgrade.

Running sendmail, I had it forward my local mail to my regular email account.  I can no longer get it to do this.  It gets sent out but doesn't bounce and doesn't arrive.

This is a header from a mail that forwarded properly back when it worked, in case it's a clue as to how it was working:

```

Return-Path: <root@masqueraded-domain.net>
Delivery-Date: Mon, 26 Jan 2009 06:36:53 -0500
Received: from ubuntu_box (xxx.tukw.qwest.net [xx.xx.xx.xx])
	by mx.perfora.net (node=mxus2) with ESMTP (Nemesis)
	id 0MKobQ-1LRPlg0CPd-0001Du for [email]eatloaf@yahoo.com[/email]; Mon, 26 Jan 2009 06:36:53 -0500
Received: from ubuntu_box (localhost [127.0.0.1])
	by ubuntu_box (8.14.2/8.14.2/Debian-2build1) with ESMTP id n0QBa6kd012089
	for <eatloaf@ubuntu_box>; Mon, 26 Jan 2009 03:36:20 -0800
Received: (from root@localhost)
	by ubuntu_box (8.14.2/8.14.2/Submit) id n0QBa5EM012084
	for eatloaf; Mon, 26 Jan 2009 03:36:06 -0800
Date: Mon, 26 Jan 2009 03:36:06 -0800
From: root <root@masqueraded-domain.net>
Message-Id: <200901261136.n0QBa5EM012084@ubuntu_box>
To: eatloaf@ubuntu_box
Subject: [ubuntu_box backup log: eatloaf]
Envelope-To: [email]eatloaf@yahoo.com[/email]

```

I set the masquerading in the new sendmail configuration but I don't recall changing anything else and I don't see any evidence of any other changes when I browse the old 8.04 sendmail configuration files.

Can anyone tell me what I'm missing in my new system?

---

### Post by HermanAB on 2009-02-02
Use nullmailer.  It is a simple as it gets.  

Sendmail is for masochists only.

Cheers,

Herman

---

