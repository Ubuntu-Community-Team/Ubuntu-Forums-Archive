---
title: "phpmyadmin install on dapper"
date: 2008-05-26
forum: Server Platforms
---

### Post by elbeano on 2008-05-26
I am working with a server running dapper and want to use phpmyadmin. I installed using apt and the install proceeds with no messages. I understand that the install is into a folder other than /var/www and that there is a symlink setup in /var/www. I've tried to run the setup script, but it will not run. I've checked permissions. I created config directory in /etc/phpmyadmin and chmod o+rw config I've tried to run from:

www/scripts/setup (the actual location)
www/phpmyadmin/scripts/setup

with no success... browser reports unavailable

Looking for suggestions, or pointing to good info for setup of phpmyadmin on Dapper.

---

### Post by windependence on 2008-05-26
Can you post the exact error message you are getting?

-Tim

---

### Post by elbeano on 2008-05-26
Error message:

To browser address: [http://192.168.0.188/scripts/setup.php](http://192.168.0.188/scripts/setup.php)

You tried to access the address [http://192.168.0.188/scripts/setup.php](http://192.168.0.188/scripts/setup.php), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelled and punctuated, then try reloading the page.

---

### Post by windependence on 2008-05-26
OK try this

```
sudo updatedb

sudo locate setup.php
```

Where does it say the file is located?

-Tim

---

### Post by elbeano on 2008-05-26
After running the commands, the setup.php file is reported as located at:

/usr/share/phpmyadmin/scripts/setup.php
usr/share/libraries/phpmyadmin/dbg/setup.php

Nevertheless, I can cd /var/www/scripts and also see a copy there...

---

### Post by windependence on 2008-05-26
Did you create the config directory in the phpMyAdmin directory? Remember, directory names are case sensitive.

-Tim

---

### Post by windependence on 2008-05-26
NM, I see that you created that directory, sorry.

Try running [http://192.168.0.188/phpmyadmin](http://192.168.0.188/phpmyadmin) in your browser and tell me what happens.

-Tim

---

### Post by elbeano on 2008-05-26
Tim,

Thanks for your help. I finally did a manual install of phpmyadmin, after finding out that the location of the web root was NOT in /var/www (vtigerCRM5 install).

I have it working now.

---

### Post by windependence on 2008-05-26
> **elbeano said:**
> Tim,

Thanks for your help. I finally did a manual install of phpmyadmin, after finding out that the location of the web root was NOT in /var/www (vtigerCRM5 install).

I have it working now.

No problem, if you have time read this:


[http://ubuntuforums.org/showthread.php?t=591952](http://ubuntuforums.org/showthread.php?t=591952)

You probably didn't have to go through all that. :)

-Tim

---

