---
title: "LAMP problem"
date: 2006-05-26
forum: Server Platforms
---

### Post by brickbat on 2006-05-26
I'm sorry if this has been asked before.  I could not find this problem in other posts but there were so many, I may have missed it.

I just installed Dapper RC

I have installed Apache php5 and mysql

Apache is tested and is working fine.

When I try a simple php script, it is ignored.

I have checked the php with sudo a2enmod php5 and it says it's running.

Here is the script I tried

<HTML>
<HEAD>
<TITLE>Apache Testing</TITLE>
</HEAD>
<BODY>
<?php
echo "If this works, we really did it!";
?>
</BODY>
</HTML>

In Apache2.conf I uncommented

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

and I restarted Apache.

No luck.

---

### Post by mandrakethepenguin on 2006-05-26
[FONT=arial,sans serif,helvetica][SIZE=3][COLOR=#000000][FONT=courier][SIZE=4][COLOR=#a8003b][COLOR=Black][SIZE=2]Darn, I wrote a guide for Apache 1.3, you meant apache2.  Sorry, cant help you.[/SIZE][/COLOR][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by brickbat on 2006-05-26
Yes sorry, I neglected to mention.

Apache2 and PHP5

---

### Post by brickbat on 2006-05-27
ok. the problem was that the line

AddType application/x-httpd-php .php

was missing .html at the end so of course it wasn't parsing html files.

Stupid.

---

### Post by adamkane on 2006-05-27
Install Apache/MySQL/PHP the easy way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

