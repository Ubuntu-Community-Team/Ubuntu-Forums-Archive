---
title: "Server Load: Outlook vs Webmail"
date: 2008-01-30
forum: Server Platforms
---

### Post by quietas on 2008-01-30
I've got a mail server I've inherited adminship of and I'm wondering if anyone knows the server load overhead of using Outlook vs webmail.

Courier Imap
PHPGroupware
PHP4
Apache2
150 users internal and external

Any ideas?

---

### Post by Yhetti on 2008-01-30
In general, POP3, IMAP, SMTP are going to be less load than a web frontend.  That's not always the case, but it's a safe bet.  With mail protocols, the client does all the heavy lifting while the server is really only a glorified database lookup; via webmail, the server does all the heavy lifting *and* all the data lookup.

---

### Post by foxylad on 2008-01-30
Of course, you can outsource all that heavy lifting to Google Mail...

---

### Post by hkgonra on 2008-01-30
> **foxylad said:**
> Of course, you can outsource all that heavy lifting to Google Mail...

+1 !!!!

---

