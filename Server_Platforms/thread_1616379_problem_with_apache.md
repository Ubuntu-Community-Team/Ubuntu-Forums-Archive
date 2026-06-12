---
title: "problem with apache"
date: 2010-11-08
forum: Server Platforms
---

### Post by oren tal on 2010-11-08
Hello

I have installed ubuntu server on a computer. I have created a new index.php file and it work for me. Later i have edited the index.html file but when I access to the ip of the server from the web browser, it still show me the older index.html file (the file that the apache create by default).

I don't understand why the apache show an older file and more than that since I have changed the index.html, from where does it take it.

I will thank for any explanation.

---

### Post by wojox on 2010-11-08
Because it serves up .html files before .php files.

---

### Post by oren tal on 2010-11-08
> **wojox said:**
> Because it serves up .html files before .php files.
thanks,  but I don't understand what you are saying.

by the way when I write 192.168.1.2/index.php in the browser it work.
It show me the older file (of the html) when I write 192.168.1.2/index.html 

so what is it  about the server up?

---

### Post by FlintyV on 2010-11-08
.html files take priority over .php files. If you have a folder with hello.html and hello.php, Apache will go for the .html file if you don't explicitly request the URL of it like 192.168.1.2/hello.php.

If you go to just [http://192.168.1.2](http://192.168.1.2) it will serve up hello.html.

I think.

---

### Post by wojox on 2010-11-08
Look in 

```
/etc/apache2/mods-enabled/dir.conf
```

See how html comes before php. Why do you have two index pages anyway?

---

### Post by babur on 2010-11-08
By default apache webserver servers ".html" files, that is the way it is configured.  If you want to modify the config to serve the ".php" file by default modify the 

/etc/apache2/mods-enabled/dir.conf

to rearrange the extensions.

Or

Temporary solution is, remove the "index.html" file from the stored location.

So when you type your ip in the browser the apache will serve "index.php" file.

---

### Post by oren tal on 2010-11-08
> **wojox said:**
> Look in 

```
/etc/apache2/mods-enabled/dir.conf
```

See how html comes before php. Why do you have two index pages anyway?

I have two index pages because I am using this server to learn about php and Java script and apache so I do my experiments.

And dir.conf show following order:
```
DirectoryIndex inedx.html index.cgi index.pl index.php index.xhtml index.htm
```
Thanks again.

But when I ask for the html file (via the browser in anther computer through the internal LAN) and it show me the original file:
> 
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
and that is after I have changed the index.html file to something else.
Now I have totally erased from the folder /var/www.
but it still show me the same message.
On the other hand when I ask directly for the index.php file it does show me the product of that file, which mean the php work for me.

I just don't understand how can it continue to give me the same message even after (not only changed this file) but actually remove it.

---

### Post by wojox on 2010-11-08
> Now I have totally erased from the folder /var/www.
but it still show me the same message.

Try deleting recent history from your browser.

---

### Post by oren tal on 2010-11-08
> **FlintyV said:**
> .html files take priority over .php files. If you have a folder with hello.html and hello.php, Apache will go for the .html file if you don't explicitly request the URL of it like 192.168.1.2/hello.php.

If you go to just [http://192.168.1.2](http://192.168.1.2) it will serve up hello.html.

I think.
That is not my problem.
When I ask for the php it give the php and I am sking directly.

But when I ask for the index.html it always give the original index.html
now it continue to give the original index.html even though the folder /var/www is empty.


My problem is **NOT** that it it give the index.html instead of the product of the index.php

---

### Post by oren tal on 2010-11-08
> **wojox said:**
> Try deleting recent history from your browser.

**Thanks**, it worked.

why did the browser use cache when I reload the website**?**:confused:
It doesn't make sense to me.

---

### Post by wojox on 2010-11-08
I think it's just away to speed Firefox up. You could set it to never remember history.

---

