---
title: "Set up server to send email for server logs, errors etc."
date: 2009-11-09
forum: Server Platforms
---

### Post by mramsey on 2009-11-09
Ok I an trying to find a simple method for my server to send email messages to me for backup notifications , error reports etc. I am not sure how to go about it though and my searches have not returned the results I am after (at least I think ;) ) I can set up an email account if needed such as gmail or even from my ISP. I think I explained what I am after. Thanks in advance!

---

### Post by yaztromo on 2009-11-09
I did exactly this by installing exim and configuring it to use my ISPs smtp server (exim calls it an smtp smarthost) to send mail through.

Configuring exim is a pain, but the results are good. Look for some guides on smtp smarthost and exim on ubuntu/debian and that should get you going.

---

