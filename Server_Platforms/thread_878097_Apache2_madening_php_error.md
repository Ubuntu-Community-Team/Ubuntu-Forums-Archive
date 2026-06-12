---
title: "Apache2 madening php error"
date: 2008-08-02
forum: Server Platforms
---

### Post by TennSeven on 2008-08-02
I am pretty new at this, but I am trying to run apache server and I have a php test page in the sites-enabled directory that consists simply of the text:

<?php
phpinfo();
echo "Hello World";
?>

When I try to start apache2 I get the error:

"apache2: Syntax error on line 298 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/sites-enabled/phptest.php: /etc/apache2/sites-enabled/phptest.php:1: <?php> was not closed.

From what I can tell online, my PHP looks fine. Can anyone tell me what I am missing?

---

### Post by redraiderbum on 2008-08-02
That looks like it should work.  You could try single quotes or use print rather than echo, but I think that should work.  Try this:

<?php
phpinfo();
echo 'Hello World';
?>

---

### Post by TennSeven on 2008-08-02
I just tried it with the single quotes as you suggested, and I am getting the same error.

---

### Post by redraiderbum on 2008-08-02
My guess is you have something going on with your apache configuration.  I say that because code you are typing is essentially THE test line.  If you are configuring everything yourself, that is, without the default LAMP install, I would open the apache2.conf and see if anything seems fishy on line 298.

I'm assuming you have tried it without the phpinfo() call and simply added it for feedback.

---

### Post by mbeach on 2008-08-02
the location of your php file should not be the site-enabled folder.

put your php file in /var/www/

the sites-enabled folder typically houses symbolic links to conf files in sites-available.  It should not contain php or html files.

Apache's error is telling you that it is trying to read your php file as a configuration file for apache which is not what you want.

---

### Post by TennSeven on 2008-08-02
Thanks Mbeach! I knew it had to be something dumb that I was doing wrong.  I am trying to teach myself how to set up mysql and this was basically the very first step in making sure everything was installed.  I must have mis-read the directions I found online.

I moved the file to /var/www and now I can navigate to [http://localhost/phptest.php](http://localhost/phptest.php)

Thanks again for the help.

---

