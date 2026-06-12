---
title: "Apache2 2.2.4 error"
date: 2008-02-23
forum: Server Platforms
---

### Post by Daoism on 2008-02-23
My site was working fine before, but today i tried to view my site and i got a stupid DNS error. So I restarted my server, but DNS error did not go away. Then i checked my apache2 log.

[error] (9)Bad file descriptor: apr_socket_accept: (client socket)
[Sat Feb 23 07:10:40 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations

Does anyone know how to fix this error?

Thanks,
Daoism

---

### Post by tubezninja on 2008-02-23
The Bad file descriptor error I think might be unrelated to the DNS issue.  What specific error message did you get from your browser when you tried to access the page?

Also, does a traceoute or ping from another computer resolve your hostname?

---

### Post by Daoism on 2008-02-24
DNS ERROR - The page does not exist

Yeah i did everything and i still getting that error. BUt somehow today, i can access to my site again. This is soo weird.

---

