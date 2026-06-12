---
title: "Apache 2 what am I doing wrong?  I still get forbidden error."
date: 2015-06-25
forum: Server Platforms
---

### Post by RobRobinson on 2015-06-25
I followed the tutorial to the letter.

I edited apache2.conf to

```
<Directory /home/rob/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

```

Then I edited 000-default.conf to

```
DocumentRoot /home/rob/www/
```

And when I try to access my page I still get

"Forbidden


You don't have permission to access / on this server."

I am in a pickle here.  What the heck am I doing wrong?

Thanks

Rob

---

### Post by Lars Noodén on 2015-06-25
> **RobRobinson said:**
> I followed the tutorial to the letter.

I edited apache2.conf to...

Which tutorial?  In Ubuntu, the first default virtual host is in the file 000-default.conf in the directory /etc/apache2/sites-enabled/
In Ubuntu it is not usual to have to modify apache2.conf, and even then not for vhosts.

---

### Post by RobRobinson on 2015-06-25
Thanks Lars, let me try that.

---

### Post by RobRobinson on 2015-06-25
000-default.conf


in both sites-available and sites-enabled both read


```
DocumentRoot /home/rob/www/

```

Still no go

What next?

---

### Post by Lars Noodén on 2015-06-25
And you have the following in 000-default.conf?

```

<Directory /home/rob/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

```

(Note that the files in sites-enabled are symlinks to the files in sites-available, you can see that with 'ls -lh'.  So only one file needs changing if it was done right.  )

If that is set, then check the permissions.  

```

sudo chmod o+x /home/
sudo chmod o+x /home/rob/
sudo chmod o+rx /home/rob/www/

```

And  see if you can read the files:

```

sudo -u www-data ls /home/rob/www/

```

---

### Post by Lars Noodén on 2015-06-25
By the way, you are moving the virtual host's whole document root.  There is a built-in feature where you have have per-user directories: 

[http://httpd.apache.org/docs/2.4/mod/mod_userdir.html](http://httpd.apache.org/docs/2.4/mod/mod_userdir.html)

[http://httpd.apache.org/docs/2.4/howto/public_html.html](http://httpd.apache.org/docs/2.4/howto/public_html.html)

---

### Post by RobRobinson on 2015-06-25
This is in the apache2.conf

<Directory /home/rob/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

---

### Post by RobRobinson on 2015-06-25
The chmod did the trick!  Thank you so very much Lars.

Rob

---

### Post by Lars Noodén on 2015-06-25
> **RobRobinson said:**
> This is in the apache2.conf


Please try moving it out of apache2.conf and into /etc/apache2/sites-enabled/000-default.conf the restart apache and see if that helps.

Edit: ok I see that it is fixed.  But the right place for a vhost configuration is in the vhost's own file.

---

