---
title: "Configuring MySQL [or] PostgreSQL to work with BitWeaver"
date: 2007-01-18
forum: Server Platforms
---

### Post by Maelgwyn on 2007-01-18
Hey guys - I've install all the req's for a LAMP server, and have logged into the mysql> prompt etc, yet when I try to install BitWeaver it tells me:

```

 		Database type
 												[LIST]
[*][IMG]http://localhost/liberty/icons/warning.png[/IMG] You currently have no Database installed that works here. If you feel this is wrong, please contact the [bitweaver Team]("http://www.bitweaver.org/").[/LIST]
 						The type of database you intend to use.
 			[LIST]
[*][IMG]http://localhost/liberty/icons/warning.png[/IMG] If the database you wish to use is not listed above, the version of PHP on this server does not have support for that database installed or compiled in.
```[/LIST]Is there a way for me to check if mysql is setup to play nicely with APACHE etc?

Thanks :)

---

### Post by jtc on 2007-01-18
Well, since Bitweaver seems to be written in PHP perhaps you could use a simple PHP-script to see how well your PHP cooporates with your MySQL-server?

```

<?php

//Trying to connect to the MySQL-server
$db = mysql_connect("localhost", "username", "password") or die("Couldn't connect to MySQLd");

//Closing the connection
mysql_close($db);

?>

```

---

### Post by Maelgwyn on 2007-01-18
That popped up with a blank screen, so I'm expecting it worked... :)

---

