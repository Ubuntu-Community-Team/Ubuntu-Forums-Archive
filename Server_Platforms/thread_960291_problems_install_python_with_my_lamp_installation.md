---
title: "problems install python with my lamp installation"
date: 2008-10-27
forum: Server Platforms
---

### Post by newbuntuxx on 2008-10-27
hey...

i installed lamp (apache2, mysql, php), then i followed this tutorial to get the python_mod installed so i can run python scripts like i would php scripts: 
[http://robrohan.com/2006/10/01/howto-setup-python-for-web-development-on-ubuntu/](http://robrohan.com/2006/10/01/howto-setup-python-for-web-development-on-ubuntu/)

however, when i created an index.py file in my web directory, the .py file is not run when i visit the home page. it is just listed there as a file that you can download. but i am certain that i installed the python_mod because when i visit the home page, at the bottom, i get the following info:

```

Apache/2.2.8 (Ubuntu) mod_python/3.3.1 Python/2.5.2 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at localhost Port 80
```

Any suggestions or hints?

thanks

---

### Post by alienprdkt on 2008-10-27
I had this problem too, I had solved it by adding this to the httpd.conf file:

<ifModule mod_python.c>
   AddHandler mod_python .py
   PythonHandler mod_python.publisher
   PythonDebug On
</ifModule>


hope this works for you.

---

### Post by newbuntuxx on 2008-10-27
alas, it didn't work..any other suggestions?

---

### Post by alienprdkt on 2008-10-27
[http://howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch](http://howtoforge.com/embedding-python-in-apache2-with-mod_python-debian-etch)

---

### Post by newbuntuxx on 2008-10-28
lol alienprdkt..i actually came  back after i found that link and fixed the problem (dont know what it was, i just re-did everything again). thanks for posting it though...it is very useful.

One question though, which wasn't covered in the link, how can i get .py and .psp extensions run by apache both at the same time? i tried adding the psp handler code and the publisher code to the apache2.conf file, but that failed! is it even possible to do?

thanks

---

### Post by alienprdkt on 2008-10-28
> **newbuntuxx said:**
> lol alienprdkt..i actually came to back after i found that link and fixed the problem (dont know what it was, i just re-did everything again). thanks for posting it though...it is very useful.

One question though, which wasn't covered in the link, how can i get .py and .psp extensions run by apache both at the same time? i tried adding the psp handler code and the publisher code to the apache2.conf file, but that failed! is it even possible to do?

thanks

lol i have tried and ended up with some really weird stuff, think its one or the other.

---

