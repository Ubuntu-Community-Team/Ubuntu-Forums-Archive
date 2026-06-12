---
title: "how to make old php site work on ubuntu 18.04"
date: 2019-08-02
forum: Ubuntu Dev Link Forum
---

### Post by mikesalazar on 2019-08-02
I havent been using ubuntu and i'm tryng to run my old applications on ubuntu 18.04.

Before, i would simply import my db onto mysql and paste my www folder to a new server and my browser based applications would run. Now i cant seem to make anything work.
I am a very novice ubuntu user used to copy and pasting to the www folder. any help would be great. thanks!

---

### Post by SeijiSensei on 2019-08-02
Did you install the apache2 package and the php and php-mysql packages? The mysql-server package?

You need to give us a lot more detail than "it doesn't work."

Have you looked at /var/log/apache2/error.log to see what might be failing?

---

### Post by mikesalazar on 2019-08-02
i get an error 404

[h=1]Not Found[/h] The requested URL /*folder*/*subfolder*/index.php was not found on this server.

 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at localhost Port 80

---

### Post by mikesalazar on 2019-08-02
i copied the contents of the  /www folder from my old backups and place it in the /www folder of the new server.

i have installed apache2, mysql-server, php and phpmyadmin.

normally when i do it before in several instances, it would work. the last time i did it was in 2015 in an ubuntu 14.04 instance and it worked. i have done it other times as well.

---

### Post by SeijiSensei on 2019-08-03
> **mikesalazar said:**
> i get an error 404

[h=1]Not Found[/h] The requested URL /*folder*/*subfolder*/index.php was not found on this server.

 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at localhost Port 80

Well that's the problem, right? Check the DocumentRoot specification in the configuration file for this virtual host. If you're using a separate conf file in /etc/apache2/sites-available, you might try disabling 000-default.conf and see if that helps.

---

