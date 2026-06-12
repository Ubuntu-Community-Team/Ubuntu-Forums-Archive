---
title: "mod_python and firefox"
date: 2007-01-02
forum: Server Platforms
---

### Post by digby on 2007-01-02
Semi-useless background: I've been working on writing a little web app to keep track of billing for patients I see.  I'm writing it in python, and at this point, it works just like it should from the terminal.  So now, I'm trying to setup apache2 and mod_python.

I have everything installed and working.  When I load localhost/mptest.py, (a little hello, world test) it executes as it should; I just can't get firefox to render it as html.  A friend (outside my LAN) tested it in IE, and it rendered just like it should.

Here is the script I'm using:```
import os
from mod_python import apache
from mod_python import psp

def handler(req):
    req.log_error('handler')
    req.content_type = 'text/plain'
    req.send_http_header()
    req.write("""<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Test script ftw</title>
</head>
<body>Hello, world! This is a <strong>test</strong> to see <br />how well <em>this</em> works.</body></html>""")
    return apache.OK
```When run, firefox just prints out the contents of req.write() as if it were plain text.

I have added handlers to apache2.conf and obviously have .htaccess in the folder working properly since it does run the script.  I just can't get FF to render it... any ideas?

---

### Post by digby on 2007-01-02
-solved-
I needed req.content_type = 'text/html' instead of 'text/plain'

---

