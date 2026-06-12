---
title: "Give Apache rights outside /var/www"
date: 2009-11-12
forum: Server Platforms
---

### Post by Bruut on 2009-11-12
Hello

Ik have a server running Apache. I've written a PHP application which manages documents elsewhere on the server (/var/documents/). But I have got trouble setting the permissions. Below the setup

Apache 
user: www-data
group: www-data

/var/documents/
user: bruut
group: documentfolder
chmod: 2775

Currently PHP/Apache can't write to /var/documents. To fix this I thought about adding user 'www-data' to group 'documentfolder'. But easily said:it still gives an error. Should this work? If not, how can I make it work?

I don't want to change the group of /var/documents because I setup several users and linked it to the 'documentfolder' group.

---

### Post by Valasule on 2009-11-12
Have you looked into using the suexec module in apache?  This might solve your problem since Apache won't be able to modify files that are not owned by user www-data and group www-data unless they are set to world writable, which is not always a good idea.
The package you will want to install is apache2-suexec-custom and you can find information on how suexec works at Apache's website here: [http://httpd.apache.org/docs/2.2/suexec.html](http://httpd.apache.org/docs/2.2/suexec.html)

Hope this gets you goin, cheers.

---

### Post by lykwydchykyn on 2009-11-12
Are you running apparmor?  It might be preventing this.

see if there is an apparmor profile for apache under /etc/apparmor.d/

---

### Post by Lars Noodén on 2009-11-12
How are the permissions set inside your virtual host configuration?

```

<Directory "/var/documents">
      Options Indexes FollowSymLinks MultiViews
      AllowOverride None
      Order allow,deny
      Allow from all
      . . .
</Directory>

```

---

### Post by Bruut on 2009-11-13
I'm running Ubuntu 6.06 LTS, that version doesn't contain Apparmor afaik.

I created the following script to test:
<?php touch ('/var/documents/test'); ?>

I just set the permissions on test to get it working, and it only works when the owner is www-data. Otherwise, even with chmod 777, I got a permission denied.


There is no /var/documents direction in the apache config. only a /var/documents/www and I want apache to be able to create files in for example /var/documents/development
```

DocumentRoot /var/documents/www

<Directory />
	Options FollowSymLinks
	AllowOverride None
</Directory>

<Directory /var/documents/www/>
	Options FollowSymLinks MultiViews
	AllowOverride all
	Order allow,deny
	allow from all
</Directory>

```

About suexec module, I first want to try to work without it.


Thanks for the help so far

---

### Post by Lars Noodén on 2009-11-13
If Apache's configuration points to /var/documents/www/, then that directory must exist on the filesystem. If it does not exist, then create it and then set the file permissions so the group www-data can read it. e.g.

```

# just a guess.  ymmv
ls /var/documents/www ||*sudo mkdir -p /var/documents/www
sudo chgrp www-data /var/documents/www

# read access:
sudo chmod u=rwx,g=rxs,o=rx /var/documents/www

# if write access is needed then use this instead
sudo chmod u=rwx,g=rwxs,o=rx /var/documents/www

```

If that was not it can you cut and paste a line from the Apache error log showing the exact error?

suexec is not necessary right away.  Apache should be running as user www-data and group www-data.  You can see that in /etc/apache2/envvars

---

### Post by Bruut on 2009-11-13
I'm currently playing with it again, but it looks like it works fine now. With chmod 2775 bruut/documentsfolder i can write in /var/documents/

I think the permissions were not 2775. 

Thanks for all the help anyway.

---

### Post by Telep on 2009-12-16
Just wondering, if I understand correctly it is possible to change the user Apache runs as from www-data to something else, such as my own user ID, even without suExec. Is there any reason not to do this if it's my own server ?

---

### Post by Sporkman on 2009-12-17
> **Telep said:**
> Just wondering, if I understand correctly it is possible to change the user Apache runs as from www-data to something else, such as my own user ID, even without suExec.

Try this (found by googling):

[http://ubuntuforums.org/showpost.php?p=5960549&postcount=2](http://ubuntuforums.org/showpost.php?p=5960549&postcount=2)

---

