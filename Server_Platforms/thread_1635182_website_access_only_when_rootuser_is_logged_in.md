---
title: "website access only when rootuser is logged in"
date: 2010-12-01
forum: Server Platforms
---

### Post by marue on 2010-12-01
After a battle with Ubuntu, Django, Apache and wsgi i could reach the website i set up from another computer via ip-adress (10.37.129.6). i then restarted the server and after booting tried to access the website from outside - permission to / denied with the usual 403 error. trying to fix that, i logged in to the server and suddenly the website was available again. typed logout on the server - no access wt. 403. logged in - website can be accessed.

i somehow suspect this is some strange permission problem, but i don't have a clue where to start searching. errorlogs just contain information that a / access request has been denied. for further information here are my:

------------------------------ apache site configuration
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        WSGIScriptAlias / /home/marue/LFS/lfs.wsgi

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/marue/LFS/>
                Options Indexes FollowSymLinks MultiViews ExecCGI

                AddHandler cgi-script .cgi
                AddHandler wsgi-script .wsgi

                AllowOverride None
                Order allow,deny
                Allow from all
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

</VirtualHost>

------------------------------ wsgi file
import os,sys

sys.path.append('/home/marue/LFS')
sys.path.append('/home(marue/LFS/bin/django')

os.environ['DJANGO_SETTINGS_MODULE']='lfs_project.settings'

sys.path = [
    '/home/marue/LFS/eggs/django_lfs-0.5.0b6-py2.6.egg',
    '/home/marue/LFS/eggs/Pillow-1.5-py2.6-linux-x86_64.egg',
    '/home/marue/LFS/eggs/gunicorn-0.11.2-py2.6.egg',
    '/home/marue/LFS/eggs/djangorecipe-0.20-py2.6.egg',
    '/home/marue/LFS/eggs/zc.recipe.egg-1.3.2-py2.6.egg',
    '/home/marue/LFS/eggs/zc.buildout-1.5.2-py2.6.egg',
    '/home/marue/LFS/eggs/setuptools-0.6c12dev_r85381-py2.6.egg',
    '/home/marue/LFS/eggs/django_contact_form-0.3-py2.6.egg',
    '/home/marue/LFS/eggs/django_paypal-0.1.2-py2.6.egg',
    '/home/marue/LFS/eggs/django_tagging-0.3.1-py2.6.egg',
    '/home/marue/LFS/eggs/django_reviews-0.2.1-py2.6.egg',
    '/home/marue/LFS/eggs/django_pagination-1.0.7-py2.6.egg',
    '/home/marue/LFS/eggs/django_portlets-1.0b4-py2.6.egg',
    '/home/marue/LFS/eggs/django_lfstheme-0.5.0b5-py2.6.egg',
    '/home/marue/LFS/parts/django',
    '/home/marue/LFS/parts/django',
    '/home/marue/LFS',
    '/home/marue/LFS/parts',
    '/home/marue/LFS/lfs_project',
    ] + sys.path

import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()

---

### Post by marue on 2010-12-08
i'm still seeking help on this topic. couldn't find a solution yet.

---

