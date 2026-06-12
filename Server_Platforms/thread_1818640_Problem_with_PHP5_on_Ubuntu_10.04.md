---
title: "Problem with PHP5 on Ubuntu 10.04"
date: 2011-08-05
forum: Server Platforms
---

### Post by miroiuso on 2011-08-05
Hello,

I have a machine running on Ubuntu 10.04. When choosing (in the installation steps) what software to install, I just choosed openSSH server.
I then continued with installing apache2 and mysql.
Now I need to install php5 on the server.
I ran apt-get install php5 and everything finished ok.
But now I'm trying to open a test file, test.php, (just the usual php_info(); in it) by issuing http://<server_ip_address>/test.php I get a browser error like it doesn't find the file.
The test.php file is in /var/www/.

What am I doing wrong here ?

Thank you in advance.

Sorin M.

---

### Post by dinu90 on 2011-08-05
What error do you get in /var/log/apache2/error.log ?

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by ruffEdgz on 2011-08-05
Sounds like a permission issue if your browser is showing an error about not finding that file.

Make sure the test.php file has the correct permissions to be seen and is owned by 'www-data'.

```

sudo chown www-data.www-data /var/www/test.php && chmod 664 /var/www/test.php

```

You might also want to see the config file for your apache service found in /etc/apache2/sites-enabled/ and make sure the variable 'DocumentRoot' is pointing to the correct directory:

```

DocumentRoot /var/www

```

Cheers!

---

### Post by SeijiSensei on 2011-08-06
See if "sudo apt-get install libapache2-mod-php5" fixes the problem for you.  You'll need to restart Apache after installation and before testing with "sudo restart apache2".  People with your problem are usually missing the "AddHandler" directive that's contained in /etc/apache2/mods-enabled/php5.conf which is part of the libapache2-mod-php5 package.

---

### Post by miroiuso on 2011-08-24
Hello.

Sorry for the delayed response, I was on holiday.

So, the problem is due to the fact that I wrote php_info() instead of phpinfo() :(

The log file specified this.

Thank you to all you guys.

regards,
Sorin

---

