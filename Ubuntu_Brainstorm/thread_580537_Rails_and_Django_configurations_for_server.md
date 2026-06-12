---
title: "Rails and Django configurations for server"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by unixhead on 2007-10-18
Rails and Django configurations for server would be a great addition to existing mail, LAMP, etc configurations.

---

### Post by Zdravko on 2007-10-19
I wonder why these are not here yet.

---

### Post by tminuszero on 2007-10-25
> **unixhead said:**
> Rails and Django configurations for server would be a great addition to existing mail, LAMP, etc configurations.

:confused:

apt-get install rails
apt-get install python-django

What are you asking for? Do you want the Rails package to automatically configure your apache2 virtualhost information? There's too many variables there for the installer to be successful. What if I want to use lighttpd for my rails apps instead of apache2? What if I have 100 sites enabled, but only want Rails for one site? What if I want to run it via wsgi, fastcgi, etc?

As for Django, it works fine. Great, in fact. But I'm running trunk and I installed manually, but the configuration was brutally simple (once I figured out what I was doing). Not sure what could be done by the installer.

If you have any Django installation questions, just ask.

---

### Post by izamryan on 2008-06-06
This idea may still have some merit.

I've been able to quite happily configure my stock Ubuntu 8.04 & apache2 install to use virtual hosts in moinmoin, ohobb2, phpmyadmin, Drupal5 and Gallery2.

But when I come to Django, I'm quite stuck.

This is what I've got so far, but it doesn't work properly. I've managed to get it to work with FastCGI, but I have to manually start & restart the Django project with manage.py

<VirtualHost *:80>
        ServerName caduceus
        ServerAlias *.caduceus
        DocumentRoot /home/djangosites/caduceus/

        ErrorLog /var/log/apache2/caduceus.selfip.com.error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/caduceus.selfip.com.access.log combined

        <Location "/">
                SetHandler python-program 
                PythonHandler django.core.handlers.modpython 
                SetEnv DJANGO_SETTINGS_MODULE caduceus.settings 
                PythonDebug On 
                PythonPath "['/home/djangosites/caduceus/settings.py'] + sys.path"      
        </Location> 
        <Location "/admin_media/"> 
                SetHandler None 
        </Location> 
        <Location "/assets/">
                SetHandler None
        </Location>
</VirtualHost>

---

### Post by tminuszero on 2008-06-08
> **izamryan said:**
> 
        <Location "/">
                SetHandler python-program 
                PythonHandler django.core.handlers.modpython 
                SetEnv DJANGO_SETTINGS_MODULE caduceus.settings 
                PythonDebug On 
                PythonPath "['/home/djangosites/caduceus/settings.py'] + sys.path"      
        </Location> 


Assuming that /home/djangosites/caduceus/ is where your project is stored, try the following:

```

        <Location "/">
                SetHandler python-program
                PythonPath "['/home/djangosites/'] + sys.path"
                PythonHandler django.core.handlers.modpython
                SetEnv DJANGO_SETTINGS_MODULE caduceus.settings
                PythonDebug On
        </Location>

```

Note - PythonPath should not link directly to your settings file (as far as I know).

This configuration seems to work for me. Let me know if it works for you. :)

---

### Post by izamryan on 2008-06-11
har har har.

I switched to lighttpd ... and it seems to be easier to configure, and serves faster ? Haven't got real benchmarks, that's just a layman's observation.

But I got all my web apps configured and working just fine now.

Django is configured as below, in "20-caduceus.conf" in /etc/lighttpd/conf-available.

```

$HTTP["host"] == "caduceus.selfip.com" {
        server.document-root = "/home/djangosites/caduceus"
        fastcgi.server = (
                "/caduceus.fcgi" => (
                "main" => (
                        # Use host / port instead of socket for TCP fastcgi
                        "host" => "127.0.0.1",
                        "port" => 3033,
                        # "socket" => "/home/djangosites/caduceus/caduceus.sock",
                        "check-local" => "disable",
                )
        ),
)
alias.url = (
    "/media/" => "/usr/share/python-support/python-django/django/contrib/admin/media/",
)

url.rewrite-once = (
    "^(/media.*)$" => "$1",
    "^/favicon\.ico$" => "/media/favicon.ico",
    "^(/.*)$" => "/caduceus.fcgi$1",
)


}

```

Then within rc.local I just have a line that says:

```

sudo -u www-data python /home/djangosites/caduceus/manage.py runfcgi method=threaded host=127.0.0.1 port=3033
```

---

### Post by alexisbellido on 2008-10-18
This tutorial about [setting up Django with Apache, mod_python, mod_proxy and Lighttpd]("http://ventanazul.com/webzine/tutorials/setup-apache-lighttpd-django-ubuntu") on Ubuntu may help you as well. 

Cheers.

---

### Post by dracule on 2008-10-20
I got django set up on apache in i think 2 config files. I gave up on rails. Django is extremely easy to set up, at least for me.

---

