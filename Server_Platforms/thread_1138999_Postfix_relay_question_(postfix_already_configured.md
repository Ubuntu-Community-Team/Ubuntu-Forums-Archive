---
title: "Postfix relay question (postfix already configured and working)"
date: 2009-04-26
forum: Server Platforms
---

### Post by radekg on 2009-04-26
Hi all,

I have to admit, I'm not asking questions too often, only when don't know what to ask Google for :)
I have a postfix related question. I managed to configure it as a relay for gmail, it is working fine, I can correctly send mail through gmail. But here is the question:

Let's say myhostname is set to myfunkydomain.com and I have a gmail account configured for that domain, from this server (myfunkydomain.com) I'm sending an email message to:

[EMAIL="radekg@myfunkydomain.com"]radekg@myfunkydomain.com[/EMAIL]

Instead of receiving it in gmail I have it in

/var/mail/radekg

I suppose I know why this is the case but was curious if there is a way to change it and tell postfix "always send it to oustide world even if recipient address belongs to me".

Cheers,
Radek G

---

### Post by radekg on 2009-04-26
D'oh!
Figured it out. Instead of using:

mydestination=myfunkydomain.com

use:

mydestination=smtp.gmail.com

---

