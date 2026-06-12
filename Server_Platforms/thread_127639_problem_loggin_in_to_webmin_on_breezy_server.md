---
title: "problem loggin in to webmin on breezy server"
date: 2006-02-09
forum: Server Platforms
---

### Post by baza41 on 2006-02-09
I've installed webmin on my server which is running 5.10.

The problem I have now is logging in. I've set an admin password using the changepass.pl program, but when I enter that on the login screen it's not recognised. What am I doing wrong?

---

### Post by Derek Djons on 2006-02-09
Sorry, I'm not familiar with webmin but isn't it possible to start it up using the terminal? That way you could check for error-output.

---

### Post by lreyes6 on 2006-02-09
you do this... 
```
/usr/local/webmin-1.260/changepass.pl /etc/webmin admin foo
```

where:
/usr/local/webmin-1.260 --> is the path where u untar the tar.gz
/etc/webmin --> is your installation path
admin is --> your user (could be root or whatever u put on the installation)
and foo --> is the new password u want 

and i suggest u to read the webmin [documentation]("http://www.webmin.com/index2.html")

---

### Post by baza41 on 2006-02-09
I didn't use a tarball, I just got it from synaptic. I'm not sure if it stores it in /usr/local/ ?

---

### Post by makisupa123 on 2006-02-10
Here is the command you need...if your changing user 'root':

 sudo /usr/share/webmin/changepass.pl /etc/webmin root foo


mak.

---

### Post by baza41 on 2006-02-10
[QUOTE=makisupa123]Here is the command you need...if your changing user 'root':

 sudo /usr/share/webmin/changepass.pl /etc/webmin root foo


mak.[/QUOTE]

yeah I've done that but it still wont take my username/password combination? Any ideas?

---

### Post by baza41 on 2006-02-13
Really could use some help with this one folks.

---

### Post by baza41 on 2006-02-14
Ah, fixed it. It was a permissions problem with a couple of the config files in the webmin directory.

---

