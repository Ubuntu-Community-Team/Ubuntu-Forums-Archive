---
title: "Error after installing Django 1.2.1 (supposed PATH or PYTHONPATH “error”)"
date: 2010-05-29
forum: Server Platforms
---

### Post by mpetrovic on 2010-05-29
Hi all,

I guess this is a PATH/PYTHONPATH error, but my attempts failed so far to make django working.


System is Ubuntu 10.04, 64bit. Python version: 2.6.5:

```
@mx:~/webapps$ python -V
Python 2.6.5
```


When I run django-admin.py, the following happens:

```
mx:~/webapps$ django-admin.py
Traceback (most recent call last):
  File "/usr/local/bin/django-admin.py", line 2, in <module>
    from django.core import management
ImportError: No module named django.core
```


Similar when I import django in python shell:

```
mx:~/webapps$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named django
>>> quit()
```


More details:

```
mx:~/webapps$ python -c "from distutils.sysconfig import get_python_lib; print get_python_lib()"

/usr/lib/python2.6/dist-packages
```


Within python shell:

```
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/lib/python2.6/dist-packages/django', '/usr/local/lib/python2.6/dist-packages/django/bin', '/usr/local/lib/python2.6/dist-packages/django', '/home/petra/webapps', '/usr/lib/python2.6', '/usr/lib/python2.6/plat-linux2', '/usr/lib/python2.6/lib-tk', '/usr/lib/python2.6/lib-old', '/usr/lib/python2.6/lib-dynload', '/usr/lib/python2.6/dist-packages', '/usr/lib/python2.6/dist-packages/PIL', '/usr/lib/pymodules/python2.6']
```


django-admin.py can be found here:

```
mx:~/webapps$ locate django-admin.py
~/install/sources/Django-1.2.1/build/lib.linux-i686-2.6/django/bin/django-admin.py
~/install/sources/Django-1.2.1/build/scripts-2.6/django-admin.py
~/install/sources/Django-1.2.1/django/bin/django-admin.py
/usr/local/bin/django-admin.py
/usr/local/lib/python2.6/dist-packages/django/bin/django-admin.py
/usr/local/lib/python2.6/dist-packages/django/bin/django-admin.pyc
```


And, in the end, this doesn't help:

```
export PYTHONPATH="/usr/lib/python2.6/dist-packages/django:$PYTHONPATH"
```


nor this:

```
export PYTHONPATH="/usr/local/lib/python2.6/dist-packages/django:$PYTHONPATH"
```


How to solve this!? Googling for couple of hours, I know I'm missing something painfully obvious, but my mind is just blocked at the moment... :)
If you need more details, I'd be happy to provide.

Thanks all in advance! :)

---

### Post by mpetrovic on 2010-05-30
Just to give a heads-up for someone facing the same problem:

After spending hours and hours in CLI I have finally found the solution. The reason django-admin.py wasn't able to execute was access permission of the /usr/local/lib directory, actually, lack of owner's execute permission.

So, one: ```
sudo chmod 711 /usr/local/lib
``` solves the django-admin.py execution problem for ever :)

---

