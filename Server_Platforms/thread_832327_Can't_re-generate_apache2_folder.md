---
title: "Can't re-generate apache2 folder"
date: 2008-06-17
forum: Server Platforms
---

### Post by DanielReidal on 2008-06-17
Hi! I'm a newbie.

I have re installed ubuntu 8.0.4 and I installed apache2. I wanted to use my old apache configuration files, so I deleted /etc/apache2 and tried to copy my old apache2 directory to /etc/. Something failed. I tried to run apt-get remove apache2 and after that apt-get install apache2. No warnings, but the /etc/apache2 directory were never created. I have tried serveral times

What am I doning wrong?

Cheers Daniel

---

### Post by windependence on 2008-06-18
You gotta get yourself outta that Windoze "reinstall everything if it doesn't work" attitude. :-)

I suspect you were fine until you went to replace the config file and then it was probably a permissions or ownership issue. Do you still have your old Apache configuration file that you wanted to use? I think I can walk you through doing what you wanted to do. You will need a clean install of Apache, and your old config file.

-Tim

---

### Post by DanielReidal on 2008-06-18
Thanks. I will provide you with more information when I get home tonight...

I will copy my backup apache2 folder and provide you with the warning messages I see when I start the webserver.

Cheers! DR

---

### Post by windependence on 2008-06-18
No problem, I'm sure we can fix it. I work nights here in the states so I will be here.

-Tim

---

### Post by DanielReidal on 2008-06-18
Hi again.

1. I put a copy of my old apache2 directory in /etc/
2. I was not sure about the rights so I did a chmod -R 755 of the apache2 dir. (I can find out proper rights later on)
3. When restarting apache i get the followin message:
-----
dradmin@drserver:/etc/apache2$ /etc/init.d/apache2 restart
open: Permission denied
 * Restarting web server apache2                                                                                                 ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars
Syntax error on line 141 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configurat                         ion
open: Permission denied                                                                                           [fail]
-----

Here are line 140 to 143 in the envvars file:
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

Do you need any more information?

Thanks Daniel

---

### Post by mbeach on 2008-06-21
I might recommend not copying the whole directory, but instead the individual files in sites-available, then enable the sites you want using "a2ensite". 

You'd probably also want to enable any mods you use with
"a2enmod"

I'd probably read through the old files, and make the necessary adjustments in the 'new' conf files (apache2.conf, ports.conf ...).  Unless you have some really non-default like configuration, this approach may prove easier.

When you go to restart apache, do so using:
sudo /etc/init.d/apache2 restart

---

