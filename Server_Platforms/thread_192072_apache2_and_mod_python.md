---
title: "apache2 and mod_python"
date: 2006-06-08
forum: Server Platforms
---

### Post by scotoma on 2006-06-08
Hey all,

I am having an issue getting mod_python to run the way I want. I can get it to run using .htaccess with this code in my .htaccess file:

AddHandler mod_python .py
PythonHandler index
PythonDebug On

The olny problem with that is that for every .py file is index is executed. i.e., foo.py executes index.py. This is not what I am looking for. Do I need to modify my apache2.conf or my default virtualserver configuration file in the sites-available folder to get things going correctly? And what changes do i need to make? examples appreciated.

Thanks in advance!

---

### Post by scotoma on 2006-06-08
Update: 

I added this to the bottom of my apache2.conf file

<Directory /var/www/mysite> 
        AddHandler mod_python .py
        PythonHandler index
        PythonDebug On 
 </Directory>

And here is my index.py file

from mod_python import apache

    def handler(req):
        req.content_type = 'text/plain'
        req.write("Hello World!")
        return apache.OK

After restarting apache it now launches a "sava as.." box.

---

### Post by scotoma on 2006-06-08
yet another update:

The same "save as" box appears when I add 

<Directory /var/www/mysite>
AddHandler mod_python .py
PythonHandler index
PythonDebug On
</Directory>

to my default virtualhost file. heres what that looks like:

<virtualHost mysite:80>
    ServerName mysite
    DocumentRoot /var/www/mysite
    ErrorLog /var/log/apache2/error.log

    <Directory /var/www/mysite>
      Options ExecCGI FollowSymLinks
      AddHandler cgi-script .cgi
      AllowOverride all
      Order allow,deny
      Allow from all
    </Directory>
<Directory /var/www/mysite>
        AddHandler mod_python .py
        PythonHandler index
        PythonDebug On
</Directory>

  </VirtualHost>

---

### Post by scotoma on 2006-06-08
one more update:

when I change the index.py file to:

print 'Content-type: text/HTML'
print
print "hello world"

I get a 404 error.

---

### Post by scotoma on 2006-06-08
OK. Just in case anyone else is having the same issue. It works when I change index.py to

def index(req):
    return "hello world"


tada!

---

