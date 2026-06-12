---
title: "Apache2/LDAP Problem"
date: 2010-02-05
forum: Server Platforms
---

### Post by andremta on 2010-02-05
I'm having problems with Apache2 to setup LDAP authentication to my SVN server.

My SVN/DAV works nice, but when adding LDAP authentication I got a problem.

**/etc/apache2/mods-available/dav_svn.conf**
[PHP]## SVN Technical
<Location /technical>
     DAV svn
     SVNPath /home/svn/technical
     AuthType Basic
     AuthName "Technical SubVersion repository"
     #AuthUserFile /home/svn/svn-users

     AuthBasicProvider ldap
     AuthLDAPEnabled on
     AuthLDAPAuthoritative on
     AuthLDAPURL ldap://192.168.1.2/ou=people,dc=myserver,dc=com
     AuthzSVNAccessFile /etc/svn-users
     Require valid-user

     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
</Location>[/PHP]

> 
root@ubuntu:/etc/apache2# **sudo a2enmod ldap**
Module ldap already enabled


> root@ubuntu:/etc/apache2# **sudo a2enmod authnz_ldap**
Considering dependency ldap for authnz_ldap:
Module ldap already enabled
Module authnz_ldap already enabled


> root@ubuntu:/etc/apache2# **/etc/init.d/apache2 reload**
[COLOR="Red"][B]Syntax error on line 67 of /etc/apache2/mods-enabled/dav_svn.conf:
Invalid command 'AuthLDAPEnabled', perhaps misspelled or defined by a module not included in the server configuration
   ...fail![/B][/COLOR]


Since my LDAP modules are enable, why is happening this error?

---

### Post by terazen on 2010-02-05
You may not need the AuthLdapEnabled line.  Have you tried commenting it out?

---

### Post by BobVila on 2010-02-05
[SIZE=2]I think AuthLDAPEnabled is deprecated.

Try [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]AuthBasicProvider ldap

Here's the apache auth doc for reference:
[http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html](http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html)


[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by andremta on 2010-02-06
Thanks for the reply guys!

When I comment the AuthLDAPEnable it shows me the error:
> 
Invalid command '**AuthLDAPAuthoritative**', perhaps misspelled or defined by a module not included in the server configuration

I'm not sure If I'm loading the correct LDAP modules!

---

### Post by airtonix on 2010-10-20
Since it's been about 9-10 months since you last posted here, I'll assume : 

1. you realised that reading the linked page is a good idea

Anyway, this is my working vhost def file : 

```


<VirtualHost *:80>
        ServerAdmin airtonix@ubuntu.local
        ServerName support.localhost
        ServerAlias support.ubuntu
        ServerAlias support.ubuntu.local

        DocumentRoot /var/www/support/public_html

        <Directory /var/www/support/public_html>
                Options Indexes FollowSymLinks MultiViews
                Order allow,deny
                allow from all
        </Directory>

        <location / >
                AuthBasicProvider ldap
                AuthLDAPURL ldap://127.0.0.1:389/ou=people,dc=ubuntu,dc=local?uid
                AuthLDAPBindDN "CN=admin,DC=ubuntu,DC=local"
                AuthLDAPBindPassword "--plaintext-pasword-:("
                AuthType Basic
                AuthName "Password Prompt"
                require valid-user
        </location>
        ErrorLog /var/www/support/logs/error.log
        CustomLog /var/www/support/logs/access.log combined

</VirtualHost>

```

Few things : 

1. apache2 server runs on the same machine as the ldap server, so i just refer to it via the 127.0.0.1 local loopback ip address.
2. at the moment i'm specifying the ldapAdmins password in plaintext, this is not ideal and i'd really like to use something else that does not immediatly reveal what the password is.
3. I confirm my LDAP server runs fine by using phpldapadmin to browse and edit objects.

---

