---
title: "How to remove PHP extension, receiving no data"
date: 2012-02-27
forum: Server Platforms
---

### Post by ludatha on 2012-02-27
Hello

I've setup my lamp server with ubuntu-server. I installed XDebug and now I get "Zero Sized Reply" or "Your request returned no data. Please check your url and try again"

How do I remove XDebug from the command line? There's nothing in php.ini

Thanks

---

### Post by ludatha on 2012-02-27
I have found the answer to my question :)

> A lot of PHP extension installs on Linux use their own .ini files for configuration. Take a look in /etc/php.d/ for any files called xdebug.ini. Comment out any lines in the file using a semi-colon and re-start Apache.

That should disable it.

---

