---
title: "Postfix receive from headers"
date: 2010-04-08
forum: Server Platforms
---

### Post by dmrazor on 2010-04-08
Hi,

I've been succesfully running Postfix for some years now, but recently added a local DNS with a fictious domain to tidy up some loose ends.

Mailclient connecting to the internal IP address of the mailserver the first "Received: from" header used to be:
```
Received: from [192.168.1.51] (unknown [192.168.1.51])
	by stone.bluepoint.nl (Postfix) with ESMTP id 94897355
	for <pipo@hotmail.com>; Wed,  7 Apr 2010 21:22:35 +0200 (CEST)
```
With an internal DNS this has now become:
```
Received: from Received: from [192.168.1.51] (rock.bluepoint.lan [192.168.1.51])
	by stone.bluepoint.nl (Postfix) with ESMTP id 9B763E86
	for <pipo@hotmail.com>; Wed,  7 Apr 2010 22:13:18 +0200 (CEST)

```
My question is how to interpret the "[FONT="Courier New"]Received: from [192.168.1.51 ] (rock.bluepoint.lan [192.168.1.51])[/FONT]" header, and especially why the first occurance of the [192.168.1.51] IP-address isn't resolved to a dns-name, where the mailer is clearly able to do both forward and reverse lookups.

Shouldn't the header be "[FONT="Courier New"]Received: from rock.bluepoint.lan (rock.bluepoint.lan [192.168.1.51])[/FONT]"? What's the information that's actually being given in the different parts of such a "received: from" header?

I find it pretty hard to locate much in depth documentation about this, hence the question in these forums. Any insights are appreciated.

Thanks,

Raz.

---

