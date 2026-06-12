---
title: "Prevent Apache from logging IP"
date: 2007-02-16
forum: Server Platforms
---

### Post by bunnynuts on 2007-02-16
I have the 6.06 default lamp server installed and need to prevent apache from logging the IP addresses of those visiting the site. I tried sending the CustomLog to /dev/null...lets just say that doesn't work at all (apache wont reload when you do that).

Any help/ideas will be greatly appreciated.

---

### Post by conjur3r on 2007-02-16
Take a look at the **LogFormat** directive in your /etc/apache2/apache2.conf

I believe you want to get rid of that %h at the beginning.  Restart apache and it shouldn't log IP addresses anymore.

---

### Post by bunnynuts on 2007-02-16
That did it, thanks for the help

---

