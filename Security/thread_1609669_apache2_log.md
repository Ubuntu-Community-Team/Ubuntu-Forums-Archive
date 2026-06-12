---
title: "apache2 log"
date: 2010-10-30
forum: Security
---

### Post by jhayes on 2010-10-30
i want to access the /var/log/apache2/access.log from a php page.
i know the php works, i am getting access denied to that file. i tried switching to www-data , creating a link (ln -s /var/log/apache2/access.log access.log in the www folder) could not access the link or the real file as user www-data. 
i tried to make a cronjob, i edited /etc/crontab added this line
*/1   * * * *   root    /media/raid5/www/cronjob1.sh
that script real simple, cp access.log to the www folder, but it does work.  i also have "sudo crontab -e" with a line 
*/1 * * * * /media/raid5/www/cronjob1.sh >/dev/null 2>&1 .
i can change the php/script to point to access.log in the www folder, and copy the access.log there and chmod/chown it to www-data and the ip's will be listed.
i am running out of ideas.


edit
i saw this [http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)
redid the cron job, all is well now
[http://thanksforallthefish.endofinternet.net/server-stats.php](http://thanksforallthefish.endofinternet.net/server-stats.php)
now to add in code that checks arin or whois and reports the country code or something.

solved

---

### Post by Ryan Dwyer on 2010-10-30
If you add www-data to the adm group it should be able to read /var/log/apache2/access.log. That way you don't have to play around with cron.

---

