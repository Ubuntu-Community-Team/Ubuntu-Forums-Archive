---
title: "Apache on Ubuntu Server"
date: 2007-05-23
forum: Server Platforms
---

### Post by Luft on 2007-05-23
I have been running a Suse Linux server but it died due to a hardware failure.  I'm switching my server over to Ubuntu.  I used the LAMP install.  It was very painless.  But now I need to allow my users to have web pages in there public_html directories.

Apache on Ubuntu is a little different than on Suse so I'm feeling a little disoriented.  Could someone point me to some doc files for Apache on Ubuntu?  Do I still just edit http.conf??

---

### Post by rickyjones on 2007-05-23
> **Luft said:**
> I have been running a Suse Linux server but it died due to a hardware failure.  I'm switching my server over to Ubuntu.  I used the LAMP install.  It was very painless.  But now I need to allow my users to have web pages in there public_html directories.

Apache on Ubuntu is a little different than on Suse so I'm feeling a little disoriented.  Could someone point me to some doc files for Apache on Ubuntu?  Do I still just edit http.conf??

[http://ubuntuforums.org/showthread.php?t=436230&highlight=public_html](http://ubuntuforums.org/showthread.php?t=436230&highlight=public_html)

Looks like you just need to enable a module from within Apache. 

-Richard

EDIT:

Here is some more info directly from Apache: [http://httpd.apache.org/docs/2.2/mod/mod_userdir.html](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html)

I believe the command to enable it is something like "a2enmod user_dir" but I could be severely mistaken. But that should help!

---

### Post by craigp84 on 2007-05-24
Assuming you're using apache2 (or above):

```
sudo a2enmod userdir
sudo /etc/init.d/apache2 restart
```

Then create public_html folders for each user and access via [http://myserver/~user/](http://myserver/~user/)

Hope this helps,

Craig

---

### Post by Luft on 2007-05-24
I haven't tried it on my server yet but it worked great on my test laptop.  

I think it is exactly the information that I needed.  Thanks! :D

---

