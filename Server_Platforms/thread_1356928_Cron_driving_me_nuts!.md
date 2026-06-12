---
title: "Cron driving me nuts!"
date: 2009-12-16
forum: Server Platforms
---

### Post by kindledwind on 2009-12-16
I've got a php script that crunches numbers from some mysql info, then builds a link for the google chart API. It gets the Google chart & fwrite()'s the image to my server for display in a few different websites. The script works great...until I let cron try it.

This is my cron line:
*/5 * * * * TERM=xterm php /var/www/path-to/graph.php

If I become root & execute graph.php from the terminal. It does exactly what it's supposed to do. However, once I let the root crontab do it, the script does everything it's supposed to, EXCEPT write graph1.png. It's not logging any errors anywhere the emails all say it was successful...it just won't write graph1.png!

ls -l from the folder:
-rw-r--r-- 1 root     root  3917 2009-12-17 01:01 graph1.png
-rwxrwxrwx 1 www-data sites 4263 2009-12-17 00:41 graph.php

The 0777 and www-data ownership of graph.php is from me monkeyin with permissions & stuff to see if it would change anything...it doesn't. No combination of permissions on graph1.png and graph.php will allow cron to write graph1.png, been trying for 2 days. chattr-i doesn't change anything either.

Anyone have any idea why root  can make it work, and the root crontab can't? What gives?

Thanks
Todd

---

### Post by kindledwind on 2009-12-16
Oh, and the php path is declared in graph.php by the way.

---

### Post by BkkBonanza on 2009-12-17
You may have already checked this but be sure the parent directory also has execute privilage because the script can't create a file in that dir without it. 

Assume you checked for error messages in the php log location not just from cron email or log.

Also I would try changing the ownership of the php script in case the fact it's owned by www-data causes php to drop privilages when run.

---

### Post by kindledwind on 2009-12-17
augh!

Cron runs from the user's home directory. So, when I set a cronjob up from root to output graph1.png..it writes it to /root/graph1.png, not /path/to/graph.php

2 days of  ](*,) because I didn't run  find / -name

Anyway, sorry I'm linuxtarded.

Todd

---

