---
title: "Duplicated emails in Postfix"
date: 2009-03-24
forum: Server Platforms
---

### Post by shirley_o on 2009-03-24
Hi,

I'm having problem with receiving duplicated emails. This happens only for a few random external senders. I am using Postfix and Amavisd-new. Upon checking the mail header, I can see that there is a delay:

[FONT="Courier New"]Received:  from localhost (ip6-localhost [127.0.0.1])	by reinjection.xxx (Postfix) with ESMTP id 21C2A6A0DE	for <xxx>; Tue, 24 Mar 2009 12:49:11 +0000 (GMT)
X_Spam_Score:  5.001
X_Spam_Level:  *****
X_Spam_Status:  No, score=5.001 tagged_above=-999 required=5.4	tests=[HTML_MESSAGE=0.001, RCVD_IN_DNSWL_LOW=-1, RCVD_IN_FIVETEN=3,	RCVD_IN_SPAMHAUS_PBL=3]
Received:  from xxx ([127.0.0.1])	by localhost (xxx [127.0.0.1]) (amavisd-new, port 10024)	with ESMTP id JF1XcFQHGWM7 for <xxx>;	Tue, 24 Mar 2009 12:49:07 +0000 (GMT)
Received:  from xxx (xxx [xxx])	by xxx (Postfix) with SMTP id BA5786A0D9	for <xxx>; Tue, 24 Mar 2009 12:38:49 +0000 (GMT)
Received:  (qmail 61560 invoked from network); 24 Mar 2009 12:39:24 -0000
Received:  from hxxx (HELO xxx) (pcrecycling-xxx)  by xxx with SMTP; 24 Mar 2009 12:39:24 -0000[/FONT]

I've checked the queue activity using qshape and it is healthy. Any help is much appreciated. 

Thanks.

---

