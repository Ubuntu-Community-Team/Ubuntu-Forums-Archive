---
title: "Help! Installing apache2 python2.7 mod-wsgi django"
date: 2012-03-21
forum: Server Platforms
---

### Post by Trd002200 on 2012-03-21
Hello everybody. I'm trying to install an Apache web server for Django applications but no success. I'm not very expert in Linux.

I hope somebody could help me.

So, I have a Ubuntu Server 10.04. I've installed apache2. I have a pretty nice interface from ISPConfig for configuring DNS entries, new apache virtualhosts and so on. Everything it's ok.

Like everybody else, I've tried the:
```
sudo apt-get install libapache2-mod-wsgi
```

The python version was 2.6. I've used pythonbrew to upgrade to python2.7. I had some errors, but... I don't know how I did it but now when I type "python" in console, it is Python 2.7.2. I'm not sure if everything it's ok for Apache and mod-wsgi. I have in /usr/local/bin two folders "python2.6" and "python2.7" and a symlink "python" to "python2.7". Looks ok. Please tell me if Apache or mod-wsgi could try to use other version or how to check if everything is fine.

Then, I've installed Django (1.3.1). It was installed under Python2.7 folder. I can import it from console.

When I've tried to run a first django application, I had an error in apache error logs: "No module named django.core.handlers.wsgi". The interesting this was that from python console, I could import django.core.handlers.wsgi.

I've checked:
```
dpkg -l | grep wsgi
```
and the mod-wsgi was version 2.8.

Now, with some help, I have 3.3 (like it should be).

The WSGIScriptAlias Apache directive works and a .wsgi file like this works too:
```

def application(environ, start_response):
    status = '200 OK' 
    output = 'Hello World!'    
    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)

    return [output]

```

Now, after all this, when I run a Django application the error is:
```

ImproperlyConfigured: Error importing middleware django.middleware.csrf: "No module named csrf"

```
If I comment the import django.middleware.csrf line, the error will be that it cannot import the next middleware needed. So it looks like it doesn't know where Django is, or something like this.

My .wsgi file is:
```

import os,sys

path = '/var/www/transimart.ro/web'
path2 = '/var/www/transimart.ro'
if path not in sys.path: sys.path.append(path)
if path2 not in sys.path: sys.path.append(path2)

os.environ['DJANGO_SETTINGS_MODULE'] = 'web.settings'
import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()

```
The django application is in /var/www/transimart.ro/web, and the wsgi file: /var/www/transimart.ro/web.wsgi.
The apache directive is:
```
WSGIScriptAlias / /var/www/transimart.ro/web.wsgi
```

How can I do some debugging, to see where is the problem?
Thank you. If any other information is needed, please tell me.

---

