---
title: "Mysql does not show right time"
date: 2023-04-01
forum: Server Platforms
---

### Post by cazz on 2023-04-01
Hi
Now we have summertime here in Sweden I now trying to see why MySQL does not follow the Ubuntu Server time.

In ubuntu it show right time but MySQL show now one hour later.
I have change time zone and I can see it have save the settings in mysql and also ```
/etc/mysql/my.cnf
``` but still does now show right time in MySQL?


```
sudo mysql -e "SET GLOBAL time_zone = '+1:00';"
```

---

### Post by MAFoElffen on 2023-04-02
Did you restart the MySql db to pickup the changes after resetting it? I know that sounds like the obvious. Just making sure...
```

sudo systemctl restart mysql

```

---

### Post by cazz on 2023-04-02
Thanks for the replay
Yes I have restart MySQL, I have even restart server but same result

```
mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2023-04-02 19:52:19 |
+---------------------+
1 row in set (0.00 sec)
```

Time was 20:52:19 when I did run the code.

---

