---
title: "moving CGI dir to /var/www"
date: 2012-12-18
forum: Server Platforms
---

### Post by micahpage on 2012-12-18
I have had files /usr/lib/cgi-bin working fine, but I would like to move them to /var/www. So i created /var/www/cgi
```
sudo chmod 755 /var/www/cgi
```and then copied all files to new dir:
```
sudo cp /usr/lib/cgi-bin/*.py /var/www/cgi
``````
        ScriptAlias /cgi-bin/ /var/www/cgi/
        <Directory "/var/www/cgi/">
#        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#        <Directory "/usr/lib/cgi-bin">
#               #AllowOverride None
#               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch Includes
#               Order allow,deny
#               Allow from all
#               AddHandler cgi-script .py 
#               AddHandler default-handler .html .htm  
#               AddType text/html .shtml
#               AddHandler server-parsed .html
#               AddHandler server-parsed .shtml
#               DirectoryIndex index.shtml index.html
#               AddOutputFilter INCLUDES .shtml

                Options +ExecCGI Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                AddHandler cgi-script .py
                AddHandler cgi-script .cgi
                AddHandler default-handler .html .htm
                AddType text/html .shtml
                AddHandler server-parsed .html
                AddHandler server-parsed .shtml
                DirectoryIndex index.shtml index.html
                AddOutputFilter INCLUDES .shtml
                AddHandler php5-script php
        </Directory>

```file permissions for files,dir, and parent dirs:
```
drwxr-xr-x  14 root root  4096 Nov  3 07:23 var
``````
drwxrwxr-x 13 www-data www-data 4096 Dec 18 18:03 www

``````
drwxr-xr-x  2 root      root           4096 Dec 18 18:05 cgi

``````
metulburr@server:/var/www/cgi$ ls -l
total 28
-rwxr-xr-x 1 root root  442 Dec 18 18:05 cgi_basic2.py
-rwxr-xr-x 1 root root  442 Dec 18 18:05 cgi_basic.py
-rwxr-xr-x 1 root root  789 Dec 18 18:05 client_ip.py
-rwxr-xr-x 1 root root 1183 Dec 18 18:05 portingguide.py
-rwxr-xr-x 1 root root 8410 Dec 18 18:05 versiondiff.py
metulburr@server:/var/www/cgi$ 

```So when i try to execute the python scripts from /var/www/cgi, i get a 403 error, but yet the cgi dir has the same perm, but i can access the listing of that dir? How can i set the new cgi directory within /var/www?


EDIT:
after checking the error logs when i try to access /var/www/cgi/somepythonprogram.py via browser, i get the error:
Options ExecCGI is off in this directory: /var/www/cgi/portingguide.py

but yet i have "+ExecCGI" in the options? What is going on?

the full config is:
[http://codepad.org/tMrScBGa](http://codepad.org/tMrScBGa)

---

