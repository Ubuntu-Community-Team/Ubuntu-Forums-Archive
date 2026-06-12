---
title: "Installing wordpress in our LAMP Server"
date: 2008-01-23
forum: Server Platforms
---

### Post by cocotu on 2008-01-23
We install wordpress in our LAN LAMP server.  We are trying to use permalinks, but keep getting: Not Found.  The same wordpress install works fine at our host company.  I read about enabling the Apache mod_rewrite here: [http://www.movingtofreedom.org/2007/05/09/how-to-wordpress-on-ubuntu-gnu-linux/](http://www.movingtofreedom.org/2007/05/09/how-to-wordpress-on-ubuntu-gnu-linux/)

I did it and still nothing.  Is there something else I need to enable in apache, mysql, php in our LAMP server in order to use wordpress permalinks?
thanks

---

### Post by Vinno on 2008-01-24
Did you follow on reading and try the .htaccess with the rewrite content?

---

### Post by cocotu on 2008-01-24
I gave up and decided to start over.  I'm woking on it at this moment.  Will let you know the results.  thanks Vinno!

---

### Post by cocotu on 2008-01-24
I did everything over.  Permalinks still don't work, it works fine without using the permalinks.  I followed the instructions in that site and I'm using the .htaccess correctly.  The mod_rewrite is enabled and I restarted apache several times.  No solution yet. thanks

---

### Post by cocotu on 2008-01-24
I fix it:

1. You need to change  AllowOverride None to  AllowOverride All
2. Restart Apache.

More info here: [http://codex.wordpress.org/Using_Permalinks](http://codex.wordpress.org/Using_Permalinks)

Thanks...

---

### Post by Vinno on 2008-01-25
Good job on it \\:D/

---

