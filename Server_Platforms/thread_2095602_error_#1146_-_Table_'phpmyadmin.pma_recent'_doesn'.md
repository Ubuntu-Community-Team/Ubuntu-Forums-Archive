---
title: "error #1146 - Table 'phpmyadmin.pma_recent' doesn't exist"
date: 2012-12-17
forum: Server Platforms
---

### Post by Toriku on 2012-12-17
this morning I loaded up phpMyAdmin after not using it for over a week, and was greeted by the message:

> 
SELECT  `tables` 
FROM `phpmyadmin`.`pma_recent`
WHERE  `username` = 'root'

MySQL said: 

#1146 - Table 'phpmyadmin.pma_recent' doesn't exist 


 I can't see a database with the name "phpMyAdmin or anything similar" on either this server with the error
or with either of my other servers that aren't outputting any errors; also it seems that whatever is causing the error isn't impeding the programs that use MySQL;
I can't find anything on Google that seems relevant, and I've rebooted the machine and I still get this message as soon as I log into phpMyAdmin...
 Can anyone shed any light on what could be causing this problem, or how to clean it up?

Thanks

---

### Post by Toriku on 2012-12-18
I've still not figured it out, or found any useful information on Google, has anyone else encountered this before?

---

### Post by Toriku on 2013-01-18
if anyone else has this problem, use phpMyAdmin to import "create_tables.sql" from the examples folder of phpMyAdmin

---

### Post by vasheck1 on 2013-04-12
Toriku, thanks so much for the tip! worked like a charm and you've saved me hours of work and searching... :)

---

### Post by SynthesizersFTW on 2013-05-02
> **Toriku said:**
> if anyone else has this problem, use phpMyAdmin to import "create_tables.sql" from the examples folder of phpMyAdmin

helpful - but you omitted the path, which is more useful if you arrived here via Google and don't know where that is, exactly:

/usr/share/doc/phpmyadmin/examples/

Just use the import feature and choose "create_tables.sql.gz".

For more info, see:
[http://wiki.phpmyadmin.net/pma/Configuration_storage]("http://wiki.phpmyadmin.net/pma/Configuration_storage")

---

### Post by xevaz on 2013-06-08
> **Toriku said:**
> if anyone else has this problem, use phpMyAdmin to import "create_tables.sql" from the examples folder of phpMyAdmin

: D muchas gracias compañero
solo me registre en el foro para agradecer tu ayuda

---

### Post by ekeyte on 2013-06-29
Just as an FYI, anyone looking for a quick solution, when viewing the config-db.php file in etc/phpmyadmin, note that the dbname variable is the name of the table that the create_tables.sql file generated. This will allow you to resume use of PMA without any issues.

---

### Post by Gary_Woodfine on 2013-08-22
> **SynthesizersFTW said:**
> helpful - but you omitted the path, which is more useful if you arrived here via Google and don't know where that is, exactly:

/usr/share/doc/phpmyadmin/examples/

Just use the import feature and choose "create_tables.sql.gz".

For more info, see:
[http://wiki.phpmyadmin.net/pma/Configuration_storage](http://wiki.phpmyadmin.net/pma/Configuration_storage)

Thank you so much this helped me solve my issue. It appears my whole Lamp Server configuration failed. 
After I completed the steps above, I also received another error where at the bottom of the page I was getting read error message with
[h=2]Connection for controluser as defined in your configuration failed.[/h]I had to basically uninstall and re-intall phpmyadmin
[PHP]
sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin
[/PHP]

Details can be found here [http://ubuntuforums.org/showthread.php?t=1152326&page=2](http://ubuntuforums.org/showthread.php?t=1152326&page=2)

All seems to working fine now

---

