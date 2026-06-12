---
title: "apache access log"
date: 2008-12-01
forum: Server Platforms
---

### Post by nicola76b on 2008-12-01
Hi all, 
sometimes (it's not predefined times) my apache stops, so I start watching logs to understand the problem. The first log that I investigated is access.log that it shows a strange entry:
```
...
82.57.15.220 - - [20/Nov/2008:10:30:08 +0100] "GET /med/course/category.php?id=18 HTTP/1.1" 200 11303 "http://mitel.dimi.uniud.it/med/course/index.php" "Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4"
127.0.0.1 - - [20/Nov/2008:10:30:09 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
127.0.0.1 - - [20/Nov/2008:10:30:12 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
127.0.0.1 - - [20/Nov/2008:10:30:13 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
127.0.0.1 - - [20/Nov/2008:10:30:14 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
127.0.0.1 - - [20/Nov/2008:10:30:15 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
127.0.0.1 - - [20/Nov/2008:10:30:18 +0100] "GET / HTTP/1.0" 302 - "-" "Apache/2.2.0 (Fedora) (internal dummy connection)"
82.57.15.220 - - [20/Nov/2008:10:30:18 +0100] "GET /med/course/view.php?id=28 HTTP/1.1" 303 234 "http://mitel.dimi.uniud.it/med/course/index.php" "Mozilla/5.0 (Windows; U; Windows NT 5.1; it; rv:1.9.0.4) Gecko/2008102920 Firefox/3.0.4"
...
```
I think that gecko is the Layout engine used by mozilla, but what I don't understand is the entry about Fedora: my server is an ubuntu server..
Please, clarify my situation, and if you have some tips related to unexpected "stops", council me!!
thank you very much, best regards, 
   -nicola

---

