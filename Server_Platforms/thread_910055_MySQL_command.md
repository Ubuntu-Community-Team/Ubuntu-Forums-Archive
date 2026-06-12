---
title: "MySQL command"
date: 2008-09-04
forum: Server Platforms
---

### Post by satimis on 2008-09-04
Hi folks,


On typing following lines granting privilege;

mysql> GRANT SELECT ON mailserver.*
    -> TO mailuser@localhost
    -> IDENTIFIED BY 'password; [Enter]
Query OK, 0 rows affected (0.00 sec)


I discovered later miss-typing "mailuser" as "maluser".  Please advise how can I rectify it.  Or how to delete that privilege and then recreate another one.



Besides what command shall I run to show virtual users

mysql> show virtual_user

doesn't work.


TIA


B.R.
satimis

---

