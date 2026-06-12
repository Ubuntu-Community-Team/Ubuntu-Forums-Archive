---
title: "web server with apache"
date: 2011-12-08
forum: Server Platforms
---

### Post by lioreh on 2011-12-08
Hello everyone,

I`m new in this forum and in linux either..
I wrote few html pages and I want make my computer as web server
that everyone who in my network/have my ip can get this page..
I heard I can to that with Apache
Someone can please explain me what this software and how I use it?
A simple guide we be fine also :),

Thanks in advance, Lior.

---

### Post by lisati on 2011-12-08
*Thread moved to **Server Platforms**.*

Although a full "LAMP" server might be overkill for just displaying web pages, some information can be found here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The main part you should focus on would be the parts relating to Apache.

---

### Post by Lars Noodén on 2011-12-09
> **lioreh said:**
> 
Someone can please explain me what this software and how I use it?


First install a web server.  That can be Apache, Lighttpd, or nginx.  It's your choice which one.  

Then put your web pages in the directory [font=Courier New]/var/www[/font] and you're all set.  If you want to make standardized headers, footers or menus then all you need is to use Server Side Includes.

---

