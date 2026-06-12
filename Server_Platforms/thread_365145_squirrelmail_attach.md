---
title: "squirrelmail attach"
date: 2007-02-19
forum: Server Platforms
---

### Post by enriquecm on 2007-02-19
Good How to 
[URL="http://flurdy.com/docs/postfix/index.html"]http://flurdy.com
[/URL]

Ok First I want to explained somethig

How u can up the MB of u squirrelmail attach?

vim /etc/php4/apache2/php.ini
Search this and change it

> 
memory_limit
post_max_size
upload_max_filesize


Next :
```

Restart the service Apache
/etc/init.d/apache2 restart

```

The last:
vim /etc/postfix/main.cf

add this line to increment ure limit mail box
```

message_size_limit=100240000 
virtual_mailbox_limit=100240000 

```

OK
```

/etc/init.d/postfix restart

```

---

