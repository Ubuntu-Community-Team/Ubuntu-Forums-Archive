---
title: "phpMyAdmin without libapache2-mod-php5 (using Nginx and php5-fpm)"
date: 2011-02-04
forum: Server Platforms
---

### Post by ichilton on 2011-02-04
Hi,

I'm using Nginx and php5-fpm but when I apt-get install phpMyAdmin, it wants to install apache etc because it depends on libapache2-mod-php5.

Is there any way to get around this?

It looks like i'm going to have to go and download the phpMyAdmin source and use that, but i'd rather use the Ubuntu package so it will get updates.

Thanks,

Ian

---

### Post by Thirtysixway on 2011-02-04
> **ichilton said:**
> Hi,

I'm using Nginx and php5-fpm but when I apt-get install phpMyAdmin, it wants to install apache etc because it depends on libapache2-mod-php5.

Is there any way to get around this?

It looks like i'm going to have to go and download the phpMyAdmin source and use that, but i'd rather use the Ubuntu package so it will get updates.

Thanks,

Ian

You could try looking around for a PPA of phpmyadmin that doesn't depend on apache. Or like you said, download the source and use that.

---

### Post by chupnik on 2011-04-23
> **Thirtysixway said:**
> You could try looking around for a PPA of phpmyadmin that doesn't depend on apache. Or like you said, download the source and use that.
You don't need any other PPA for installing **phpmyadmin**!!! If you look closely you'll see, that **phpmyadmin** requires (**libapache2-mod-php5** OR **php5-cgi**). So you can install only **php5-cgi** before installing **phpmyadmin**.

---

