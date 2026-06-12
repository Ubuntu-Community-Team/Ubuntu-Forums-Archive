---
title: "Apache2 Web Server Problem: VirtualHost gives Blank Page"
date: 2009-07-19
forum: Server Platforms
---

### Post by zzzBrett on 2009-07-19
I am attempting to set up a web server with ubuntu 9.04 using apache2.

I set up virtualhost as follows:

```
<VirtualHost *:80>
	ServerName domain.com
	ServerAlias www.domain.com
	DocumentRoot "/var/www/domain/"
</VirtualHost>
```

Whenever I try to browse [http://domain.com](http://domain.com), all I get is a blank (white) page.  Where can I start troubleshooting this?

Thanks

---

### Post by zzzBrett on 2009-07-20
Any suggestions?

---

### Post by wojox on 2009-07-20
What do you have in the /domain directory as far as a page (index.php, index.html).

---

### Post by zzzBrett on 2009-07-20
> **wojox said:**
> What do you have in the /domain directory as far as a page (index.php, index.html).

index.php, and it is configured as the default page.

---

### Post by wojox on 2009-07-20
What is the code inside index.php?

---

### Post by hartunnoo on 2010-05-17
I think it is permission issues.. you have to chmod -R 777 /home/user/public_html/

---

