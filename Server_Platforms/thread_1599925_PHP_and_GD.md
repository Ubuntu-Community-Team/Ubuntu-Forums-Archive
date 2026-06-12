---
title: "PHP and GD"
date: 2010-10-18
forum: Server Platforms
---

### Post by mcarrara on 2010-10-18
I need GD for image viewing with PHP.  On the PHP web site it says I have to recompile PHP --with GD.  However in the user comments someone said that with Debian use apt-get install php5-gd and that will work.  Well I tried that and I still do not have GD available.  Is there something I missed with the apt-get method or do I have to recompile PHP?

Mark

---

### Post by mcarrara on 2010-10-19
No response?  Does that mean it is so obvious that I'm an idiot for not seeing the answer, or I am not asking the question correctly?

Mark

---

### Post by SeijiSensei on 2010-10-19
Did you restart the Apache server?  I just installed the php5-gd module to my vanilla Ubuntu server installation, restarted Apache ("sudo service apache2 restart"), and PHP now has GD functionality.

One good way to see what's installed with PHP is to use the phpinfo() function.  Create a simple script in /var/www like this:

```
echo '<? phpinfo() ?>' > /var/www/info.php
```

then view info.php from a browser.  You'll see a complete list of all PHP modules and much other useful information as well.

---

### Post by mcarrara on 2010-10-19
I had restarted Apache2 and I am using the phinfo() function.  But I restarted again, and still no GD. I do have EXIF, but no GD.  I verified that GD-PHP5 was installed and I even tried running apt-get again.  This web server has been running for a couple of years, so I don't remember if I did anything weird when I set up Apache, like put it in a different location.  My concern is if I recompile PHP it might break something else that is running on the web site.

---

### Post by SeijiSensei on 2010-10-19
It sounds like it's not loading the module if it doesn't show up with phpinfo().

Is the copy of PHP up-to-date with an identical release version as php5-gd?  I'm running the 10.04 version of Ubuntu Server where my PHP5 installation is all at version 5.3.2 including php5-gd.  I would have thought installing a more recent version of php5-gd would cause the entire installation to be upgraded as well?

Maybe /var/log/apache2/error.log will have some useful information?

---

