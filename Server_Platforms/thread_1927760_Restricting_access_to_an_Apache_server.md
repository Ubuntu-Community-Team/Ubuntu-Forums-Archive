---
title: "Restricting access to an Apache server"
date: 2012-02-18
forum: Server Platforms
---

### Post by I Am Legend on 2012-02-18
Hi, 

I have apache2 serving pages from my Ubuntu machine (10.4 LTS). I'm trying to add password control (right now anyone can access the files just by going to the ip address). I'm not much of an Apache expert but I tried the following steps after some research on the web:


1) Added to  /etc/apache2/apache2.conf: 

AccessFileName .htaccess

<Directory />
  Options FollowSymLinks
  AllowOverride AuthConfig
  Order deny,allow
  Deny from all
</Directory>
 
2) Added a .htaccess file
>> cat /var/www/.htaccess 
AuthUserFile  /etc/apache2/.htpasswd
AuthGroupFile /dev/null require valid-user 
AuthName  Default
AuthType Basic
require user <user>

3) Created a password file with:
sudo htpasswd -c /etc/apache2/.htpasswd <user>

[NOTE: <user> is of course just a simple user name in both cases above.]

4) Restarted Apache
sudo apache2ctl restart


This seems to have no effect, pages are seared up to remote machines without any password protection.

Did I miss something or is this just the wrong method?

---

### Post by Iowan on 2012-02-18
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a doc that might help. Under which directory do you have the files?

---

### Post by I Am Legend on 2012-02-18
Seem to have got this working by adding the step mentioned here:

To make .htaccess files work as expected, you need to edit /etc/apache2/sites-available/default. Look for a section that looks like this:

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
You need to modify the line containing AllowOverride None to read AllowOverride All. This tells Apache that it's okay to allow .htaccess files to over-ride previous directives. You must reload Apache before this change will have an effect:


Thanks for the link.

---

### Post by SeijiSensei on 2012-02-19
> **I Am Legend said:**
> You need to modify the line containing AllowOverride None to read AllowOverride All. This tells Apache that it's okay to allow .htaccess files to over-ride previous directives.

Alternatively you can leave AllowOverride set to none and place any directives you would have placed in .htaccess in the VirtualHost definition itself.

I maintain separate configuration files for each virtual host and put any access control directives in the appropriate <Directory> container.  .htaccess files make sense when other people are storing sites on your server.  If you're entirely in control of all the sites, it's safer to manage the directives in the configuration files in /etc/apache2/.

---

