---
title: "apache never start than work"
date: 2006-12-04
forum: Server Platforms
---

### Post by msn4us on 2006-12-04
hi guys ...:( 

when i try to start apache2 its never work whith me

```
 sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server...                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```


i dont know what shoud i do](*,) ](*,)

---

### Post by GSMD on 2006-12-04
Looks like your hostname isn't set try to put smth like

127.0.0.1       localhost.localdomain localhost

to you /etc/hosts file.

---

### Post by msn4us on 2006-12-04
ya...its sloved but i cant browser it in firefox

still look like not running...problem loading page
[PHP]
* Starting apache 2.0 web server...                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 30450) already running
                                                                         [ OK ][/PHP]

so how i configure it or how i remove it include all files

and install it agian

---

### Post by MJN on 2006-12-04
The lack of Servername is not an issue - it's assumed localhost in its absence.
 
Your problem is that there's already a web server running on port 80 (with process ID 30450). You need to find what it is and remove it if not required.
 
Mathew

---

### Post by tturrisi on 2006-12-04
try:
/etc/init.d/apache2 **restart**

---

### Post by mohdridha on 2007-01-23
> **tturrisi said:**
> try:
/etc/init.d/apache2 **restart**

i installed apache from source. and there is no directory/file named:

/etc/init.d/apache2
and
/etc/apache2

I think all the Apache files are stored at /usr/local/apache2/

how can i make apache start automatically everytime i switch on my Ubuntu machine?
where? is it init.d or rc.d directory? or do i need to make some script in order my Apache2 to be auto start.. Thanks

---

