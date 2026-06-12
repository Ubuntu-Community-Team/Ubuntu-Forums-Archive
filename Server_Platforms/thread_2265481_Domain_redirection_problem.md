---
title: "Domain redirection problem"
date: 2015-02-15
forum: Server Platforms
---

### Post by bremenpl on 2015-02-15
Hello there,
I am running ubuntu server 14.04 on an Microsoft Azure VM. I am hosting an Owncloud server there. To acces my server I use myname.cloudapp.net/owncloud. I have succesfully added my custom domain so instead of this name, I can use owncloud.mycustomdomain.com/owncloud. Now I was wondering, since to get to my site I have to use owncloud.mycustomdomain.com/owncloud it would be nice to change the address directly to owncloud.mycustomdomain.com, without typing the owncloud after the slash. I would really aprichiate if someone could explain me how to do this. The poin is to:

use myapp.cloudapp.net/owncloud (with the /owncloud) and
owncloud.mycustomdomain.com without the slash.

Is there a way to acces the owncloud folder when using customdomain? I tried doing this when setting CNAME record but it doesnt allow slashes.
I am using apache2 and php5. I would really aprichiate any help.

---

### Post by SeijiSensei on 2015-02-16
What if you go to owncloud.mydomain.com now?  Do you get the default "It works!" page, or something else?

If your Apache configuration looks something like this:
```

<VirtualHost *:80>
     ServerName myname.cloudapp.net  
     ServerAlias owncloud.mydomain.com
     DocumentRoot /var/www/html
     [ stuff ]
</VirtualHost>

```
change the DocumentRoot to point to /var/www/html/owncloud, or wherever the top of the Owncloud installation is located.

---

