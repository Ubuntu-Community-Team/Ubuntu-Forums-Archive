---
title: "Python in Apache"
date: 2012-01-12
forum: Ubuntu Dev Link Forum
---

### Post by Orcris on 2012-01-12
I installed mod_python in Apache and enabled it, but when I created a test python page. Here's what it looks like:
```
#!/usr/bin/python3.2
import cgi

print("content-type: application/xhtml+xml")


print("""<?xml version="1.0" encoding="UTF-8"?>\n
<html xmlns="http://www.w3.org/1999/xhtml>\n
\t<head>\n
\t\t<title>A Python Page</title>\n
\t\t<meta http-equiv="content-type" content="application/xhtml+xml;encoding="UTF-8"/>\n
\t</head>\n
\t<body>\n
\t\t<p>Test</p>\n
\t</body>\n
</html>""")
```

When I try to open this page in Firefox, it downloads instead of displaying it, though. I edited my .htaccess file to recognize .py files as cgi. How do I get this to display?

---

### Post by vandorjw on 2012-01-13
What version of apache are you using and is there a reason why you are sticking with mod_python.

I have not used mod python but I can guide you thought mod_wsgi if you like.
Information about mod_wsgi can be found here: [http://code.google.com/p/modwsgi/](http://code.google.com/p/modwsgi/)

I have used it to successfully host a couple of python applications.

---

