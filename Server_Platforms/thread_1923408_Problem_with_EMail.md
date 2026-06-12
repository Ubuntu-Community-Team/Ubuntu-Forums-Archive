---
title: "Problem with EMail"
date: 2012-02-10
forum: Server Platforms
---

### Post by goshock on 2012-02-10
I have setup a postfix server and it's been running fine for some time.  All of the sudden, starting yesterday, I am seeing about 600 messages sending out ever 12 minutes, and I cannot figure out how to stop them or figure out where they are coming from.  Here is what is in the message file:

```
CO          56799             205               1               0           
56799L^Xamavis:[127.0.0.1]:10024T^Q1328900117 
250955A^Vcreate_time=1328900117A^Urewrite_context=localF^@S^Zvhost@<fqdn pf 
server>M^@N=Received: by <fqdn of server> (Postfix, from userid 5008)N6   id 4BFBB1A87BD; Fri, 
10 Feb 2012 10:55:17 -0800 (PST)N!To: [email]moncia_denunzio@jrtrealty.comN[/email]^[Subject: 
Your Order#2161629N/From: "American Airlines" <news-nr15924@aa.com>N^]X-Mailer: 
CSWMSAutoMailer:regN3Reply-To: "American Airlines" <news-nr15924@aa.com>N^QMime-Version: 
1.0NIContent-Type:multipart/mixed;boundary="----------13289001174F356815394FB"N=Message-Id: 
<20120210185517.4BFBB1A87BD@<fdqn of server>>N+Date: Fri, 10 Feb 2012 10:55:17 -0800 
(PST)N^@N^@N^@N#------------13289001174F356815394FBN^WContent-Type:text/html;N^_Content-
Transfer-Encoding: 8bitN^@N
```


Any pointer on how to fix this would be much appreciated.

---

