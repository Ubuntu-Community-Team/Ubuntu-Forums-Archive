---
title: "Build a form on mysql to set values"
date: 2010-09-11
forum: Server Platforms
---

### Post by xtrmsound on 2010-09-11
Hi..

Is there a way to build a form so an admin can enter and add values to a database:

Example 

```

use squid
insert into passwd values('testuser','test',1,'Test User','for testing purpose'); 
```Is there a free software or an easy to configure script?

Thanks

---

### Post by Ryan Dwyer on 2010-09-11
phpMyAdmin?

---

### Post by xtrmsound on 2010-09-12
Yea. PHPmyadmin does that in an excellent way. 
But I want to build something with my design and add some info on what every value does. I don't want to give access to phpmyadmin to anyone but me.

Thanks

---

### Post by cj13579 on 2010-09-12
> I don't want to give access to phpmyadmin to anyone but me.

phpMyadmin is password protected. You can then distribute passwords to who ever you wanted. Or nobody if that's what you want.

Otherwise you could just write your own really PHP to do the same thing e.g:

[PHP]
$host="host"; 

$username="root";  

$password=""; 

$db_name="database";


mysql_connect("$host", "$username", "$password")or die("Cannot connect to Server"); 

mysql_select_db("$db_name")or die("Cannot connect to Database");

$sql = "INSERT INTO passwd (user, pass, id, desc, comments) VALUES ('test, test, 1, Test, For testing)";[/PHP]

---

### Post by LightningCrash on 2010-09-19
This concept is generally called CRUD Scaffolding and there are many tools for it

google: mysql scaffolding

[http://www.phpscaffold.com/](http://www.phpscaffold.com/)

---

### Post by windependence on 2010-09-19
[http://phpformgen.sourceforge.net/](http://phpformgen.sourceforge.net/)
 
-Tim

---

### Post by memilanuk on 2010-09-19
> **windependence said:**
> [http://phpformgen.sourceforge.net/](http://phpformgen.sourceforge.net/)

Seems kind of abandoned (released for beta in 2007)...

---

