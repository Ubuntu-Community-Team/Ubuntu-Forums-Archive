---
title: "Apache2 mod_expires acting inconsistantly across sites..."
date: 2011-09-21
forum: Server Platforms
---

### Post by Rebajas on 2011-09-21
Hi Everyone,

I have gone through the steps to get mod_expires working:

```
        a2enmod expires
        /etc/init.d/apache2 restart
```

I have added the following to all virtual hosts, with no variance between them:

```
        ExpiresActive On
        ExpiresDefault A0

        <IfModule mod_expires.c>
                <FilesMatch "\.(js|css)$">
                        ExpiresDefault "access plus 1 week"
                </FilesMatch>
                <FilesMatch "\.(jpg|jgeg|png|gif)$">
                        ExpiresDefault "access plus 1 month"
                </FilesMatch>
        </IfModule>
```

But, some sites work and some don't.

For example, [http://www.secretsauce.co.uk/](http://www.secretsauce.co.uk/) I can see there are Expires headers of one month, but [http://beta-www.secretsauce.co.uk/](http://beta-www.secretsauce.co.uk/) there is not (just using Firebug to test).

Is there something, somewhere that might explain this weirdness?

Any help appreciated,


Tony.

---

### Post by Rebajas on 2011-09-22
If you have thoughts but need more information on the setup, then let me know. 

Also, have fixed jgeg typo in images FilesMatch.

Thanks in advance.

---

### Post by Rebajas on 2011-09-25
Any ideas anyone?

---

### Post by naptastic on 2011-11-30
Hello,

I tried for a while to set up expires rules for a DokuWiki installation and had about given up. Just on a whim, I moved the .htaccess file to its parent directory (my docroot; the wiki is in docroot/wiki) and it's handling it properly now. *shrug*

It still doesn't seem to be consistent, but it's at least working for me, so I'm happy. And it makes things way faster.

Hope that helps.

Next up: deflate.

---

