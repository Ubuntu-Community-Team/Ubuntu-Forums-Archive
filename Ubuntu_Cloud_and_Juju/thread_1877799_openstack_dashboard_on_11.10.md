---
title: "openstack dashboard on 11.10"
date: 2011-11-08
forum: Ubuntu Cloud and Juju
---

### Post by Temujiin on 2011-11-08
Does anyone have the openstack dashboard working on 11.10?  I can apt-get openstack-dashboard but it does not seem to install things properly.

I got the webserver running doing a 

 dashboard/manage.py runserver 0.0.0.0:8000

but I get the following error:

Traceback (most recent call last):    File "/usr/lib/pymodules/python2.7/django/core/servers/basehttp.py", line 283, in run     self.result = application(self.environ, self.start_response)    File "/usr/lib/pymodules/python2.7/django/contrib/staticfiles/handlers.py", line 68, in __call__     return self.application(environ, start_response)    File "/usr/lib/pymodules/python2.7/django/core/handlers/wsgi.py", line 250, in __call__     self.load_middleware()    File "/usr/lib/pymodules/python2.7/django/core/handlers/base.py", line 47, in load_middleware     raise exceptions.ImproperlyConfigured('Error importing middleware %s: "%s"' % (mw_module, e))  ImproperlyConfigured: Error importing middleware django_openstack.middleware.keystone: "No module named openstackx"

Openstackx lib is installed.

Any ideas?

---

### Post by fhrosa on 2011-11-14
Same issue here but with Pootle on Ubuntu 11.10.

Whereas usually I would fire a browser and point to 8080 and get my nice Pootle server, now I am getting:

Traceback (most recent call last):

  File "/usr/lib/pymodules/python2.7/django/core/servers/basehttp.py", line 283, in run
    self.result = application(self.environ, self.start_response)

  File "/usr/lib/pymodules/python2.7/django/contrib/staticfiles/handlers.py", line 68, in __call__
    return self.application(environ, start_response)

  File "/usr/lib/pymodules/python2.7/django/core/handlers/wsgi.py", line 250, in __call__
    self.load_middleware()

  File "/usr/lib/pymodules/python2.7/django/core/handlers/base.py", line 47, in load_middleware
    raise exceptions.ImproperlyConfigured('Error importing middleware %s: "%s"' % (mw_module, e))

ImproperlyConfigured: Error importing middleware pootle_misc.middleware.siteconfig: "No module named thread_support"

This is very frustrating. This is Ubuntu server... you do not expect a production server to just go out of work like this. Thinking seriously about migrating the server to Debian Stable.

---

### Post by Temujiin on 2011-11-17
For the  meantime I am using Hydrafox which works fairly well however it is not for the faint of heart to use.

---

### Post by fhrosa on 2011-11-27
Two weeks after the first reports and still no answer. Did a apt-get update && apt-get upgrade hoping a newer python/django version would fix it but it's hopeless. 

Switching to Debian stable this weekend. I do not consider Ubuntu server a viable option any more. Breaking a production server and no fix in 2 weeks? This is completely absurd.

---

### Post by tspycher on 2011-12-08
Hi 

I've ran in the same problem! I was able to fix it by installing the current python modules

```

    apt-get -y install git    
    mkdir -p ~/src
    cd  ~/src
    git clone https://github.com/4P/horizon.git
    git clone https://github.com/cloudbuilders/openstackx.git
    cd horizon; python django-openstack/setup.py install; cd ..;
    cd openstackx; python setup.py install; cd ..;
    cd

```

Thats all and you will be happy :)

---

