---
title: "Hosting site. Server only returns HTML content"
date: 2012-12-28
forum: Server Platforms
---

### Post by spriggan486 on 2012-12-28
Hi. I'm trying to host my own site for the first time. I have LAMP installed. My problem is, when I access my site from the web, all the server returns is the HTML content and non of the PHP. I'm hoping for some help in resolving this. Thank you very much for any input.

---

### Post by sandyd on 2012-12-28
> **spriggan486 said:**
> Hi. I'm trying to host my own site for the first time. I have LAMP installed. My problem is, when I access my site from the web, all the server returns is the HTML content and non of the PHP. I'm hoping for some help in resolving this. Thank you very much for any input.

How did you install LAMP?

Also, make sure the apache2 php handler is loaded and installed
```

#install apache2 php handler
sudo apt-get install php5
#enable php5
a2enmod php5
```

---

### Post by spriggan486 on 2012-12-28
no luck. PHP5 mod is alresdy enabled

---

### Post by sandyd on 2012-12-28
> **spriggan486 said:**
> no luck. PHP5 mod is alresdy enabled

What are the contents of the php file that you are are trying to run?

---

