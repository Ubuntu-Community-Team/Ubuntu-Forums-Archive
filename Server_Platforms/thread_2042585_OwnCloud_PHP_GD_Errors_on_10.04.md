---
title: "OwnCloud PHP GD Errors on 10.04"
date: 2012-08-14
forum: Server Platforms
---

### Post by daryl314 on 2012-08-14
Hello,

I am trying to get OwnCloud running on Ubuntu Server 10.04.  I installed the php5-gd package and restarted Apache, but I am still getting a "PHP module GD is not installed" error.  If I run a test case, it shows that GD is installed using the same logic that OwnCloud appears to use to detect it in lib/util.php (as the code snippet below returns "GD is installed").  Anyone have an idea of how to fix this?

```

echo '<?php if(function_exists("imagepng")){echo "GD is installed\n";}else{echo "GD is not installed\n";} ?>' | php

```

Thanks,
Daryl

---

### Post by SeijiSensei on 2012-08-14
Create a page in the website directory with just this line of code:

```
<?php phpinfo()?>
```

and view it with your browser.  If the module has loaded correctly, you'll see a section of the resulting page that lists the module and its defined parameters.

---

### Post by slooksterpsv on 2012-08-14
You can also try restarting Apache just to make sure it's loading everything:
```

sudo apache2ctl restart

```

---

### Post by daryl314 on 2012-08-16
> **SeijiSensei said:**
> Create a page in the website directory with just this line of code:

```
<?php phpinfo()?>
```

and view it with your browser.  If the module has loaded correctly, you'll see a section of the resulting page that lists the module and its defined parameters.

I don't see any information showing up about the GD module in the info page.  Is there something else I need to do in addition to installing it (apt-get install php5-gd) and restarting Apache?  For some reason function_exists("imagepng") returns true.

"gd" also shows up in the list when I run "php -m"

---

### Post by SeijiSensei on 2012-08-16
The command-line version of php is independent of the php module for Apache, so it won't give you the correct answer.

On my system, the file /etc/php5/apache2/conf.d/gd.ini contains the following code to activate the module:

```

; configuration for php GD module
extension=gd.so

```

Does that file exist on your server?  If not, try just creating it manually, then restart apache, and see if that helps.

---

### Post by daryl314 on 2012-08-16
Creating gd.so worked for me.  For some reason it wasn't installed with php5-gd.

Thanks!

---

