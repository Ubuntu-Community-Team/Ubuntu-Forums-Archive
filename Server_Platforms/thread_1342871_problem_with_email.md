---
title: "problem with email"
date: 2009-12-01
forum: Server Platforms
---

### Post by ishfady on 2009-12-01
Hi

I am very new to Ubuntu and try to learn mail system.
I have install Webmin and it is working fine. I can log into my server from other pc.
I am sending test mail to myself on yahoo account.
When I send mail through webmin, it say, mail send successfully, but I m not receiving into my yahoo account.

Please can someone advice, where I am going wrong.

Many thank

---

### Post by weemadarthur on 2009-12-01
Haven't used webmin, but there are a couple of things you can check.

1. Does your ISP allow outbound connections on port 25? Some ISPs don't allow these connections to cut down on spam.
2. Look at /var/log/maillog. There should be some info there which will help you debug the problem.

---

