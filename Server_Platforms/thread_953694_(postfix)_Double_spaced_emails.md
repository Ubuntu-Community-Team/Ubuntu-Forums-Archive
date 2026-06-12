---
title: "(postfix) Double spaced emails?"
date: 2008-10-20
forum: Server Platforms
---

### Post by jay0316 on 2008-10-20
I am having problem with my emails getting double spaced using postfix and the php mail()function .  I found a thread that talked about it:
> Postfix under Mandrake 10.0 also objects to \\r\\n. The result is that every email is double-spaced, and all attachments break. (it was OK in 9.1).* My (short-term) fix is this:

$message = str_replace("\r",'',$message);

Adding the code to my script worked, however, we have a lot of pages sending mail and it would be difficult to track down every one and insert that code.  

Does anyone know of a solution that can be done within postfix's configuration or at the server level?

---

### Post by jay0316 on 2008-10-21
So, has no one ever have this problem before?

---

