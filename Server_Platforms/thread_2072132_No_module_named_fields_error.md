---
title: "No module named fields error"
date: 2012-10-17
forum: Server Platforms
---

### Post by hunterlove22 on 2012-10-17
I got error from django

```
Wed Oct 17 03:59:27 2012] [error] [client XXX] Traceback (most recent call last):
[Wed Oct 17 03:59:27 2012] [error] [client XXX]   File "/usr/local/lib/python2.7/dist-packages/django/core/handlers/wsgi.py", line 219, in __call__
[Wed Oct 17 03:59:27 2012] [error] [client XXX]     self.load_middleware()
[Wed Oct 17 03:59:27 2012] [error] [client XXX]   File "/usr/local/lib/python2.7/dist-packages/django/core/handlers/base.py", line 47, in load_middleware
[Wed Oct 17 03:59:27 2012] [error] [client XXX]     raise exceptions.ImproperlyConfigured('Error importing middleware %s: "%s"' % (mw_module, e))
[Wed Oct 17 03:59:27 2012] [error] [client XXX] ImproperlyConfigured: Error importing middleware klobe.middleware: "No module named fields"
```


I installed django-fields and import but no luck. Please help me.

Thanks,
Kevin

---

### Post by anonymouschief on 2012-10-19
Please refer to [https://www.djangoproject.com/community/](https://www.djangoproject.com/community/)

It would be nice too if you included a bigger chunk of your log, for example:

```

Working good.
Working good.
Working good.
Working good.
Error.
Error.
Error.

```

It helps to see the last thing that worked successfully before the first error in your log. I recommend that you restart Python/Django (which ever service controls them), then send us a log that shows the process from the restart leading to the errors you're getting. What was the last thing you changed before te errors came up? Are you configuring these services for the first time? Which edition and version of Ubuntu are you running?

Thanks,
AC

---

