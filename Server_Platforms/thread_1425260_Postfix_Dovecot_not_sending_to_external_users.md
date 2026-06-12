---
title: "Postfix Dovecot not sending to external users"
date: 2010-03-08
forum: Server Platforms
---

### Post by schilders on 2010-03-08
Hello,
I am trying to troubleshoot a Postfix Dovecot install on a 64 bit cloud server. Telnet sends internal mail fine but not to the outside world. When my users try to POP their mail from Entourage or Outlook, they receive server cannot be found when using mail.mydomain.com. 
I have setup an OpenSSL cert and named it mailcert.pem and made the saslauthd changes. 
Has anyone else had this issue?  How did you solve it?  Does Postfix depend on MySQL or is that an optional config step?  
I greatly appreciate any/all advice. 
Thanks,
Sid

---

