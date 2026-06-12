---
title: "500 Internal Server Error"
date: 2009-05-04
forum: Server Platforms
---

### Post by pi.theta on 2009-05-04
(using ubuntu jaunty
i just installed apache2 and have this file at the default location
/usr/lib/cgi-bin/hello.py

with following code:

```
#!/usr/bin/python
print ´Conten-Type:text/plain\n´
print ´My name is theta´
```

when i addresss it using firefox (localhost/cgi-bin/hello.py)

firefox a

500 Internal Server Error

can anyone help me where the trouble could be
thanks for any help in advance

---

### Post by cdenley on 2009-05-04
Does it give you a 500 error if you spell "Content" correctly?
```

#!/usr/bin/python
print ´**Content-Type**:text/plain\n´
print ´My name is theta´

```

---

### Post by pi.theta on 2009-05-04
yes, it still does 

it shows the same error while using plain html

```
<hmtl>
<title> local server </title>

some text here

</html>
```

can u also tell about the address, because when i press enter after typing 

localhost/cgi-bin/hello.html

a http://

gets added at the beginning

---

### Post by cdenley on 2009-05-05
You're not using a valid quotes character.
```

#!/usr/bin/python
print **[COLOR="Red"]'[/COLOR]**Content-Type:text/plain\n[COLOR="Red"]**'**[/COLOR]
print **[COLOR="Red"]'[/COLOR]**My name is theta[COLOR="Red"]**'**[/COLOR]

```

---

### Post by msatep on 2009-05-23
i've got the same probem(((
herewith there is mod_python works normally on my Ubuntu. But python CGI-scripts do not work. What can I do?

---

### Post by albinootje on 2009-05-23
Check the apache logfiles for possible more information.

---

### Post by ActiveFrost on 2009-05-23
Terminal : 
```
sudo chmod 755 /usr/lib/cgi-bin/hello.py
```

Apache configuration file :
```
<Directory /usr/lib/cgi-bin/>
    AllowOverride None
    Options ExecCGI
    Order allow,deny
    Allow from all
</Directory>
```

Hope it helps :)

---

### Post by msatep on 2009-05-23
There is a record after a try of running of CGI-script in the Apache log-file:

[Sat May 23 20:34:30 2009] [error] (13)Permission denied: exec of '/usr/lib/cgi-bin/test.py' failed
[Sat May 23 20:34:30 2009] [error] [client 127.0.0.1] Premature end of script headers: test.py

what is it means?

To ActiveFrost: Thank You! It works!!!

---

