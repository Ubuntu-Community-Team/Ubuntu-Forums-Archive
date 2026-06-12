---
title: "Password protect whole site with apache"
date: 2008-05-06
forum: Server Platforms
---

### Post by rlpt on 2008-05-06
I've got an apache setup running a django project. I want to password protect the whole site but all documentation i can find just shows how to protect a directory. This doesn't work for me because my conf for apache looks like this:

```
<Location "/">
	SetHandler python-program
	PythonPath "['/var'] + sys.path"
	PythonHandler django.core.handlers.modpython
	SetEnv DJANGO_SETTINGS_MODULE pt.settings
	PythonDebug On
</Location>

<Location "/site_media/">
	SetHandler None
</location>

```

I want to protect the location "/". Any ideas guys?

---

### Post by yogensha on 2008-05-06
You can only put the appropriate configuration inside a <Directory> section.  The "/" in the <Location> tag does point to something on disk, and you'll have to add a <Directory> section for that location on disk.  <Location> sections don't describe disk locations, they describe URL locations.

See:

[http://httpd.apache.org/docs/1.3/sections.html](http://httpd.apache.org/docs/1.3/sections.html)
[http://httpd.apache.org/docs/1.3/mod/core.html#location](http://httpd.apache.org/docs/1.3/mod/core.html#location)

---

