---
title: "Viewing Directories from Client Machines"
date: 2007-03-12
forum: Server Platforms
---

### Post by uamusa on 2007-03-12
I do not want to allow directory browsing via my webserver from client computers.  Will someone please tell me how to deactivate this?

using apache2

---

### Post by jtc on 2007-03-12
Assuming you have a default install you'll find some lines looking somewhat like this in your /etc/apache2/sites-available/default

```

...
<Directory /var/www/>
         Options Indexes FollowSymLinks MultiViews
         AllowOverride None
         Order allow,deny
         allow from all
         ...
</Directory>
...

```

Remove the option *Indexes*, save the file and restart Apache.

---

### Post by uamusa on 2007-03-12
Thank you!!  This fixed it.  -Chris McCall

---

