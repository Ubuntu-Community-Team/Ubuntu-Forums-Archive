---
title: "vsFTPd question :)"
date: 2009-09-24
forum: Server Platforms
---

### Post by ieatlinux on 2009-09-24
I am not using ubuntu on this dedicated server (CentOS), as I didn't set it up :( 
I assume it would be the same across most platforms though. 
I am a root user on a dedicated server that me and a friend share and he is the one that set it up and I can't really contact him right now.
He set up vsFTPd server on our server but the password he gave me for my root FTP account isn't working and I was wondering how to change the password for my FTP account without FTP access.
Is this possible?

Thanks
-ieatlinux

---

### Post by Bachstelze on 2009-09-25
First we have to know if the server uses local users or virtual users. Do you have SSH access to the server?

---

### Post by ieatlinux on 2009-09-25
local users, yes I am root and can access it through SSH.

---

### Post by Bachstelze on 2009-09-25
> **ieatlinux said:**
> local users, yes I am root and can access it through SSH.

And you have a root FTP account? That's an extremely bad idea... Anyway, if your FTP users are local system users, then they can login using the same password they use on the sysem (provided that they're allowed to login at all, of course).

---

