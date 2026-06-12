---
title: "About PHP.."
date: 2012-10-30
forum: Server Platforms
---

### Post by friendlybacteria on 2012-10-30
Hello, I'm totally new on everything.. but trying to build a LAMP server.. (i know.. HHH..)

I've used the command below:

apt-get install LAMP-server

and figured out I've installed the required software 'successfully', but got no idea how to setup/test the php5.. please help, thank you.

---

### Post by sandyd on 2012-10-30
**moved to server platforms**

---

### Post by friendlybacteria on 2012-10-30
excuse me.. i'm using apache2.. where do i move to the server-platform? thank you.

---

### Post by Doug S on 2012-10-30
My suggestion is that you refer to the [related section of the server guide]("https://help.ubuntu.com/12.10/serverguide/php5.html#php5-configuration"), which also contains links to other references with more detail.
You did not mention your Ubuntu version number, so you might prefer to start from [here]("https://help.ubuntu.com/"). The link above was for version 12.10.

---

### Post by CharlesA on 2012-10-30
PHP should already be set up.

You can create a file in /var/www named phpinfo.php with this inside:
```
<?php phpinfo(); ?>
```

Try to access it from a browser and you will know if PHP is working or not.

[http://php.net/manual/en/function.phpinfo.php](http://php.net/manual/en/function.phpinfo.php)

---

### Post by friendlybacteria on 2012-10-30
> **sandyd said:**
> **moved to server platforms**

well.. my Ubuntu version is 12.04 LTS.. I've also tried the phpinfo.php built:

<?php phpinfo(); ?>

my browser is chromium, and after I used it to open the file, nothing happened instead.. only a rectangle with the phpinfo.php named shown left-below the screen..

---

### Post by CharlesA on 2012-10-30
Make sure php is enabled.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_PHP_5)

---

### Post by friendlybacteria on 2012-10-30
i've typed the command in the terminal:
a2enmod php5
the result it replied: module php5 already enabled..

and I've just noticed that my browser keeps 'downloading' the php file.. I then follow the instruction to reinstall the package, but it didn't work..

---

### Post by Doug S on 2012-10-31
Did you put the phpinfo.php file at /var/www/phpinfo.php , as Charles mentioned?
If instead you put it in your own user public_html directory, php does not work there by default. For php to work in the user directories /etc/apache2/mods-available/php5.conf needs to be edited (it tells you what to do in the file.)
 
Is the apache web server delivering html content O.K.?

---

### Post by Lars Noodén on 2012-10-31
> **friendlybacteria said:**
> well.. my Ubuntu version is 12.04 LTS.. I've also tried the phpinfo.php built:

<?php phpinfo(); ?>

my browser is chromium, and after I used it to open the file, nothing happened instead.. only a rectangle with the phpinfo.php named shown left-below the screen..

You have to read it via the web server.  It is the web server that does the PHP processing, not the browser.  So if you open the file directly in the browser nothing will happen.  

The default location of the files for the web server's first virtual host is /var/www, if you haven't moved them.  Put the file there.

---

### Post by SeijiSensei on 2012-11-02
Also check that the libapache2-mod-php5 package is installed.  That adds the needed code to the web server to tell it to parse and display .php files rather than sending them directly to the browser.

---

### Post by friendlybacteria on 2012-11-04
Still working on it.. but THANK YOU ALL for helping! :)

---

### Post by friendlybacteria on 2012-11-28
Hello~ I now have my PHP5 module enabled under apache2, but once I try to run a .php file, the browser still keeps downloading it.. any suggestion? THANK YOU. :)

---

### Post by SeijiSensei on 2012-11-28
As I asked before, is libapache2-mod-php5 installed?  

Try "sudo apt-get install libapache2-mod-php5".

---

### Post by friendlybacteria on 2012-11-29
> **SeijiSensei said:**
> As I asked before, is libapache2-mod-php5 installed?  

Try "sudo apt-get install libapache2-mod-php5".

Yes, the libapache2-mod-php5 is installed, I read several documents saying that it needs to be set-up under httpd.conf, (am I correct?) but I can't find this file.. 

Thank you for helping. :)

---

### Post by Mopar1973Man on 2012-11-29
Just to be helpful you might try using Webmin to aid in setting up your server. 
[http://webmin.com/](http://webmin.com/)

---

### Post by friendlybacteria on 2012-11-30
> **sandyd said:**
> **moved to server platforms**

I will try, thank you. :)

---

### Post by friendlybacteria on 2012-11-30
> **Mopar1973Man said:**
> Just to be helpful you might try using Webmin to aid in setting up your server. 
[http://webmin.com/](http://webmin.com/)

thank you. :)

---

