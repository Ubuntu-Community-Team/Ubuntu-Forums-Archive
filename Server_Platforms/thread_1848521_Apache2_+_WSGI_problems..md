---
title: "Apache2 + WSGI problems."
date: 2011-09-22
forum: Server Platforms
---

### Post by garfonzo on 2011-09-22
OK I don't what I'm doing wrong here. I have a Linode VPS running Ubuntu. I installed Django 1.3, Apache2, and mod-WSGI. I created my (extermely simple) website, slapped in some images, have a CSS sheet, have a favicon.ico and it works beautifully with the Django test server. The site looks precisely as it should -- all the images load, the CSS is working properly, etc.

Then I tried running the site with Apache and it won't work. Here are my relevant configuration files:

Apache sites-enabled/default:

```
<VirtualHost *:80>
    ServerAdmin ***@***.com

    WSGIScriptAlias / /srv/www/django_site/django.wsgi
    AliasMatch ^/([^/]*\.css) /srv/www/django_site/static_media/css/$1
    Alias /static_media/ /srv/www/django_site/static_media/

    <Directory /srv/www/django_site>
        Options -Indexes
        Order deny,allow
        Allow from all
    </Directory>

    ErrorLog /srv/www/logs/error.log
    LogLevel warn

    CustomLog /srv/www/logs/access.log combined

Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
    Options MultiViews FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
```

My WSGI script (django.wsgi):
```

import os
import sys
path = '/srv/www'
if path not in sys.path:
   sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'django_site.settings'

import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()

```

When I try to surf to the website, I get a 500 internal error page. The traceback is this:

```

    Traceback (most recent call last):

 File "/usr/local/lib/python2.6/dist-packages/django/core/handlers/base.py", line 111, in get_response
   response = callback(request, *callback_args, **callback_kwargs)

 File "/srv/www/django_site/quote/views.py", line 9, in about
   return render_to_response("pages/about.html", context_instance=RequestContext(request))

 File "/usr/local/lib/python2.6/dist-packages/django/shortcuts/__init__.py", line 20, in render_to_response
   return HttpResponse(loader.render_to_string(*args, **kwargs), **httpresponse_kwargs)

 File "/usr/local/lib/python2.6/dist-packages/django/template/loader.py", line 181, in render_to_string
   t = get_template(template_name)

 File "/usr/local/lib/python2.6/dist-packages/django/template/loader.py", line 157, in get_template
   template, origin = find_template(template_name)

 File "/usr/local/lib/python2.6/dist-packages/django/template/loader.py", line 128, in find_template
   loader = find_template_loader(loader_name)

 File "/usr/local/lib/python2.6/dist-packages/django/template/loader.py", line 95, in find_template_loader
   mod = import_module(module)

 File "/usr/local/lib/python2.6/dist-packages/django/utils/importlib.py", line 35, in     import_module
   __import__(name)

 File "/usr/local/lib/python2.6/dist-packages/django/template/loaders/app_directories.py", line 23, in <module>
   raise ImproperlyConfigured('ImportError %s: %s' % (app, e.args[0]))

ImproperlyConfigured: ImportError quote: No module named quote

```

The "quote" module is simply a django app within the "django_site" project directory. I don't know why it is claiming that there is no module named quote since that module does indeed exist, and it works fine in the Django test server.

This should be straight forward. What boggles my mind is that I have a second Linode VPS running Ubuntu with a different website that has the exact configuration files and it works perfectly.

I bet this is some simple tweak and it will all work.

Any ideas?

Thanks!

---

