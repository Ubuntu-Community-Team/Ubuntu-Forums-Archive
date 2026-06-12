---
title: "bcc_maps sends mails twice"
date: 2016-04-06
forum: Server Platforms
---

### Post by lukas34 on 2016-04-06
Hi
I'm using recipient_bcc_maps like that:
```
@domain.com catchall@domain.com
```
Every mail is sent twice to [email]catchall@domain.com[/email] however.
Don't really understand why...

---

### Post by lukas34 on 2016-04-07
enable_original_recipient = No in main.cf fixed it

---

