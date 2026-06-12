---
title: "SVN - auto export to &quot;/var/www&quot; upon each commit, running chown fails without root"
date: 2009-10-22
forum: Server Platforms
---

### Post by vcppp_p on 2009-10-22
Hi
my machine is running both SVN and HTTP server. 
I need a "trick" to export the files from the repository to /var/www each time anyone commits the changes to the repo. Therefore I found and adopted the following script:

```

#!/bin/sh

# Delete Old site
rm --interactive=never -R /var/www/site

# Export Repository
svn export --force file:///var/svn/site/var/www/site

# Make sure Apache Owns the website
chown -R www-data:www-data /var/www/site
chmod 777 /var/www/site/cache
chmod 777 /var/www/site/logs
chmod 777 /var/www/site/data.sqlite
chmod 777 /home/www/kohana/sites/portfolio/data/stats.sqlite

```

unfortunately, chown requires root privilages. The problem is that without setting proper chmods and chowns my app won't work, and setting them obviously fails as the script is being run automaticaly by svn server (user svn, group: svn). I need to set the file's chown to www-data somehow... how can I do that?

thanks in advance

---

### Post by yknivag on 2009-10-22
You could run the script as root which will give it the required permission.

---

### Post by vcppp_p on 2009-10-23
> **yknivag said:**
> You could run the script as root which will give it the required permission.
it is being ran by SVN server, automatically...

---

### Post by yknivag on 2009-10-23
Is there any pressing reason why the apache user must own the website? Expecially as you're then issuing chmod 777 making the files world writable?

Could you not simply change /var/www/site/ to be owned by the user than svn is running as?  The chown line will then not be necessary in your script.

---

### Post by MalditohoN on 2012-01-31
Hi,

Is there another way just to link the repository and the webserver(/var/www) location. so that if you have updated a file on the repo, the files on the webserver will be updated as well.

Thank You!

---

