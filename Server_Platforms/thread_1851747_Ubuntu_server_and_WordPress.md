---
title: "Ubuntu server and WordPress"
date: 2011-09-28
forum: Server Platforms
---

### Post by vapor0 on 2011-09-28
I setup a LAMP server on Ubuntu like a year ago, but I haven't done anything with MySQL or PHP. Now I'm trying to follow the [wordpress instructions]("http://codex.wordpress.org/Editing_wp-config.php"), which require me to fill out certain details regarding "the name of your database" and passwords etc. But I don't know / can't remember. Can anyone recommend an easy way to find out these details?

Actually, any help at all would be appreciated. :)

Thanks.:D

---

### Post by Dangertux on 2011-09-28
You have to create your database first using mysql. 

You can do this from a terminal by doing the following. 

```

mysql -u root -p

```
Enter the password you created in lamp setup for mysql root user. 

then

```

CREATE DATABASE mywordpressdbname;
GRANT ALL PRIVILEGES ON *.mywordpressdbname TO 'myuser'@'localhost' IDENTIFIED BY 'myuserspassword';
FLUSH PRIVILEGES;
quit

```

The database name in this example is mywordpressdbname the user is myuser and the password is myuserspassword change as appropriate.

---

### Post by vapor0 on 2011-09-29
Thanks! :p

---

### Post by Dangertux on 2011-09-29
No problem :-)

---

