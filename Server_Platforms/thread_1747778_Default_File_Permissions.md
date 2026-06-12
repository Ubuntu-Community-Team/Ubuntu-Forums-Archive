---
title: "Default File Permissions"
date: 2011-05-03
forum: Server Platforms
---

### Post by rainleader on 2011-05-03
I have files in /var/www that I've set permissions as follows:

user:www-data
chmod 755

How can I set it so all subsequent files uploaded (via SFTP) have those same permissions and I don't have to keep re-running chown/chgrp/chmod -R?

Thanks.

---

### Post by falko on 2011-05-03
Use umask 022.

---

### Post by Lars Noodén on 2011-05-03
> **rainleader said:**
> user:www-data
chmod 755


The user www-data is the web server so the settings above open up a potential security problem by letting the web serve write.   If you're looking for a way to have users upload, then make another group and use that group instead of www-data.

In addition to setting the umask as Falko suggests you can set the sticky bit for the group so that new files will be made using that group.

```

sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs {} \;

```

---

