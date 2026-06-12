---
title: "DKIM Problem using Linux"
date: 2018-12-18
forum: Server Platforms
---

### Post by programercek on 2018-12-18
Do you have any idea why I got:


DomainKeys Identified Mail (DKIM) is a method for associating a domain name to an email message, thereby allowing a person, role, or organization to claim some responsibility for the message.
The DKIM signature of your message is:


	v=1;
	a=rsa-sha256;
	bh=GgwwG55XSn/1OO+qRLy/+C3yYUpS8V+FRCWs1drg5Ec=;
	d=domainname.com;
	h=Message-ID:Date:Subject:From:Reply-To:To:MIME-Version:Content-Type:X-Subscriber-Id:X-Sending-Server-Id:X-Message-Id:X-Customer-Id:X-Acelle-Campaign-Id:Precedence:List-Unsubscribe;
	i=@domainname.com;
	s=mailer._domainkey;
	t=1545135303;
	b=GPwXxt6FvNSoW3JJ7td9GfIxNOUuom0xgdHYX54EcetMrJrifYLM+kVFBmUNNyNrDp9LPwNP7ZapvTZccC5B4kImsiO6uaEc1BQ6ma/CXbsGASlaIzsIrS/M+XpQnGzRtbQVhMP4w5EcCtI83LQSY381sqU9DCygK4NHll/YzKU=
We were not able to retrieve your public key.
Please ensure that you inserted your DKIM TXT DNS record on your domain domainname.com using the selector mailer._domainkey.
If you recently modified your DNS, please be patient and test again your Newsletter in 12 hours, it may take some time for the DNS to be propagated




On Windows Server I resolved using disabled antivirus on Linux I tried but I cannot found any idea. I used Postfix

---

