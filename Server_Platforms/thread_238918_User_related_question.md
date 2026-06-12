---
title: "User related question"
date: 2006-08-18
forum: Server Platforms
---

### Post by nibbo on 2006-08-18
Hi!

I am running a small server at home with apache and proftpd amongst others installed services. I am running a small file hostings service for friends and family. They get an account and the home directory located in "/var/www/nibbo_files/their name". The files are then hosted under "files.nibbo.se/their name" So far so good, but I am also running a small homepage for myself that i want to place in "/var/www/nibbo". I want the user "nibbo" to be able to change (write, remove, and stuff like that) all files in all folders under "/var/www/" and still have the home directory in "/home/nibbo/"

To say it the simple way: I want nibbo to be the webmaster, being able everyting hosted on the webserver.

Does anybody have a good solution to this?

---

### Post by lvanderree on 2006-08-18
I just typed a complete answer.... But this forum or my internet-connection had a problem, and now my post has failed...

So for now a shorter answer:

you can add a folder under nibbo's home folder called public_html.
```

mkdir /home/nibbo/public_html

```
in this folder you can add your files like index.html

It might be so that you should have read access for every user. Not sure about that

this folder should be immediately visible when you visit [http://server/~nibbo](http://server/~nibbo)

when you want [http://server](http://server) to show this content there are two solutions.
1. change DocumentRoot in  /etc/apache2/sites-available/default
to /home/nibbo/public_html

or 
2. remove the www directory in /var and add a link to /home/nibbo/public_html and call this www, like:
```

ln -s /home/nibbo/public_html/ var/www

```

in both of these cases you can also choose an other name for public_html to anything you like, like main_site.

---

### Post by nibbo on 2006-08-18
Yea i suppose that is a solution, but it wont work for me. Isnt there just a way to get nibbo to be able to browse the whole server (not being jailed like everybody else) via ftp?

---

### Post by harisund on 2006-08-19
I don't think what you are particularly asking for is possible, since that violates the basic idea behind user security in Unix/Linux based systems. 

What you could do is become root (sudo -i) and browse all directories freely.

---

