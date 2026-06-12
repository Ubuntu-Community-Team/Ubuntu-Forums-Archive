---
title: "Need help getting phppgadmin working"
date: 2006-03-23
forum: The Cafe
---

### Post by kennethb on 2006-03-23
I have installed PHP, phppgadmin, and postgresql on Breezy. When I type:

[http://localhost/phppgadmin](http://localhost/phppgadmin)

in my browser, I get the following error message displayed:

Not Found
The requested URL /phppgadmin was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 Server at localhost Port 80

Can anyone offer some help here? How do I get phppgadmin to work? I have already created a postgresql database using a terminal sesion and cmd line.

Any help is very much appreciated.

---

### Post by WildTangent on 2006-03-24
[QUOTE=kennethb]I have installed PHP, phppgadmin, and postgresql on Breezy. When I type:

[http://localhost/phppgadmin](http://localhost/phppgadmin)

in my browser, I get the following error message displayed:

Not Found
The requested URL /phppgadmin was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 Server at localhost Port 80

Can anyone offer some help here? How do I get phppgadmin to work? I have already created a postgresql database using a terminal sesion and cmd line.

Any help is very much appreciated.[/QUOTE]
Is it properly installed? Look in /var/www see if theres a folder or symlink for phppgadmin.

-Wild

---

### Post by kennethb on 2006-03-24
Hi Wild,

No I don't see a folder or symlink of phppgadmin there:

ken@ubuntu:~$ cd /var/www
ken@ubuntu:/var/www$ ls
apache2-default
ken@ubuntu:/var/www$ cd apache2-default
ken@ubuntu:/var/www/apache2-default$ ls
apache_pb2_ani.gif       index.html.et             index.html.pt-br
apache_pb2.gif           index.html.fr             index.html.ru.cp-1251
apache_pb2.png           index.html.he.iso8859-8   index.html.ru.cp866
apache_pb.gif            index.html.hr.iso8859-2   index.html.ru.iso-ru
apache_pb.png            index.html.it             index.html.ru.koi8-r
index.html.ca            index.html.ja.iso2022-jp  index.html.ru.utf8
index.html.cz.iso8859-2  index.html.ko.euc-kr      index.html.sv
index.html.de            index.html.lb.utf8        index.html.var
index.html.dk            index.html.nl             index.html.zh-cn.gb2312
index.html.ee            index.html.nn             index.html.zh-tw.big5
index.html.el            index.html.no             robots.txt
index.html.en            index.html.po.iso8859-2
index.html.es            index.html.pt
ken@ubuntu:/var/www/apache2-default$

What is a sylink?

---

### Post by zigoto on 2006-03-24
Hi
i had the same problem, i have resolve this by typing:
sudo ln -s /usr/share/phppgadmin /var/www/phppgadmin

now try to acess the link.
[http://localhost/phppgadmin](http://localhost/phppgadmin)


sorry my english:-k

---

### Post by kennethb on 2006-03-24
zigoto, thank you for you suggestion. It work just fine.

I also had to edit the /etc/postgresql/8.0/main/pg_hba.conf by adding the follwoing lines:

> local all postgres ident sameuser
> local all all password

And commenting the line:

# local all all ident sameuser

---

### Post by franck on 2006-08-27
there is another way to get phppgadmin working. in /etc/phppgadmin/ , you have an apache.conf .... so you copy the content of the file at the end of the httpd.conf on apache1.3 server or apache2.conf in a apache2 server,then your restart the server . ;)

---

