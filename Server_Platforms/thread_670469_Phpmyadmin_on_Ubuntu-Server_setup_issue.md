---
title: "Phpmyadmin on Ubuntu-Server setup issue"
date: 2008-01-17
forum: Server Platforms
---

### Post by tet3828 on 2008-01-17
Hey guys, I asked this question in a PHP only fourm and it yeilded zero replies. Hopefully its not too far out of the scope here.

I am trying to set up phpmyadmin on my server. I am using a linux box (ubuntu-server 7.10 w/ a LAMP server running)  It appears to me that the home directory of my server is /var/www

so I copied the extracted phpmyadmin files into a folder with in the /var/www directory.

 now I have /var/www/phpmyadmin/

I am having trouble understanding exactly what to put in this config.inc.php file here is what i've done so far:

Code:
[PHP]<?php

$i=0;
$i++;
$cfg['Servers'][$i]['user']          = 'catuser';
$cfg['Servers'][$i]['password']      = 'admin'; // use here your password
?>[/PHP]
I did not know exactly what to do here... as you can see I just put my info after the equal signs. The documentation included didn't explain it enough for a linux noob such as myself so I guessed.

This is the result I get when I try to load the phpmyadmin program (by opening the index file on the server of course):

```
Warning: require_once(./libraries/common.inc.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/phpmyadmin/index.php on line 34

Fatal error: require_once() [function.require]: Failed opening required './libraries/common.inc.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/phpmyadmin/index.php on line 34
```

---

### Post by tet3828 on 2008-01-17
It never ceases to amaze me how a silly mistake can put a 2.5 hour cramp on your work day...

I didn't copy all the files over from the compressed folder required to run the program

---

