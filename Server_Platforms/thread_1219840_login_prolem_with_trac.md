---
title: "login prolem with trac"
date: 2009-07-22
forum: Server Platforms
---

### Post by wangfeng3769 on 2009-07-22
[SIZE=4]hello guys ,I installed  trac on ubuntu9.04,but something bad happened,I can't find out the reasons .
[/SIZE][SIZE=4][COLOR=DarkOrange]my configuration file[/COLOR][/SIZE][SIZE=4]:
sudo gedit /etc/apache2/mods-enabled/dav_svn.conf
and add the blow to the file 
[/SIZE][SIZE=4][COLOR=Red]<Location /svn>
  DAV svn
  SVNPath /svn
  SVNListParentPath Off

  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/dav_svn.passwd
  AuthzSVNAccessFile /etc/apache2/authz_svn.access

  Require valid-user
</Location>[/COLOR][/SIZE][SIZE=4]

sudo gedit  /etc/apache2/sites-available/trac
add the below to the file 
[/SIZE][SIZE=4][COLOR=Magenta]
[/COLOR][/SIZE][SIZE=4][COLOR=Magenta]listen 8080
NameVirtualHost *:8080


<VirtualHost *:8080>

        ServerAdmin webmaster@localhost
        ServerName trac.example.com
        DocumentRoot /var/www
        ErrorLog /var/log/apache2/error.trac.log
        CustomLog /var/log/apache2/access.trac.log combined

        <Location /trac>
                SetHandler mod_python
                PythonInterpreter main_interpreter
                PythonHandler trac.web.modpython_frontend
                PythonOption TracEnvParentDir /var/lib/trac
                PythonOption TracUriRoot /trac 
                PythonOption PYTHON_EGG_CACHE /tmp
        </Location>

       
        <LocationMatch "/trac/[^/]+/login">
               AuthType Basic
               AuthName "Trac"
               AuthUserFile /etc/apache2/dav_svn.passwd                              
               SVNPath /var/lib/svn
               AuthzSVNAccessFile /etc/apache2/authz_svn.access
               #AuthzSVNAccessFile /etc/apache2/authz_svn.access
               Require valid-user
        </LocationMatch>


</VirtualHost>
[/COLOR][/SIZE][SIZE=4]

then resart the apache2 ,it works ,and the trac page appears ,but when I clink the "login" button ,it  gives a bad respond ,the trac. log reads as below 
"
[/SIZE][SIZE=4][COLOR=Blue][Wed Jul 22 17:28:11 2009] [error] [client 127.0.1.1] File does not exist: /var/www/favicon.ico
[Wed Jul 22 17:28:14 2009] [error] [client 127.0.1.1] File does not exist: /var/www/favicon.ico
[Wed Jul 22 17:28:27 2009] [error] [client 127.0.1.1] user wangfeng: authentication failure for "/trac/jakj/login": Password Mismatch, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:28:33 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:29:18 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:29:37 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:31:08 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj/search](http://127.0.1.1:8080/trac/jakj/search)
[Wed Jul 22 17:31:22 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj/search](http://127.0.1.1:8080/trac/jakj/search)
[Wed Jul 22 17:36:15 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:37:34 2009] [error] [client 127.0.1.1] (9)Bad file descriptor: Could not open password file: (null), referer: [http://127.0.1.1:8080/trac/jakj/browser](http://127.0.1.1:8080/trac/jakj/browser)
[Wed Jul 22 17:37:39 2009] [error] [client 127.0.1.1] (9)Bad file descriptor: Could not open password file: (null), referer: [http://127.0.1.1:8080/trac/jakj/browser](http://127.0.1.1:8080/trac/jakj/browser)
[Wed Jul 22 17:40:33 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj/](http://127.0.1.1:8080/trac/jakj/)
[Wed Jul 22 17:43:27 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:45:25 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:45:48 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[Wed Jul 22 17:48:42 2009] [error] [client 127.0.1.1] Access denied: 'wangfeng' GET login:/trac/jakj/login, referer: [http://127.0.1.1:8080/trac/jakj](http://127.0.1.1:8080/trac/jakj)
[/COLOR][/SIZE][SIZE=4]"
I really don't know how to continue my work ,guys who know the answer ,give your reply .
[/SIZE][SIZE=4][COLOR=DarkSlateGray]thank you [/COLOR][/SIZE][SIZE=4]:popcorn:

[/SIZE]
[SIZE=4]I post my problem here ,I hope whoever meets the same the problem and has solved it  ,share your answer with me .thank you again[/SIZE].

---

### Post by BbUiDgZ on 2009-07-22
see the "[Configuring Authentication](http://trac.edgewall.org/wiki/TracInstall)" section on the trac website.
EDIT: also see [here](http://trac.edgewall.org/wiki/TracPermissions)

---

### Post by wangfeng3769 on 2009-07-22
thank you so much ,I have made it :KS:P:):o:D

---

