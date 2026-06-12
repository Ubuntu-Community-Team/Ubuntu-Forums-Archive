---
title: "localhost folder ownership problem"
date: 2011-02-17
forum: Security
---

### Post by Coastalguy on 2011-02-17
I just installed a lamp on my Ubuntu 10.10. The localhost works fine running the index.html on var/wwww that the install added there.

However, when I pointed the localhost to another folder, I just get a 403 Permission Not granted error. On checking the owner of these folders, the default var/www is set to root, where my new folder owner is set to my ownership. 

Obviously, my owner permissions is lacking something that will not allow my local sites to run. Do I set the new folder (and sub-folders) to root, or update my owner permissions, or what?

If someone could let me know the best way to get the sites under my new folder to run, and give me the commands that I need to do this, it would be appreciated. Thanks....

---

### Post by cariboo on 2011-02-17
I'll leave the permission issues to others as the only web sites I run aren't open to the rest of the world.

As for getting other sites to work, there should be a configuration file in /etc/apache2/sites-available for each separate web site you run, these will be symlinked to /etc/apache2/sites-enabled after you run:

```
sudo a2ensite
```

If you use pre-package sites from the repositories, for example wordpress or mediawiki, there is usually a configuration file in the /etc directory for each site.  For example when you install wordpress from the repositories, after the installation is finished you'll find a file called apache2.conf in /etc/wordpress, just copy the file to /etc/apache2/sites-available:

```
sudo cp /etc/wordprees/apache2.conf /etc/apache2/sites-available/wordpress
```

then run:

```
sudo a2ensite wordpress
```

to make the site available. To access it from a browser type:

[http://localhost/wordpress](http://localhost/wordpress)

---

