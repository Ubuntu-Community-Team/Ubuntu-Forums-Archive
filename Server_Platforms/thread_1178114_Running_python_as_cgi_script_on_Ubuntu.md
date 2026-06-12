---
title: "Running python as cgi script on Ubuntu"
date: 2009-06-04
forum: Server Platforms
---

### Post by vifillr on 2009-06-04
Hi
I have Ubuntu 9.04 installed (Desktop Edition). I want to use this as a local test server for my web project, and has therefore installed apache and mysql ++. 

I want the server to run python files as scripts to generate html by using the cgi module. Yes, I know there are more efficient and probably better ways to to this, but at this stage I do not want to use mod_python, cherrypy etc. 

Apache is running ok, the message /var/www/index.html is working in a web browser pointing at 127.0.1.1. 

However, I have a file index.py containing

#!/usr/bin/python


import cgitb

cgitb.enable()

import cgi

print 'Content-type: text/html'
print ''

... and then some html here...

When pointing the server to [http://127.0.1.1/index.py](http://127.0.1.1/index.py) I am asked to download the file. 

I have tried to add AddHandler cgi-script .py to /etc/apache2/apache2.conf
and to add 
<Directory "/var/www/">
        Options FollowSymLinks ExecCGI
</Directory>
to /etc/apache2/sites-enabled/000-default 

Any help would be appreciated!

---

### Post by vifillr on 2009-06-05
Arg, the solution was very simple:

/etc/apache2/sites-enabled/000-default should be changed to
<Directory "/var/www/">
    Options FollowSymLinks +ExecCGI
    AllowOverride None
</Directory>

Remember the + before ExecCGI...


/Vifillr  





> **vifillr said:**
> Hi
I have Ubuntu 9.04 installed (Desktop Edition). I want to use this as a local test server for my web project, and has therefore installed apache and mysql ++. 

I want the server to run python files as scripts to generate html by using the cgi module. Yes, I know there are more efficient and probably better ways to to this, but at this stage I do not want to use mod_python, cherrypy etc. 

Apache is running ok, the message /var/www/index.html is working in a web browser pointing at 127.0.1.1. 

However, I have a file index.py containing

#!/usr/bin/python


import cgitb

cgitb.enable()

import cgi

print 'Content-type: text/html'
print ''

... and then some html here...

When pointing the server to [http://127.0.1.1/index.py](http://127.0.1.1/index.py) I am asked to download the file. 

I have tried to add AddHandler cgi-script .py to /etc/apache2/apache2.conf
and to add 
<Directory "/var/www/">
        Options FollowSymLinks ExecCGI
</Directory>
to /etc/apache2/sites-enabled/000-default 

Any help would be appreciated!

---

### Post by ZeldeR on 2009-06-05
you can install Python Server => karrigell  ;)

---

