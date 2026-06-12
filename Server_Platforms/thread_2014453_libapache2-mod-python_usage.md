---
title: "libapache2-mod-python usage"
date: 2012-07-02
forum: Server Platforms
---

### Post by gameguy on 2012-07-02
I just installed mod-python for apache2 and I love the way it works and seperates your code, however I can't work out how to do POSTs, GETs, session variable (both retrieve and set), and redirects. Does anyone know how to do that?

---

### Post by gameguy on 2012-07-02
I tried this, but it doesn't appear to do the GET properly (cgi side). The get is working, cause the URL is [http://127.0.0.1/login.py?user=username&pwd=password](http://127.0.0.1/login.py?user=username&pwd=password)

```

#!/usr/bin/python

import cgi
def index(req):
    form = cgi.FieldStorage()
    usr = form.getfirst('user')
    pwd = form.getfirst('pwd')
    return """
<html>
    <title>blah</title>
    <head>
        %s<br/>
        %s<br/>
    </head>
    <body>
        <form method="GET">
            Username: <input type="text" name="user"> <br/>
            Password: <input type="password" name="pwd"> <br/>
            <input type="submit" value="Login">
        </form>
    </body>
</html>
""" % (usr, pwd)

```

---

