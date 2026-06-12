---
title: "Help with suexec on Ubuntu 11.10"
date: 2012-02-01
forum: Server Platforms
---

### Post by Pr1der on 2012-02-01
Not sure exactly where to post this...

I'm trying to set up a website development machine with Ubuntu 11.10 and Apache 2.2 and Perl 5.3.5. No PHP. I would like Apache to serve files from the following directory structure:

/home/user1/public_html/website1, with Apache running as user1
/home/user1/public_html/website2, with Apache running as user1
and
/home/user2/public_html/website3, with Apache running as user2

With respect to website1, I've done the following:

1. installed and enabled Apache module suexec-custom and configured it to point at /home and public_html/website1. No other changes to the Apache config files.

2. I use server-side includes, so I added index.shtml to dir.conf and directives in the 
virtual server file.

3. set up a virtual server with the following site file:

<VirtualHost *:80>
        # set server name
        ServerName      testbed1
        ServerAdmin webmaster@localhost
        # set suexec user and group
        SuexecUserGroup user1 user1

        # set document root
        DocumentRoot /home/user1/public_html/website1/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        # set the correct website root
        # and added other needed changes:
        #       option +IncludesNOEXEC
        #       allowoverride changed from None
        #       addoutputfilter
        #       addtype
        <Directory /home/user1/public_html/website1/>
                Options Indexes FollowSymLinks MultiViews +IncludesNOEXEC
                AllowOverride FileInfo Limit AuthConfig Indexes
                Order allow,deny
                allow from all
                AddOutputFilter INCLUDES .shtml
                AddType text/html .shtml
        </Directory>

        # set the correct cgi path, allowoverride to All
        ScriptAlias /cgi-bin/ /home/user1/public_html/website1/cgi-bin/
        <Directory "/home/user1/public_html/website1/cgi-bin/">
                AllowOverride All
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # commented out the following section
#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

</VirtualHost>

4. restarted Apache.

This setup works as long as all the files in website1 are readable by everyone... if I 
chmod them to 600 I get a 403 (no permissions) error. I assume this means that the server is not running as user1.

What am I missing?  Thanks...

---

### Post by CharlesA on 2012-02-01
Moved to Server Platforms per OP request.

---

### Post by Pr1der on 2012-02-03
In the end, this was my error; actually my misunderstanding. I thought  that Apache would always use suexec, whether it was running a script or serving a static page. Turns out that it's only for scripts. I ensured that the file/directory ownerships and permissions were correct... everything owned by user user1 group user1, all directory permissions 755, all static files 644, all scripts 750... and everything works as I want.

I stumbled on the hint to this on one of the Apache server forums. I never saw anything in the documentation I used that said the suexec was only for scripts. There's probably some basic stuff about web servers that I just don't know. At any rate, my question has been answered.

---

