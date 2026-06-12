---
title: "Finding phpmyadmin"
date: 2007-10-24
forum: Server Platforms
---

### Post by coral on 2007-10-24
Hello, just installed phpmyadmin on my clean install of ubuntu. The problem is, i cant find it. Usually it was in serverroot/phpmyadmin/

but now it isn't there. How do i access it from the web?

---

### Post by tmatt95 on 2007-10-24
Hi coral,
I have just got my system working from the same problem. I found the solution in this thread: [http://ubuntuforums.org/showthread.php?t=494724&highlight=installing+phpmyadmin]("http://ubuntuforums.org/showthread.php?t=494724&highlight=installing+phpmyadmin") in which Buffalo Soldier put the following:

phpmyadmin is installed in /usr/share/phpmyadmin. Assuming that you have not changed the default [http://localhost](http://localhost) directory (/var/www), this is what you need to do:

Code:

```
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

after that just point your favourite web browser to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Hope that helps,

Regards,
Matt

---

### Post by raxz on 2007-12-11
hey this worked! thanks. :)

weird on the other releases of Ubuntu I found phpmyadmin under var/www/:lolflag:

---

### Post by ruibernardo on 2007-12-11
Creating a link is not a good idea. You don't see any /var/www/phpmyadmin because there is an alias of /phpmyadmin in apache configuration since you installed . If you type "http://localhost/phpmyadmin" it will be there. If it isn't, check if you installed the LAMP correctly.

There is no need to add a link to /var/www/, unless you want it to be clearly visible to all other users.

To prevent users that access your apache server to access phpmyadmin, look at this post: [http://ubuntuforums.org/showpost.php?p=3688994&postcount=9](http://ubuntuforums.org/showpost.php?p=3688994&postcount=9)

---

