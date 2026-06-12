---
title: "Apache &amp; Active Directory"
date: 2009-09-25
forum: Server Platforms
---

### Post by ppdit on 2009-09-25
Hello Ubuntu Community!

Long time lurker, first time poster!  All help is greatly appreciated.

Here is what I have:

Ubuntu 9.04 running the latest software updates.

I want to use Apache to authenticate against a domain controller.  All apache modules have been loaded, but I'm getting ldap_simple_bind_s failed (invalid credentials) when I try to authenticate.  Here are my default site config:

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        <Directory /var/www/ppdinet/>
                AllowOverride None
                AuthzLDAPAuthoritative on
AuthType Basic
AuthBasicProvider ldap
AuthName "Apache LDAP"
                AuthLDAPURL ldap://harmony.ppdmail.dom:389/ou=EmailUsers,o=ppdmail,c=dom?uid?sub
                AuthLDAPBindDN cn=Administrator,ou=Users,o=ppdmail,c=dom
                AuthLDAPBindPassword *
order allow,deny
allow from All
require valid-user
Satisfy any
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


I can ping my servers by name.  The above is the current config that doesn't work.  Here is one I originally tried:

AllowOverride None
AuthzLDAPAuthoritative on
AuthType Basic
AuthName "Apache LDAP"
AuthLDAPURL "ldap://harmony.ppdmail.dom:389/ou=EmailUsers,dc=harmony,dc=ppdmail?sAMAccountName?sub?(objectCategory=person)(objectClass=User)"
AuthLDAPBindDN "cn=administrator,cn=Users,dc=harmony,dc=ppdmail,dc=dom"
AuthLDAPBindPassword *****
 Order allow,deny
Allow from All
Require valid-user

I even tried using the .htaccess method with no luck.  I need to get this going as soon as I can, but I am out of ideas.  Thank you in advance.

---

### Post by scorp123 on 2009-09-26
"Active Directory" and LDAP are similar ... but not the same. A better way to achieve what you want would be via ***LikeWise Open*** I guess? Apache would then authenticate against the system (as if it were authenticating local Linux users), but your system in turn would authenticate against the AD controller, thanks to ***LikeWise*** ...

I'd suggest you try that route.
```
sudo apt-get install likewise-open likewise-open-gui
```

That latter package gives you an easy to use "LikeWise" menu entry underneath the ***System > ...*** menu (in the top menu bar).

After that you should be able to login with a valid AD username and password. The normal syntax is e.g. to use ***DOMAIN\username*** as username and then your AD password .... This should work right away if done correctly e.g. on the login mask.

I'd also recommend you search this forum and/or Google for "likewise open" ... there are plenty of postings and tutorials out there.

---

### Post by c1utch on 2009-09-30
Hello,

I'm trying to get apache to run as domain user, but no luck.

I joined domain with domain username/password, that has access to MSSQL server. So now, my login is IPCC\rpersak@ubuntu:~$ and AFAIK that should suffice. But it doesn't.

When I try to connect to mssql server, I get:
```

Warning: mssql_connect() [function.mssql-connect]: message: Login failed for user '(null)'. Reason: Not associated with a trusted SQL Server connection. (severity 14) in /home/IPCC/rpersak/www/skripta.php on line 17
```
And yes, I do have
```
mssql.secure_connection = On
```



Any Ideas?

I was trying to run apache server AS user ipcc\rpersak, so I've changed permissions, changed port etc... PS says: 

> 
IPCC\rpersak@ubuntu:~$ ps -U ipcc\rpersak -F
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD


> 
IPCC\rpersak@ubuntu:~$ ps -A -F | grep apache2
root      3476  3411  0   773   644   0 10:52 pts/1    00:00:00 tail -f /var/log/apache2/error.log
1654129887 4075    1  0  5517  6212   0 10:57 ?        00:00:00 apache2 -k start
1654129887 4076 4075  0  5677  6176   0 10:57 ?        00:00:00 apache2 -k start
1654129887 4077 4075  0  5517  3252   0 10:57 ?        00:00:00 apache2 -k start
1654129887 4078 4075  0  5517  3252   0 10:57 ?        00:00:00 apache2 -k start
1654129887 4079 4075  0  5517  3252   0 10:57 ?        00:00:00 apache2 -k start
1654129887 4080 4075  0  5517  3252   0 10:57 ?        00:00:00 apache2 -k start
clutch    4740  4358  0   773   644   0 10:59 pts/3    00:00:00 tail -f /var/log/apache2/access.log
1654129887 6474 4075  0  5517  3252   0 11:00 ?        00:00:00 apache2 -k start


---

