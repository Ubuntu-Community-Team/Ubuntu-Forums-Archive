---
title: "apache2 and mod-python"
date: 2005-09-18
forum: Server Platforms
---

### Post by muszek on 2005-09-18
I have apache2 working nicely.  I just installed apache2-mod-python2.4 and restarted apache2.  When I enter localhost/test.py in my browser, it doesn't parse the script, but wants to open/save it.  What should I do?

---

### Post by pingswept on 2005-10-07
[QUOTE=muszek]I have apache2 working nicely.  I just installed apache2-mod-python2.4 and restarted apache2.  When I enter localhost/test.py in my browser, it doesn't parse the script, but wants to open/save it.  What should I do?[/QUOTE]

I had exactly this problem on Breezy. I fixed it (after reading [this message]("http://www.modpython.org/pipermail/mod_python/2003-August/014036.html") in the mod_python mailing list archives) by commenting out the line:

text/x-python            py

in /etc/mime.types.

I also found [these instructions]("http://www.modpython.org/live/current/doc-html/inst-testing.html") useful.

Pingswept

---

