---
title: "What should my hostname be set to?"
date: 2007-05-28
forum: Server Platforms
---

### Post by Avicus on 2007-05-28
My server is acting as a webserver for 2 domains, and forwards email for both domains to external email addresses. What should my /etc/hosts and /etc/hostname be set to? 

The reason I'm asking is because some of the emails that are forwarded are being rejected and the best reason I could find out why is because of this page:
[http://cbl.abuseat.org/hostname.html](http://cbl.abuseat.org/hostname.html)

Anyone able to help?

---

### Post by Mr. C. on 2007-05-28
Your hostname in /etc/hosts or /etc/hostname will not be visible to external websites.  

To relay mail, your server needs to be configured such that:

  - the name it announces itself as is the same as that posted in DNS
  - You have a proper A record for your mail server
  - The PTR record matches the IP address of your server

If your server is on a dynamic IP address, or the above are not true, many server will refuse to allow your server to relay mail.

MrC

---

