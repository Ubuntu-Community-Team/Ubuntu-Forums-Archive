---
title: "Python and Apache2 (mod_python)"
date: 2005-11-16
forum: Server Platforms
---

### Post by fnando on 2005-11-16
How to configure Apache2 to run .py files in the same way it runs .php files? I mean, without having to keep the files on cgi-bin directory or to create handlers.

Cheers!

---

### Post by WelterPelter on 2006-03-04
I have the same question. I've got php running fine. I used synaptic to install the libapache-mod-python2.4  In the apache2/mods-available/ dir there's a mod-python load file but no mod-python conf file. 
Little help?

---

### Post by oscar on 2006-03-04
[EDIT] WelterPelter, I just saw that you said you used libapache-mod-python2.4 which means you are using apache not apache2. I wrote this for apache2, I dont know how different they are but i guess it wont work, i suggest installing apache2 and libapache2-mod-python[/EDIT]

To enable mod_python:
```
cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/mod_python.load mod_python.load
```
To enable the parsing of .py scripts:
```
cd /etc/apache2/sites-available/
sudo gedit default
```
On line 10 you should have:
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```
Change it to:
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all

                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On

                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```
Save the file.
Now restart your server:
```
sudo /etc/init.d/apache2 restart
```

Test it:
```
sudo gedit /var/www/test.py
```
insert these lines:
```
def index(req):
  return "Test successful";
```
and it should work
visit [http://localhost/test.py](http://localhost/test.py) and it should say "Test successful" in plain text

---

### Post by WelterPelter on 2006-03-05
Thanks, oscar, that worked perfectly. I did have the wrong mod-python, as well. 
Now it's running fine.
:KS

---

### Post by oscar on 2006-03-06
Good, glad I could help. I had been playing around the day before and wanted to do exactly the same thing, thought I would share. I still need to fiddle around with the handlers a bit before I understand totally but I dont really have the time and it works.

Some interesting links I found:
- Python Server Pages, Python but in an embedded form like php:
[http://programmer-art.org/mod_python](http://programmer-art.org/mod_python)
- The python tutorial
[http://modpython.org/live/current/doc-html/](http://modpython.org/live/current/doc-html/)

Looking at my default site config I realise that the python handling should probably be put in the /var/www Directory definition, not the / one, not sure if putting it in / is actually bad but its not what we want. I will update my post before

---

### Post by WelterPelter on 2006-03-06
You're a mind  reader. I was just digging into how to do that stuff moments ago, so these links are completely useful. 

Time to get back to work, however. Thanks, again.

---

### Post by chiefy on 2007-01-12
Kinda at a loss, wondering if someone can help?

I have mod_python 3.2.8 python 2.4.4c1 apache 2.0.55 installed on Edgy. I have followed the instructions above, and I have a test script - /var/www/test.py when I go to that URL ([http://my.local.host/test.py](http://my.local.host/test.py)) the browser opens a window with "save to.." box. However, when i go to [http://my.local.host/test.py/](http://my.local.host/test.py/) the script works. I have added py to my /etc/mime.types. Any ideas?

---

### Post by keyvez on 2007-01-21
I was having trouble even after configuring it in the way suggested above, and it worked when I renamed the file.

---

### Post by mvaranda on 2007-02-16
Hi All,

I have followed this procedure and all looks fine. However, Browser gets a msg that file was not found. Apache log looks fine. Interesting is that if I add a wrong line in my python script I get the proper error message in the Browser. But when script is free of error then I get this "file not found" error. File is 777.



This is happening in both 6.06 and Edgy.

here my script:


#!/usr/bin/python

import sys
import time

# Following line causes error to be sent to browser
# rather than to log file (great for debug!)

sys.stderr = sys.stdout

print "Content-type: text/html\n"

print """
<html>
<head><title>A page from Python</title></head>
<body>
<h4>This page is generated by a Python script!</h4>
The current date and time is """

now = time.gmtime()
displaytime = time.strftime("%A %d %B %Y, %X",now)

print displaytime,

print """
<hr>
Well House Consultants demonstration
</body>
</html>
"""

Thanks in advance.

---

### Post by NewWithoutClue on 2007-02-17
> **mvaranda said:**
> Hi All,

I have followed this procedure and all looks fine. However, Browser gets a msg that file was not found. Apache log looks fine. Interesting is that if I add a wrong line in my python script I get the proper error message in the Browser. But when script is free of error then I get this "file not found" error. File is 777.



This is happening in both 6.06 and Edgy.

here my script:


#!/usr/bin/python

import sys
import time

# Following line causes error to be sent to browser
# rather than to log file (great for debug!)

sys.stderr = sys.stdout

print "Content-type: text/html\n"

print """
<html>
<head><title>A page from Python</title></head>
<body>
<h4>This page is generated by a Python script!</h4>
The current date and time is """

now = time.gmtime()
displaytime = time.strftime("%A %d %B %Y, %X",now)

print displaytime,

print """
<hr>
Well House Consultants demonstration
</body>
</html>
"""

Thanks in advance.

I came up with this in two seconds.. not to brag or anything..

```

#!/usr/bin/python

import sys
import time

def index(req):

# Following line causes error to be sent to browser
# rather than to log file (great for debug!)

        sys.stderr = sys.stdout

        #print "Content-type: text/html\n"

        #print """
        blah1 = """<html>
        <head><title>A page from Python</title></head>
        <body>
        <h4>This page is generated by a Python script!</h4>
        The current date and time is """

        now = time.gmtime()
        displaytime = time.strftime("%A %d %B %Y, %X",now)

        #print displaytime,
        blah1 += displaytime

        #print """
        blah1 += """
        <hr>
        Well House Consultants demonstration
        </body>
        </html>
        """
        return blah1

```

Regards,
Paul

---

### Post by mvaranda on 2007-02-19
Many thanks, Paul. IT WORKS !

But there are so many tutorials/samples just using stdio outputs so why they do not works ? Anyways... I will try to leatn more about it.

Cheers

---

### Post by martinbures on 2007-04-29
I have a question.  I am trying to have the user upload a file to the server, which will be saved and processed.

Here is my code:
html = """
<html><body>
Advanced Development
<p>

<p>
Please Select a File to Parse
<p>
The resulting files will be placed in the source directory.
<form action="index.py/upload" method="POST" enctype="multipart/form-data">
  <input type="file" name="fileupload"/>
  <input type="submit" value="Upload!">
</form>
</body></html>
"""

import os

def index(req):
    return html

def upload(req):
    req.content_type = "text/plain"
    fp = req.form['fileupload'].file
    
    filename_to_write = os.path.split( req.form['fileupload'].filename )[ 1 ]
    req.write( filename_to_write )

    fod = open( filename_to_write, 'w' )
    
    data = fp.read()
    #req.write( data )
    
    fp.close()

    return #dir( req.form['fileupload'] )

Here is the error message that I get:
Mod_python error: "PythonHandler mod_python.publisher"

Traceback (most recent call last):

  File "/usr/lib/python2.4/site-packages/mod_python/apache.py", line 299, in HandlerDispatch
    result = object(req)

  File "/usr/lib/python2.4/site-packages/mod_python/publisher.py", line 213, in handler
    published = publish_object(req, object)

  File "/usr/lib/python2.4/site-packages/mod_python/publisher.py", line 412, in publish_object
    return publish_object(req,util.apply_fs_data(object, req.form, req=req))

  File "/usr/lib/python2.4/site-packages/mod_python/util.py", line 439, in apply_fs_data
    return object(**args)

  File "/var/www/index.py", line 27, in upload
    fod = open( filename_to_write, 'w' )

IOError: [Errno 13] Permission denied: '1.08.07 R-2.zol'

I assume that I don't have some permissions set up properly?  How can I fix this?

Thanks.
martin.

---

### Post by alecjw on 2007-06-01
> **oscar said:**
> [EDIT] WelterPelter, I just saw that you said you used libapache-mod-python2.4 which means you are using apache not apache2. I wrote this for apache2, I dont know how different they are but i guess it wont work, i suggest installing apache2 and libapache2-mod-python[/EDIT]

To enable mod_python:
```
cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/mod_python.load mod_python.load
```
To enable the parsing of .py scripts:
```
cd /etc/apache2/sites-available/
sudo gedit default
```
On line 10 you should have:
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```
Change it to:
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all

                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On

                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
```
Save the file.
Now restart your server:
```
sudo /etc/init.d/apache2 restart
```

Test it:
```
sudo gedit /var/www/test.py
```
insert these lines:
```
def index(req):
  return "Test successful";
```
and it should work
visit [http://localhost/test.py](http://localhost/test.py) and it should say "Test successful" in plain text

Why cant it do this automatically when you install mod_python?

---

### Post by md5hash on 2007-09-13
whats wrong i created test.py in /var/www/ and its really there but it cant be found

> Not Found

The requested URL /test.py was not found on this server.
-------------------------------------------------------------------------
Apache/2.2.3 (Ubuntu) mod_python/3.2.10 Python/2.5.1 PHP/5.2.1 Server at localhost Port 80

---

### Post by ronaldo1 on 2007-09-17
i have the same problem
says it cant be found but its there

Apache/2.2.3 (Ubuntu) mod_python/3.2.10 Python/2.5.1 PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at localhost Port 443

---

### Post by pcit on 2007-09-23
Thanks Oscar,
Your tutorial is simple and does WORKS!!!

Sincerely,

Patrick

---

### Post by bastienauneau on 2007-10-04
Hello

I'm actually programming with mod-python and apache on ubuntu. I experimented many time the same problem : i changed my code and when i ask to the webbrowser to refresh and so show me the new version of my code being interpreted, i can see old version, sometimes mixed with others or new parts of code. What do i have to change to avoid this ? I this because of the browser, python or apache ?

thanks

bastien

---

### Post by hyperair on 2007-11-24
I'm really not sure about this, but you might need to restart Apache after making the changes.

---

### Post by inuwashi on 2008-05-15
This is taken from [http://www.djangoproject.com/](http://www.djangoproject.com/).
Worked perfectly for me. The browser some times needs to be refreshed twice but thats it. :-\"

> 
Running a development server with mod_python

If you use mod_python for your development server, you can avoid the hassle of having to restart the server each time you make code changes. Just set **MaxRequestsPerChild 1** in your httpd.conf (my edit) or apache2.conf (/my edit)file to force Apache to reload everything for each request. But don&#8217;t do that on a production server, or we&#8217;ll revoke your Django privileges.


---

### Post by pocketcookies on 2008-05-21
To everyone getting the 404: File not found error when trying to use mod_python, I had the same problem.

For my version of Apache (I'm running Ubuntu Hardy Heron (8.04)), there are a number of reasons it will give a 404 besides the file actually not being found.

It appears that when using mod_python, Apache will call a function (which you need to define) named "index."  Whatever string this function returns will be used as the page itself.  Since you didn't define a index function, test.py won't actually return any text so Apache seems to be interpreting this lack of text as a missing file, thus resulting in a 404.

To fix this, just add the following:

```
#Some code can go here.
def index(req):
    #More code can go here.
    return "The entire HTML code for your web page."

#Possibly more code can go here.
```

---

