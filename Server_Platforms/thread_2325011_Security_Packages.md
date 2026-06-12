---
title: "Security Packages"
date: 2016-05-18
forum: Server Platforms
---

### Post by Marketing-Agentur on 2016-05-18
Hello,

I would like to know how to harden a ubuntu installation for the use of wordpress on a server, given that Mail, SFTP and HTTPS are running.

---

### Post by howefield on 2016-05-18
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by SeijiSensei on 2016-05-18
The most important thing I did after installing WordPress was restricting write permissions so that the Apache "user," www-data, could not alter the contents of the WP directories other than wp-content/uploads.  However this restriction makes it impossible for WP to update itself automatically, so I wrote a pair of scripts to fix the permissions before and after an update.  Here is the pre-update script:
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```

and here is the post-update script:
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```

My wp-admin/uploads directory is owned by the www-data user so these scripts don't interfere with my ability to upload graphics and other media.  The www-data is in the group that owns this directory so I change the group permissions in these scripts. I run the scripts from the top of the WP directory.

---

### Post by houstonbofh on 2016-05-18
Ubuntu is secure.  It is securing WordPress that is the problem.  I recommend running WordPress on an internap VM, with the static site generator, and export the static site to your world facing web server.  That, or check for update hourly.

---

### Post by Marketing-Agentur on 2016-05-21
thanks

---

