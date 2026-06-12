---
title: "Squirrelmail: OPTIONS link problem"
date: 2008-05-15
forum: Server Platforms
---

### Post by joanindo on 2008-05-15
hey guys,

i just finished setting up a web & mail server for my Lab.
i use Squirrelmail for the webmail so that users can open their emails
when they're not in Lab.

everything works well but there's one problem still bugging me.
i've problem with OPTIONS link in Squirrelmail after you login.

[http://.../mail/src/options.php](http://.../mail/src/options.php)     (wont open when i'm off campus) ???

when i'm at Lab (on site) and try to click the link it works well, but
at home (off site) it doesn't work.

i wonder what the problem is.

if you guys experienced this before and know how to solve it please reply.

cheers,

---

### Post by MJN on 2008-05-15
What error do you get?

Do all other links work okay?

Mathew

---

### Post by joanindo on 2008-05-15
> **MJN said:**
> What error do you get?

Do all other links work okay?

Mathew
i got this message: "The connection was reset"

other links Compose, Addresses, ... , Fetch are okay except Options.

do u have any idea about this problem?
how do i fix it?

thanks for the reply

---

### Post by MJN on 2008-05-15
I really don't know. I can't really see how it's a Squirrelmail problem, but rather a web-server or client issue.

It sounds like you're using Firefox - have you tried a different browser?

Mathew

---

### Post by joanindo on 2008-05-15
> **MJN said:**
> I really don't know. I can't really see how it's a Squirrelmail problem, but rather a web-server or client issue.

It sounds like you're using Firefox - have you tried a different browser?

Mathew
I tried IE and Safari. IE showed the same message as Firefox. but Safari just couldn't open.

Jon

---

### Post by joanindo on 2008-05-16
i don't know whether it's a web-server issue since i installed it with default configuration given by ubuntu server. that's all.

---

### Post by MJN on 2008-05-16
Try the Squirrelmail mailing list - they should be able to help pinpoint the exact problem/cause (or at least eliminate SM from the equation if need be).
 
Mathew

---

