---
title: "Apache Issue on Ubuntu 14.04 LTS"
date: 2016-01-11
forum: Server Platforms
---

### Post by Helloman2504 on 2016-01-11
Initially the problem was PHP files on my server were displayed as plain text(the whole code was shown). So I found out by investigating that the MIME type has to be added to the `/etc/mime.types` , so I did that and also restarted my server but that didn't help solve the issue so on further investigation, I found out from [http://serverfault.com/questions/393339/apache-shows-html-php-files-as-txt](http://serverfault.com/questions/393339/apache-shows-html-php-files-as-txt) that we needed php5 module enabled and on running the `apachectl -M`, I couldn't find the php5 module listed. So I tried installing it and this was the outcome of it :


    admin@vm:~$ sudo apt-get install php5
    ...
    php5_invoke pdo: already enabled for apache2 SAPI
    dpkg: error processing package libapache2-mod-php5 (--configure):
     subprocess installed post-installation script returned error exit status 1
    Errors were encountered while processing:
     libapache2-mod-php5
    E: Sub-process /usr/bin/dpkg returned an error code (1)
    
    admin@vm:~$ sudo apt-get install libapache2-mod-php5
    ...
    dpkg: error processing package libapache2-mod-php5 (--configure):
     subprocess installed post-installation script returned error exit status 1
    Errors were encountered while processing:
     libapache2-mod-php5
    E: Sub-process /usr/bin/dpkg returned an error code (1)


I also need to mention that I created 2 virtual hosts for the sites. I am not sure what is wrong. Could some one help me on this?

---

### Post by Bucky Ball on 2016-01-11
*Thread moved to **Server Platforms**.*

Not related to ***Desktop Environments***.

---

### Post by SeijiSensei on 2016-01-11
The package libapache2-mod-php5 includes the code that tells Apache to invoke the PHP interpreter for files ending in .php.  I don't know why it won't install cleanly, but that is the problem.  You shouldn't have to alter the mime.types file either, so there is something fundamentally wrong.

If this a new server, I'd start over by reinstalling Ubuntu, then running "sudo apt-get install lamp-server^" to install Apache, PHP, and MySQL.  The carat on the end of the package name is required.

---

