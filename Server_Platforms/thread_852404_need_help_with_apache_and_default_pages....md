---
title: "need help with apache and default pages..."
date: 2008-07-07
forum: Server Platforms
---

### Post by Mia_tech on 2008-07-07
I have an installation of apache, and when I type the [http://localhost](http://localhost) I get a page showing a list of all the pages in the root directory /var/www
I want to be able to browse to my web server and show the default index.html page which is not happening after adding this to my apache2.conf file
```
#defaul page for apache web server
DirectoryIndex index.html index.htm index.cgi index.pl index.php index.xhtml
```

still is browsing to the same page and not showing the index.html page, could someone advise me regarding this issue?

thanks

---

### Post by sp00ki on 2008-07-07
did you restart apache after making the change?  also, make sure apache (or whoever runs apache) has access to the index file.

---

### Post by Mia_tech on 2008-07-07
> **sp00ki said:**
> did you restart apache after making the change?  also, make sure apache (or whoever runs apache) has access to the index file.

yes I did restart apache after made the changes, and still the same problem, how could I manage access to the web pages in apache... is it with the old chmod command?...I've already given everyone rwx rights, and still not working besides so far I'm only testing the website, and it's only me accessing it..

thanks

---

### Post by cdenley on 2008-07-07
Try editing /etc/apache2/mods-available/dir.conf.

Apache accesses files as www-data. If that user has read access, permissions should be fine.

---

### Post by Mia_tech on 2008-07-07
> **cdenley said:**
> Try editing /etc/apache2/mods-available/dir.conf.

Apache accesses files as www-data. If that user has read access, permissions should be fine.

the file looks good all the possible home page are listed there "index.htm, index.html..etc.", and I gave everyone read access to that file with ```
sudo chmod ugo+r dir.conf
``` I hope that's what you meant, but still not working I've restarted apache and firefox numerous times and still not working...any other suggestions?

thanks

---

### Post by Mia_tech on 2008-07-07
I don't know if this could be part of the problem but when I restart apache I get this error
```
jorge@ubuntu-box:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

```
I don't think this is a big deal as I'm testing my apache from my local workstation, and it works, I just have to type [http://localhost/index.html](http://localhost/index.html), but what I want is not to have to type the index.html portion of it and have it default there
thanks in advance

---

### Post by osjak on 2008-07-07
Mia_tech, in your virtual host configuration disallow indexing:

        ```
<Directory /var/www>

# other directives if needed

                Options -Indexes

# other directives if needed

        </Directory>
```

Restart Apache and see if this hepled.

---

### Post by Mia_tech on 2008-07-07
thanks for directing me to that file...even though I don't know what that file is for, because it's not well documented....I was able to get it fixed, although I didn't comment it out like you suggested, I did find something that made me suspicious and I changed it, here's what I changed
in file /etc/apache2/sites-available/default

from ```
DirectoryIndex index.shtml
```

to ```
DirectoryIndex index.html
```

and that did it...I think the index.shtml was there because at some point I installed SSI on my server, and probably modified that file somehow

anyway thanks

---

### Post by osjak on 2008-07-08
Oh yes, if you had your index files set incorrectly in virtual host configuration, it would cause problems. I'm glad you found the error. I would still recommend you to turn off directory index, as I noted above. It will stop showing your directory index in directories with no index.html file in them. This way people cannot snoop around your webserver files you didn't intend to expose. It's just more secure that way.

---

