---
title: "gui set up of PHP and MySQL"
date: 2008-04-06
forum: Server Platforms
---

### Post by ianb72 on 2008-04-06
Hi 
I am new to all things servers, but I have just installed a dapper 6.06 LAMP server with the Desktop update and I would like to know if there are there any GUI that are not web based, eg Webmin, that I can set up MySQL and PHP, also create databases on a visual level??

Cheers

Ian

---

### Post by harrybazeegar on 2008-04-06
well i dont know about any GUI stuff...

but command line works pretty fine too..

```

sudo apt-get install mysql-server

```

there is something similar for PHP... but I dont know what...

For any "visual" level of databases you can try phpmyadmin( u will need to install PHP first for that)
otherwise you can work at the command line using mysql client.

After database install be sure to secure it appropriatly... set the root password, make a new user and set the previleges of the user.

---

### Post by ianb72 on 2008-04-06
> **harrybazeegar said:**
> well i dont know about any GUI stuff...

but command line works pretty fine too..

```

sudo apt-get install mysql-server

```

there is something similar for PHP... but I dont know what...

For any "visual" level of databases you can try phpmyadmin( u will need to install PHP first for that)
otherwise you can work at the command line using mysql client.

After database install be sure to secure it appropriatly... set the root password, make a new user and set the previleges of the user.

Thanks for that, I'll give it a go

Cheers
Ian

---

### Post by harrybazeegar on 2008-04-06
try this link... it was really helpful in my web-server-days:
[http://www.server-world.info/en/](http://www.server-world.info/en/)

---

