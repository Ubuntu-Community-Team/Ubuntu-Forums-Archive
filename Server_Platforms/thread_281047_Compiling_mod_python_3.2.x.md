---
title: "Compiling mod_python 3.2.x"
date: 2006-10-20
forum: Server Platforms
---

### Post by jlhughes on 2006-10-20
I'm trying to compile and install version 3.2 of mod_python. (Required by [www.djangoproject.com](www.djangoproject.com)) Ubuntu offers mod_python 2.4

The command ./configure --with-apxs=/usr/local/apache/bin/apxs doesn't work because that's not where the apxs files are.

I have Apache2 installed and I have installed apache2-threaded-dev, which I understand installs the apxs files, but I can't seem to determine the path I should use instead of /usr/local/apache/bin/apxs

Please excuse this rather newbie question. I'm not a programmer or sysadmin by trade.

======================

Apparently I don't need to compile new mod_python.  I received this info from a source in the django message group:

Assuming you're on a dapper Ubuntu box, I believe the "2.4" in the mod_python package name is referring to the Python level, not the mod_python package level.  The "latest version" for this package is 3.1.4-0ubuntu1, which I'd guess means the 3.1.4 level of mod_python built/packaged for Ubuntu.  That should meet the Django requirement of a 3.x mod_python.

So I don't think you need to build mod_python to run on Ubuntu.  At any rate I didn't, I just installed the latest available from the default repositories, and it's been running fine for a month or so (alibeit on a very low-traffic site).

---

