---
title: "MySQL and user's permissions for BD drop"
date: 2015-10-13
forum: Server Platforms
---

### Post by CrewDK on 2015-10-13
I created new local user on my mysql server and also created BD with the same user's name. I added all privileges on this BD to this user. 

>SHOW GRANTS FOR dou@localhost;
+---------------------------------------------------------------------------------------------------------------+
| Grants for dou@localhost                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'dou'@'localhost' IDENTIFIED BY PASSWORD '*****' |
| GRANT ALL PRIVILEGES ON `dou`.* TO 'dou'@'localhost'                                                    |
| GRANT ALL PRIVILEGES ON `dou\_%`.* TO 'dou'@'localhost'                                                 |
+---------------------------------------------------------------------------------------------------------------+
OK. All looks fine. User can login with phpmyadmin to my server and user see only it's own BDs. And there is my problem:  user can create any new BD's with name "username_bla-bla-bla..." but can't delete ANY of this BD. In the phpmyadmin user even cant see any checkboxes near BD name in BD list. And i cant understand which privileges i must add to user, so he could delete he's own BD's. Can some one help me with this?

---

### Post by CrewDK on 2015-10-13
OK. As i found out this isn't mysql problem, but phpmyadmin. 

```
$cfg['AllowUserDropDatabase']   = TRUE;
``` setting this in PMA config fix my problem.

---

