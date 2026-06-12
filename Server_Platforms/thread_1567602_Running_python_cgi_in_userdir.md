---
title: "Running python cgi in userdir"
date: 2010-09-04
forum: Server Platforms
---

### Post by saphil on 2010-09-04
I have a neat little set-up to run home folder-based web sites.  I want to run cgi out of the folder

```


wolf@telcontar:~/www/public_html$ ls -lR
.:
total 48
-rwxr-xr-x 1 wolf wolf  430 2010-09-03 03:53 basicc.py
lrwxrwxrwx 1 wolf wolf   16 2010-09-04 01:25 cgi-bin -> /usr/lib/cgi-bin
-rw-r--r-- 1 wolf wolf  304 2010-09-03 09:53 index.html
-rwxr-xr-x 1 wolf wolf 1033 2010-09-03 04:19 vbasiccc.py
-rwxr-xr-x 1 wolf wolf  557 2010-09-03 04:02 vbasicc.py
-rwxr-xr-x 1 wolf wolf  792 2010-09-03 04:05 vbcook.py
-rwxr-xr-x 1 wolf wolf  453 2010-09-03 04:10 vbmails.py


```I just discovered that the ls -R command didn't show the contents of the syn-linked folder cgi-bin

```
wolf@telcontar:~/www/public_html/cgi-bin$ ls -l
total 24
-rwxr-xr-x 1 root root  430 2010-09-04 01:21 basicc.py
-rwxr-xr-x 1 root root 2386 2010-05-23 11:34 gsearch.cgi
-rwxr-xr-x 1 root root 1033 2010-09-04 01:21 vbasiccc.py
-rwxr-xr-x 1 root root  557 2010-09-04 01:21 vbasicc.py
-rwxr-xr-x 1 root root  792 2010-09-04 01:21 vbcook.py
-rwxr-xr-x 1 root root  453 2010-09-04 01:21 vbmails.py


```The python code is the same in both the webroot folder and the cgi-bin folder, except for ownership.

I found this thread: [http://ubuntuforums.org/showthread.php?t=91101](http://ubuntuforums.org/showthread.php?t=91101) 
that showed that I had not added the right handler to the default site in /etc/apache2/sites-available/default
When I added the handler there, a test python ap worked from /var/www, which is the default webroot.

I am wondering if I have to add it to the userdir.conf file as well...

```

<IfModule mod_userdir.c>
        UserDir www/public_html
        UserDir disabled root

        <Directory /home/*/www/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>

                [B]AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On[/B]

        </Directory>
</IfModule>


```Wish me luck

It worked!

---

