---
title: "Postfix can recieve email - cant send"
date: 2008-12-31
forum: Server Platforms
---

### Post by ttallos on 2008-12-31
I can recieve email just fine from postfix but I cant send any email the message says sent successfully but I never get the email. I can telnet into mydomain.com using port 25 but I cant telnet into port 110? Is there another port? I am sure this is a simple configuration issue. I have dns set up with bind A, Reverse, MX records all set. I use webmin. Any help would be appriecated.

---

### Post by amauk on 2008-12-31
25 - plain SMTP (unencrypted)
465 - SMTP over SSL
587 - SMTP over TLS (successor to SSL)

---

### Post by ttallos on 2008-12-31
> **amauk said:**
> 25 - plain SMTP (unencrypted)
465 - SMTP over SSL
587 - SMTP over TLS (successor to SSL)

Port 25 works to recieve but I cant send with any success even though there is a message successful message after sending. I cant telnet into any of the other ports that you list except port 25.

---

