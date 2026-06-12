---
title: "php5-mysql installed but e107 instilation script states it is not"
date: 2008-04-05
forum: Server Platforms
---

### Post by Death_Sargent on 2008-04-05
When I run the e107 install.php script I get this 

```
e107 requires PHP to be installed or compiled with the MySQL extension to work correctly, please see the MySQL manual for more information.
```

I talk to my administrator who tells me that we are running a fully qualified LAMP. 

He tries running apt-get install php5-mysql and the system states it is already installed.

---

### Post by conjur3r on 2008-04-07
The module may not have been enabled.  Apache may not have been restarted with the new enabled module.

Create a php file with only 
<?php
phpinfo();
?>

and navigate your browser to it.  Does it provide any hints that MySQL is now supported?

---

