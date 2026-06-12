---
title: "How to enable sendmail to handle large attachment sizes"
date: 2013-04-10
forum: Server Platforms
---

### Post by hash4all on 2013-04-10
Expert,

How to enable smtp/sendmail to handle large attachment sizes?
What are the sendmail options available to set this?

Any one is there to reply.

Thanks

---

### Post by SeijiSensei on 2013-04-10
In sendmail.cf, look for the MaxMessageSize directive.  If it's set to zero, there is no limit.

---

