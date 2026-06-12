---
title: "Xampp, can't open my php files"
date: 2008-07-08
forum: Server Platforms
---

### Post by masoud23 on 2008-07-08
Hi

I have ubuntu 7.2 and xampp-linux 1.6.6. Xampp starts ok at localhost but when i try to open my php file in htdocs i get this messege:

Forbidden

You don't have permission to access /index.php on this server.
Apache/2.2.8 (Unix) DAV/2 mod_ssl/2.2.8 OpenSSL/0.9.8e PHP/5.2.5 mod_apreq2-20051231/2.6.0 mod_perl/2.0.2 Perl/v5.10.0 Server at localhost Port 80

what am I doing wrong?

tanks in advance

---

### Post by windependence on 2008-07-08
Change directories to your htdocs directory and then do:

```
ls -la
```

and then post the output here.

-Tim

---

### Post by masoud23 on 2008-07-08
get the same result when try again:

Forbidden

You don't have permission to access /examen.html on this server.
Apache/2.2.8 (Unix) DAV/2 mod_ssl/2.2.8 OpenSSL/0.9.8e PHP/5.2.5 mod_apreq2-20051231/2.6.0 mod_perl/2.0.2 Perl/v5.10.0 Server at localhost Port 80

At termianl get the fallowing:

masoud@masoud-desktop:/opt/lampp/htdocs$ ls -la
total 64
drwxr-xr-x  5 nobody root  4096 2008-07-06 23:29 .
drwxr-xr-x 20 root   root  4096 2008-02-11 09:24 ..
-rwx------  1 masoud root  5020 2006-07-24 01:00 examen.html
-rw-r--r--  1 root   root 30894 2007-05-11 14:40 favicon.ico
-rw-r--r--  1 nobody root   163 2003-10-31 22:15 index.html
drwxr-xr-x  4 root   root  4096 2008-07-06 21:58 web
drwxr-xr-x  2 nobody root  4096 2008-07-03 22:31 webalizer
drwxr-xr-x  6 root   root  4096 2008-07-06 23:29 xampp

---

### Post by Stephen_at on 2008-07-08
your webserver process needs to have read access onto your files

---

### Post by windependence on 2008-07-08
Your permissions are not right on your /opt/lampp/htdocs directory. Try this:

```
sudo chmod -R 775 /opt/lampp/htdocs
```

Restart Xampp and let me know.

-Tim

---

### Post by masoud23 on 2008-07-08
Tanks, now it works. Have to sage this is by far best forum I have been in. I am new with Linux but I always get fast and good answers. Just grate! 

Tanks again!

---

### Post by brouwser on 2008-07-29
> **windependence said:**
> Your permissions are not right on your /opt/lampp/htdocs directory. Try this:

```
sudo chmod -R 775 /opt/lampp/htdocs
```

Restart Xampp and let me know.

-Tim

Thanks, Windependence,
You wrote your advise here over a year ago. I used it and it got things working for me after trying to figure things out for ages. You were a great help. Thanks a lot.

---

### Post by aremint on 2010-03-09
hi, i have a problem to edit php file in htdocs because i'm not authorize do edit. i just can edit want access from terminal. anybody can give a solution to make my work more easy

---

### Post by fuadr on 2011-03-10
run the editor as root. 
sudo gedit 

and then open your files and you should be able to save them.

if you use a program like bluefish... you can run it the same way as well, > sudo bluefish

---

