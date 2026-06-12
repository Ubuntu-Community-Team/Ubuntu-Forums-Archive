---
title: "squid(AD) + log system (surftrackr)"
date: 2010-03-24
forum: Server Platforms
---

### Post by mrwolf on 2010-03-24
Hi,

I try to create a proxy with Ubuntu 9.10 64bit server edition.

I install squid and samba as explained here [http://doc.ubuntu-fr.org/tutoriel/comment_mettre_en_place_un_proxy_squid_avec_authentification_active_directory]("http://doc.ubuntu-fr.org/tutoriel/comment_mettre_en_place_un_proxy_squid_avec_authentification_active_directory"). this way my server joined my active directory domain for a transparent proxy authentification.

the proxy run well. My problem is for the log system.

at first I tried to install SARG, but I couldn't generate any repport. Then I tried calamaris, run well but didn't like it. Then I found surftrackr. I relly think this is what I need but... damn hard to install ane make it work...

I fallowed these steps: [http://www.surftrackr.net/blog/view/9/how-install-django-and-surftrackr/]("http://www.surftrackr.net/blog/view/9/how-install-django-and-surftrackr/") except I install every packages with aptitude except surftrackr itself which I installed with dpkg -i

now I'm trying to do the "./manage.py syncdb" as explained in the tutorial to sync the db but I get this:
```

Traceback (most recent call last):
  File "./manage.py", line 11, in <module>
    execute_manager(settings)
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 362, in execute_manager
    utility.execute()
  File "/usr/lib/pymodules/python2.6/django/core/management/__init__.py", line 303, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 195, in run_from_argv
    self.execute(*args, **options.__dict__)
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 221, in execute
    self.validate()
  File "/usr/lib/pymodules/python2.6/django/core/management/base.py", line 249, in validate
    num_errors = get_validation_errors(s, app)
  File "/usr/lib/pymodules/python2.6/django/core/management/validation.py", line 28, in get_validation_errors
    for (app_name, error) in get_app_errors().items():
  File "/usr/lib/pymodules/python2.6/django/db/models/loading.py", line 131, in get_app_errors
    self._populate()
  File "/usr/lib/pymodules/python2.6/django/db/models/loading.py", line 58, in _populate
    self.load_app(app_name, True)
  File "/usr/lib/pymodules/python2.6/django/db/models/loading.py", line 74, in load_app
    models = import_module('.models', app_name)
  File "/usr/lib/pymodules/python2.6/django/utils/importlib.py", line 35, in import_module
    __import__(name)
  File "/data/surftrackr/../surftrackr/log/models.py", line 72, in <module>
    class User(models.Model):
  File "/data/surftrackr/../surftrackr/log/models.py", line 87, in User
    workstation           = models.ManyToManyField(Workstation, null=True, blank=True, filter_interface=True)
  File "/usr/lib/pymodules/python2.6/django/db/models/fields/related.py", line 814, in __init__
    Field.__init__(self, **kwargs)
TypeError: __init__() got an unexpected keyword argument 'filter_interface'

```

so my db is still empty and I can't import the sql file as provided in the next step.

is there any thing I can do to fix the problem or any package for the log of squid with all the feature surftrackr?

Thanks

---

### Post by mrwolf on 2010-03-25
I think I found the problem but don't know how to fix it...

I think the problem come from Django,

with the version 1.1.1 and 1.0.4
I get this error:
```
TypeError: __init__() got an unexpected keyword argument 'filter_interface'
```

After I readed the post on the Django website...
```
Django: use v0.96
Oct 21st 2008
There have been some backwards-incompatible changes to Django, the web framework which Surftrackr uses, so you will need to use version 0.96 until I have had time to fix this. If you use the latest version, it won't work.

```

I tried with the version 0.96.5
and instead, I get this error:
```
Error: Couldn't install apps, because there were errors in one or more models:
surftrackr.httpauth: __init__() got an unexpected keyword argument 'max_length'
surftrackr.log: __init__() got an unexpected keyword argument 'max_length'
surftrackr.wordsearch: __init__() got an unexpected keyword argument 'max_length'
surftrackr.trackr: __init__() got an unexpected keyword argument 'max_length'
surftrackr.preferences: No module named dateutil.parser

```

on the django website, I found the backwards-incompatible changes to Django from 0.96 to 1.0

```
Moved filter_interface from the model definition ¶
An example: 

# OLD:
class MyModel(models.Model):
    field1 = models.ManyToManyField(AnotherModel, filter_interface=models.VERTICAL)
    field2 = models.ManyToManyField(YetAnotherModel, filter_interface=models.HORIZONTAL)

# NEW:
class MyModelAdmin(admin.ModelAdmin):
    filter_vertical = ('field1',)
    filter_horizontal = ('field2',)
```

so I think the lastest version of surftrackr "18th march 2008" didn't support the new way django support the "filter_interface". but the problem with the max_length, as I readed, can only be fixed by using version newer than 1.0...

and I can't install Django version 0.95.4

anyone have any idea to fix this problem?

---

### Post by mrwolf on 2010-03-25
I reinstalled django 0.96.5 and I replaced all max_length by maxlength in surftrackr files with "replace" command line

now I get only this error:

```
Error: Couldn't install apps, because there were errors in one or more models:
surftrackr.preferences: No module named dateutil.parser
```

---

### Post by mrwolf on 2010-03-25
I really must read instruction more carefully...

on the surftrackr web site...
```
Update, 18 March 2008: You will also need to install python-dateutil, available via "easy_install python-dateutil". 
```

I did: ```
aptitude install python-dateutil
```

and then ```
./manage.py syncdb
```

and it worked.

but now when I goes on the surftrackr website, I get...
```

MOD_PYTHON ERROR
...
...
File "/usr/local/lib/python2.6/dist-packages/django/conf/__init__.py", line 83, in __init__
    raise EnvironmentError, "Could not import settings '%s' (Is it on sys.path? Does it have syntax errors?): %s" % (self.SETTINGS_MODULE, e)

EnvironmentError: Could not import settings 'examples.settings' (Is it on sys.path? Does it have syntax errors?): No module named examples.settings

```

I didn't find "examples.settings" in any files and I don't have any file named "examples.settings"
The only thing I founded who is near what I seek for is:
```
/usr/share/doc/python-pygooglechart/examples/settings.py
```

still working on it...

---

