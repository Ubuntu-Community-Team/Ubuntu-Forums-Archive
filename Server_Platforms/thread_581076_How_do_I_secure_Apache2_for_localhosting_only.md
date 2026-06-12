---
title: "How do I secure Apache2 for localhosting only"
date: 2007-10-19
forum: Server Platforms
---

### Post by ade234uk on 2007-10-19
How do I secure Apache2 for localhosting only.

The server is only being used for test purposes only and should not be available to the rest of the world.

Thanks

---

### Post by bunker on 2007-10-19
Either in one of your .htaccesses, put

```

                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128

```

Note you'll need the AllowOverride directive set properly in order to let .htaccess change global config details.  It has some different values, but if you're lazy just set it to 'All'

Or in your global config between the <Directory /var/www>...</directory> part.  That's normally in /etc/apache2/sites-enabled/000default.

---

### Post by ade234uk on 2007-10-19
Thank you.

---

