---
title: "Apache Virtual Hosts Issue"
date: 2007-03-01
forum: Server Platforms
---

### Post by Klaus on 2007-03-01
Hello,

I have setup Ubuntu desktop 6.10 and I am wanting to setup some Apache Virtual Hosts for development on my laptop. I have done this successfully in Windows so I have some idea of what i'm doing but its not working under Ubuntu. Anyway, I created the file in /etc/apache2/sites-available/site.conf and ran the a2ensite command and it created the links just fine. I restart Apache and go to my site and I get a Forbidden message. I check /var/log/apache2/error.log and get this:

[Thu Mar 01 20:42:20 2007] [crit] [client 127.0.0.1] (13): /home/klaus/projects/sitename/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

I have setup my virtual host as:

NameVirtualHost *:80
<VirtualHost *:80>
        ServerName sitename.dev
        ServerAlias sitename.dev
        DocumentRoot /home/klaus/projects/sitename/svn/trunk/site

        <Directory /home/klaus/projects/sitename/svn/trunk/site>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                Allow from all
        </Directory>

</VirtualHost>

Notice how the path I setup does not correlate to the path in the error message. Any ideas?

---

### Post by Mr. C. on 2007-03-01
Apache will open all .htaccess files working its way down the directory structure.

Examine the permissions of your .htaccess file.  You will see that apache does not have permission to read it or the directory which contains it.

---

### Post by Klaus on 2007-03-01
There is no .htaccess file in that folder thats the thing. All the folders just contain other folders except for the one at the very end /site. Thats the first .htaccess file in the entire folder path. If it still needs permissions which ones?

---

### Post by Mr. C. on 2007-03-01
You still need 'rx' permissions (read/examine) for apache on the entire directory path all the way down.  Apache is trying to see if any .htaccess files exist.  It can't do this without 'rx' permissions.

---

### Post by Klaus on 2007-03-01
How do I properly set up the permissions? Nothing I try works,

---

### Post by Mr. C. on 2007-03-01
Show what they are for each directory:

ls -ld /home/klaus
ls -ld //home/klaus/projects
...
ls -ld /home/klaus/projects/sitename/svn/trunk/site

show the user/group id of your apache daemon:

id apache
or grep /etc/passwd and /etc/group for your apache or httpd user.

---

