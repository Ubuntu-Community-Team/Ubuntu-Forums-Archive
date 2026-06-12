---
title: "Where is my vhost file?"
date: 2011-12-21
forum: Server Platforms
---

### Post by mindb0ggler on 2011-12-21
I have been following a tutorial recently until I came up against this when talking about the apache config files:
```

The following must be added to an existing vhost (my use case) or to a newly created one as it will not work outside of VirtualHost directives..

```
then there was lots of code afterwards. Where should I put this code? does it go in apache.conf or its own file?

---

### Post by volkswagner on 2011-12-21
I prefer using individual vhost files.

They are located at /etc/apache2/sites-available

Take a look a the [apache documentation]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") included in the sticky at the top of this forum.  This explains the vhost procedure very well.

---

### Post by mindb0ggler on 2011-12-22
Thanks so much, you've been really helpful :)

---

