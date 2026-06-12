---
title: "401 error"
date: 2008-12-28
forum: Server Platforms
---

### Post by quikone8 on 2008-12-28
I am thinking that this might be a configuration error, any idea how to fix it?

401 Unauthorized
Your client does not have permission to get URL / from this server.

---

### Post by Drezard on 2008-12-28
Run the command:

```

chown -R www-data /var/www
chgrp -R www-data /var/www

```

That should do it. Its got the wrong permissions on the files. 

Daniel

---

### Post by quikone8 on 2008-12-28
> **Drezard said:**
> Run the command:

```

chown -R www-data /var/www
chgrp -R www-data /var/www

```

That should do it. Its got the wrong permissions on the files. 

Daniel

Hi,

Thanks for the help, I am still getting the login screen, but when I enter user and pass it does not let me through.  It almost has to be something I did or didn't do in a configuration file.

I found out late last night that Apache is not accepting the ip number for some reason, so I am getting stuck in the router.  All of the routing looks good in the router, but for some reason Apache is only looking at my 252 address and not my 251 address.  I am going to change a few things on my domain to see if I can resolve this.  If anyone has some ideas as to why Apache does not see this address, I would love to hear the ideas.

---

