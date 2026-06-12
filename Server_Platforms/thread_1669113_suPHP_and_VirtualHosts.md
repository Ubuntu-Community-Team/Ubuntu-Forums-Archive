---
title: "suPHP and VirtualHosts"
date: 2011-01-17
forum: Server Platforms
---

### Post by [pl]ice on 2011-01-17
Hello,

I got 2 virtual hosts running for a while. One got php scripts.

I would like to use suPHP for e.g.VirtualHost2, so I have compiled it.

Apache loads the module w/out problems. I still can't get suPHP_UserGroup to work on that virtualHost2. (i have compiled it with the correct flag etc)

added to /etc/apache2/apache2.conf
```

LoadModule suphp_module       /usr/lib/apache2/modules/mod_suphp.so

```
Edit: also i've chowned the test file to the correct user/group before testing the whoami.php
Also i've just tried adding the su_PHPGroupName globally and it didn't work for VirtualHOst2
and in /etc/apache2/sites-available/VirtualHost2 i have:

```


<VirtualHost *:80>
#ServerAdmin    xxxx
ServerName      xxx
ServerAlias     xxx
DocumentRoot     xxx
CustomLog        xxx

#enable suPHP engine
suPHP_Engine On
suPHP_UserGroup  someuser someuser
AddHandler application/x-httpd-php .php .php3 .php4 .php5
suPHP_AddHandler application/x-httpd-php
</VirtualHost>


```
While testing,after reseting apache2 with a:
```

<?php

echo "Output of the 'whoami' command:<br /><br />\n";

echo exec('/usr/bin/whoami');

?>

```
on the server, i get;

 Output of the 'whoami' command:

  www-data

I assume that the module is running, but it's not using the user/group :/

Not sure how it should be configured. If i put that into the apache2.conf then it will be global :/


There is nothing in logs, apache, and suphp :(

pls advise.

thank you.

---

### Post by SeijiSensei on 2011-01-17
I've not used the module, but have you created the user(s) and group(s) in /etc/passwd and /etc/group?

---

### Post by Thirtysixway on 2011-01-17
Did you try the example configuration on suPHP site?

[http://www.suphp.org/DocumentationView.html?file=suphp.conf-example](http://www.suphp.org/DocumentationView.html?file=suphp.conf-example)

---

### Post by Thirtysixway on 2011-01-17
Did you try the example configuration on suPHP site?

[http://www.suphp.org/DocumentationView.html?file=suphp.conf-example](http://www.suphp.org/DocumentationView.html?file=suphp.conf-example)

---

### Post by [pl]ice on 2011-01-18
Yes, the user is valid and working. :/

No, i haven't tried. I will try it and let you guys know.

thanks :)

---

### Post by GDR! on 2011-01-18
> **'[pl]ice said:**
> Yes, the user is valid and working. :/

No, i haven't tried. I will try it and let you guys know.

thanks :)

I've never used suphp but if you want easy configuration, mpm_itk works out of the box: [http://www.howtoforge.com/running-vhosts-under-separate-uids-gids-with-apache2-mpm-itk-on-ubuntu-9.04](http://www.howtoforge.com/running-vhosts-under-separate-uids-gids-with-apache2-mpm-itk-on-ubuntu-9.04)

---

