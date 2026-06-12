---
title: "folder name with space as document root for apache"
date: 2008-07-12
forum: Server Platforms
---

### Post by karatekid on 2008-07-12
i have just installed apache and php on my hardy(dual boot with windowsXP).
i wanted to change my document root to the folder i have been using under windows.
however i have named the folder as "web designing".as such now i am unable to set the document root to this folder becuase of the space.
the error when i restart the server after enabling my site
```


 * Restarting web server apache2 
Syntax error on line 5 of /etc/apache2/sites-enabled/mysite:
DocumentRoot takes one argument, Root directory of the document tree

```

Note: i had mistakenly posted this in the wrong section(networking) earlier , now i am reposting.

---

### Post by hyper_ch on 2008-07-12
put the whole path in quotes ""

---

### Post by karatekid on 2008-07-12
thanx a lot.
i tried  putting the quotes earlier also but put them only around the folder name and not the whole path.

---

### Post by windependence on 2008-07-12
Or rename the folder to web_designing.

-Tim

---

