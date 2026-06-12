---
title: "Apache won't use user directory"
date: 2010-05-12
forum: Server Platforms
---

### Post by Radly on 2010-05-12
I'm configuring Apache for the first time on this box (8.04 LTS) and Apache2 for the first time ever.  "Out of the box" it runs fine and I get the "It Works" page okay.  But I'd **like** to use the virtual site feature to direct Apache to a folder in my user space, and I keep getting errors.

When I point a browser at localhost, the 404 message is "The requested URL / was not found on this server." and the /var/log/apache2/error.log ends with "File does not exist: /htdocs.

Here's my config file from the apache2/sites-available folder:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/daryl/public_html/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/daryl/public_html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

I diff'ed this file with the default and the only differences are in the DocumentRoot line and the <Directory ...> line.
My public_html folder has permissions 755 and the index.html file is 644.  

What am I missing?

---

### Post by cdenley on 2010-05-12
```

ls -l /home/daryl/public_html
ls -ld /home/daryl/public_html
ls -ld /home/daryl
ls -ld /home
ls -ld /
sudo /etc/init.d/apache2 restart
echo -e "GET / HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

---

### Post by Radly on 2010-05-12
Well, I'm not quite sure whether you're just suggesting I do those things, or suggesting I do them then post the result.  In any case, I'm restarting with a clean slate (different distro), so this issue is now moot (until I have the same problem again with the new distro).  Thanks, anyway.

---

### Post by cdenley on 2010-05-12
> **Radly said:**
> Well, I'm not quite sure whether you're just suggesting I do those things, or suggesting I do them then post the result.  In any case, I'm restarting with a clean slate (different distro), so this issue is now moot (until I have the same problem again with the new distro).  Thanks, anyway.

The restart, in case you didn't know it is necessary for a new configuration, the permissions for all parent directories, because the www-data user needs permission for all of them, and the netcat command to verify there is actually a problem with the server, and not your browser caching a previous response.

---

### Post by Radly on 2010-05-12
I got it about restart.  I've done that and "reload" a dozen times or so.  And it looks like I'm coming back to Ubuntu after all--I can't get anything other than Ubuntu 8.04 on my machine (Fedora 12, Ubuntu 10.04, and Debian 'squeeze' all crash with the same stack trace, Ubuntu 9.10 can't detect my Ethernet card.  I think this "one world" distro is trying to force me where I don't want to go--a new processor. :)

---

### Post by Radly on 2010-05-13
And the answer is...

When Ubuntu installs, it sets the permissions on the user's home directory to 754, not allowing "others" to navigate the directory, which blocks Apache from looking for .htaccess files.  So here's the new question: for now I've just made that directory browseable (755), but I have this niggling feeling that a more secure solution is out there somewhere to be found; what might that be?

---

### Post by cdenley on 2010-05-13
> **Radly said:**
> And the answer is...

When Ubuntu installs, it sets the permissions on the user's home directory to 754, not allowing "others" to navigate the directory, which blocks Apache from looking for .htaccess files.  So here's the new question: for now I've just made that directory browseable (755), but I have this niggling feeling that a more secure solution is out there somewhere to be found; what might that be?

And that is why I had asked for the output from this command.
```

ls -ld /home/daryl

```

You could do this, but it won't make much of a difference
```

sudo chgrp www-data /home/daryl
sudo chmod 754 /home/daryl

```
Or you could use ACL's.

---

### Post by Radly on 2010-05-13
Okay, I'll mull that over.  If "it won't make much of a difference", it goes to the bottom of my To-Do list. :)

Thanks again!

---

