---
title: "delete default mysql tables"
date: 2010-04-26
forum: Server Platforms
---

### Post by halvors on 2010-04-26
hi!

My MySQL server have two tables named mysql and information_schema, how can i hide this for customers when they login to phpMyAdmin.

Halvor.

---

### Post by windependence on 2010-04-26
The answer is to create a non-privileged user for PHPMyAdmin, but why why why would you want a customer to log into your PHPMyadmin?

Those tables you see are tables you need for the application that store user info and privileges. You don't want to get rid of them, just hide them.

-Tim

---

### Post by ghost_ryder35 on 2010-04-26
> **windependence said:**
> The answer is to create a non-privileged user for PHPMyAdmin, but why why why would you want a customer to log into your PHPMyadmin?

Those tables you see are tables you need for the application that store user info and privileges. You don't want to get rid of them, just hide them.

-Tim

Here is a great thread regarding hiding databases [http://forums.mysql.com/read.php?101,85251,85251](http://forums.mysql.com/read.php?101,85251,85251) 

I grabbed the following code from the above thread so it will be easier to find your answer.

"Place the following code into your config.inc.php file in the phpMyAdmin folder. 
```

$cfg['servers'][$i]['hide_db'] = 'information_schema'; 

```"

---

### Post by halvors on 2010-04-26
Thanks, will try now ;)

---

