---
title: "Python, CGI and Apache"
date: 2007-07-27
forum: Server Platforms
---

### Post by Jexel on 2007-07-27
I followed the guide on ubuntuguide.com in setting up a webserver. However, I'm having trouble getting python to work...i can get .py to execute and return stuff however i can't manage to get .cgi to work.

I have a test.cgi file with the permissions

-rwxr-xr-x 1 root root 122 2007-07-28 10:15 test.cgi

and the contents

```
#! /usr/bin/python
print "Content-Type: text/plain\n\n"
print "Hello, Python!"
```

when i try to run the script it just prints the content onto the screen. Can somebody tell me where I'm going wrong?

---

### Post by Jexel on 2007-07-28
bump

---

### Post by bbzbryce on 2007-07-28
> **Jexel said:**
> bump

Is the folder your working with CGI executable? Or have you tried mod-python?

---

### Post by Jexel on 2007-07-28
i am so confused right now...i've spent hours trying to get this working and instead of printing the code to screen it now gives me a 403 Forbidden Error.

I have little clue what I'm doing since i've never done this before and it just seems that i'm going around in circles.

What exactly do I need to setup? How exactly do I use mod_python? I know i have it installed. How do I make it CGI executable? Do I need a .htaccess file?

So many questions. This really is driving me insane.

---

### Post by Jexel on 2007-07-29
after many hours i finally got it working :| chucked in a .htaccess and it worked...

---

### Post by bbzbryce on 2007-07-29
> **Jexel said:**
> after many hours i finally got it working :| chucked in a .htaccess and it worked...

If you configure your apache configuration files properly you shouldn't need a .htaccess file. The .htaccess should only be used when you can't modify the the apache configuration files, or when you want to change something without restarting the apache process. The file you want to edit most likely is:

/etc/apache2/sites-enabled/000-default

but if you have it working then I suppose that's all that really matters.

---

### Post by www.rzr.online.fr on 2007-08-03
It worked for me, these tracks may help :

grep AllowOverride /etc/apache2/mods-enabled/userdir.conf 
AllowOverride All


cat << EOF >>> ~/public_html/.htaccess
Options +ExecCGI
AddHandler cgi-script cgi pl 
EOF

-
[http://rzr.online.fr/q/HTTP](http://rzr.online.fr/q/HTTP)
[http://rzr.online.fr/q/Python](http://rzr.online.fr/q/Python)

---

