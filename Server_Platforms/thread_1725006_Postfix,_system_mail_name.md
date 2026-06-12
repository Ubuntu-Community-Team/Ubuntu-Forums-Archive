---
title: "Postfix, system mail name?"
date: 2011-04-09
forum: Server Platforms
---

### Post by rado3105 on 2011-04-09
I am trying to install postfix, but I dont understand how should look like: system mail name. I dont have installed any dns server, and server is part of local network with internet connectivity, port 25 is not blocked.

I want to send mail from my network to smtp.mynetwork.sk, so I put smtp.mynetwork.sk in the field of system mail name?

---

### Post by falko on 2011-04-09
No. Please make up a new hostname (like server1.yourdomain.com). And I really recommend that you create a DNS record for it. If this is not possible, get a hostname from dyndns.org.

BTW, if you have a dynamic IP, you should set up relaying: [http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

---

### Post by rado3105 on 2011-04-09
So I should install bind dns server, when I want all the pcs connected to my network to send emails using smtp. And there set ip of the server and bind it to: mynetwork.sk. Am I right?

---

