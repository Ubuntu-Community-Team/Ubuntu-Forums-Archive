---
title: "Trouble changing user &quot;admin&quot; on phpmyadmin"
date: 2009-10-30
forum: Server Platforms
---

### Post by madmatter23 on 2009-10-30
I recently setup a file server using Ubuntu 8.04 LTS. I installed phpmysql and I've setup the root user with password as well as a couple of other accounts.

However, when I access phpmyadmin through my web browser, I am permitted to login using username "admin" and no password. Granted, the user has no privileges once logged in and can only view the information_schema, but it can login nonetheless. 

I've deleted user "admin" through the phpmyadmin web panel, reset the root password on the server, and removed the line (it's the only one) "admin:*" from /etc/phpmyadmin/htpasswd.setup, but none of these measures has changed a thing.

Can anyone offer a suggestion?

All help appreciated. Thanks!

---

