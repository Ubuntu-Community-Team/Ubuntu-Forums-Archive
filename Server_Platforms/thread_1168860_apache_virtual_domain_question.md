---
title: "apache virtual domain question"
date: 2009-05-24
forum: Server Platforms
---

### Post by wsonar on 2009-05-24
I was wanting to change my default html file from index.html to an index.psp
I'm using mod_python which seems to be working fine.

when I look at my /etc/apache2/httpd.conf file it is empty

I have a file /etc/apache2/sites-availible/default

that has my virtual site setup information in it but not everything the httpd.conf file would have.

I don't know how the file got blanked out maybe it happened when setting up the virtual domains, but my site is functioning properly

does anybody know if there is another httpd.conf file somewhere or how the virtual domains work.

Thanks for the suggestions

---

### Post by alastair on 2009-05-24
This is normal. The httpd.conf is not used anymore (that I know of) and virtual sites go into their own config files inside sites-avaiable/ (symlinked from sites-enabled). See the Apache web site (and possibly Ubuntu docs). Your virtual config setup will be done inside your "sites-available" setup file.

---

### Post by kustomjs on 2009-05-24
httpd.conf is used to secure pages for passwords.  just keep in mind if you want to put passwords for pages use httpd.conf with this:


<Directory /var/www/>
AuthType Basic
AuthName " Protected Area "
AuthUserFile /var/www/.htpasswd
require valid-user
</Directory>


and is .htpasswd in the directory that you want to put a password in.

then restart your apache to get the password popup to work on the page you want to secure.

---

### Post by wsonar on 2009-05-24
Thanks for the replies
do I need to add this to my default file

```
<IfModule mod_dir.c>
  DirectoryIndex index.html index.psp
</IfModule>

```

Everything I've read shows this is where you change the default page but I'm having trouble figuring out how to do it with the virtual host

I'm working with mod_python and embedding python into .psp pages, so I want the index.psp to be the default page

here is my default virtualhost file

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/mysite
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/mysite>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                AddHandler mod_python .psp
                PythonHandler mod_python.psp
                PythonDebug On
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

Thanks again.

---

### Post by wsonar on 2009-05-24
> **kustomjs said:**
> httpd.conf is used to secure pages for passwords.  just keep in mind if you want to put passwords for pages use httpd.conf with this:


<Directory /var/www/>
AuthType Basic
AuthName " Protected Area "
AuthUserFile /var/www/.htpasswd
require valid-user
</Directory>


and is .htpasswd in the directory that you want to put a password in.

then restart your apache to get the password popup to work on the page you want to secure.

I am also interested in a secure login option for my site I've been exploring the many options thanks for the tip

---

### Post by wsonar on 2009-05-24
Sweet got it just updated my /etc/apache2/sites-available/default file

and added this

```

<IfModule mod_dir.c>
  DirectoryIndex index.psp
</IfModule>

```

restarted apache and it's working

Thanks for the tips  :)

---

