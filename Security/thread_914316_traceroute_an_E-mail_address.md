---
title: "traceroute an E-mail address ?"
date: 2008-09-08
forum: Security
---

### Post by Red-Shield on 2008-09-08
hello there can any one tell me if there is a way to do something close to like a **_traceroute_** or **_host_** check on an email address or trace its source i  know it comes through the server but before the server is there a way to find the real IP address of the sender ??

---

### Post by koenn on 2008-09-09
Look at the email headers. Most email clients have a menu option or a command switch to display them. 

They look like this and are to be read bottom-up, so the one furthest down the list is the initial sender:

```
Delivered-To: 	someone@somewhere	
Received: 	(qmail 12127 invoked from network); 9 Sep 2008 13:36:05 -0000	
Received: 	from hoboi2bl5.telenet-ops.be ([195.130.37.188]) (envelope-sender <Microsoft@newsletters.microsoft.com>) by vlad.telenet-ops.be (qmail-ldap-1.03) with SMTP for <someone@somewhere>; 9 Sep 2008 13:36:05 -0000	
Received: 	from asok.telenet-ops.be (asok.telenet-ops.be [195.130.137.83]) by hoboi2bl5.telenet-ops.be (8.13.1/8.13.1) with ESMTP id m89Da5Oa004964 for <someone@somewhere>; Tue, 9 Sep 2008 15:36:05 +0200	
Received: 	from ladon.telenet-ops.be (ladon.telenet-ops.be [195.130.132.50]) by asok.telenet-ops.be (Postfix) with ESMTP id 03FB960009 for <someone@somewhere>; Tue, 9 Sep 2008 15:36:05 +0200 (CEST)	
Received: 	from delivery.pens.microsoft.com (delivery.pens.microsoft.com [207.46.248.67]) by ladon.telenet-ops.be (Postfix) with ESMTP id 46686312779 for <someone@somewhere>; Tue, 9 Sep 2008 15:36:04 +0200 (CEST)	
Received: 	from TK2MSFTDDSQ15 ([10.40.249.22]) by delivery.pens.microsoft.com with Microsoft SMTPSVC(6.0.3790.1830); Tue, 9 Sep 2008 06:36:02 -0700
```

If you're using a web mail service such as gmail, I don't know if that offers this feature.

---

### Post by Red-Shield on 2008-09-09
thank you very much that dose help i use hotmail and have not found this option tho so i will contact there support i guess

---

