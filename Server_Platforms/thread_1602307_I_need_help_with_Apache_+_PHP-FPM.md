---
title: "I need help with Apache + PHP-FPM"
date: 2010-10-21
forum: Server Platforms
---

### Post by davidsilverthorn on 2010-10-21
Hello all,
I'm utterly lost on how to setup Apache with php5-fpm (I'm getting the deb from Brian Mercer's ppa). Can someone help me out on how to set it up?

I am far more familiar with the Cherokee Web Server, but due to incompatibilities with software, I'm switching to Apache. I'm using Apache Worker as well, thus I need php-fpm to get things going 100%. I just can't find any decent guides out there for php-fpm and apache (plenty for other web servers though).

---

### Post by chupnik on 2011-04-23
> **davidsilverthorn said:**
> Hello all,
I'm utterly lost on how to setup Apache with php5-fpm (I'm getting the deb from Brian Mercer's ppa). Can someone help me out on how to set it up?

I am far more familiar with the Cherokee Web Server, but due to incompatibilities with software, I'm switching to Apache. I'm using Apache Worker as well, thus I need php-fpm to get things going 100%. I just can't find any decent guides out there for php-fpm and apache (plenty for other web servers though).

I also want exactly apache2 + php-fpm, although usually php-fpm installed with nginx. This requires the mod_fastcgi and actually own php-fpm - it comes with Ubuntu, starting with version 10.10. Or you can use the great PPA [https://launchpad.net/~bjori/+archive/php5]("https://launchpad.net%20/%7Ebjori/+archive/php5") for early version of Ubuntu. Here I found a good article for the initial launch of the Apache + php-fpm. [http://alexcabal.com/installing-apache-mod_fastcgi-php-fpm-on-ubuntu-server-maverick/]("http://ubuntuforums.org/I%20also%20want%20that%20apache2%20+%20php-fpm,%20although%20usually%20php-fpm%20installed%20with%20nginx.%20This%20requires%20the%20mod_fastcgi%20and%20actually%20own%20php-fpm%20-%20it%20comes%20with%20Ubuntu,%20starting%20with%20version%2010.10.%20Or%20you%20can%20use%20the%20great%20PPA%20https:%20/%20/%20launchpad.net%20/%20%7E%20bjori%20/%20+%20archive/php5%20for%20early%20equilibria%20Ubuntu.%20Here%20I%20found%20a%20good%20article%20for%20the%20initial%20launch%20of%20the%20Apache%20+%20php-fpm.%20http://alexcabal.com/installing-apache-mod_fastcgi-php-fpm-on-ubuntu-server-maverick/")

---

