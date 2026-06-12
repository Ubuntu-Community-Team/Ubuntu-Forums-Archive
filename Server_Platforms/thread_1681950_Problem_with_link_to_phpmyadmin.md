---
title: "Problem with link to phpmyadmin"
date: 2011-02-05
forum: Server Platforms
---

### Post by JJJollyjim on 2011-02-05
I have a lamp set up on server edition, on an ec2 instance, and I am having a problem with phpmyadmin. I created a symbolic link with "sudo ln -s /usr/share/phpmyadmin /var/www", and when I visit [ip address]/phpmyadmin, google chrome downloads a file named 'download', which has the source of the index.php file of pma. Otherwise php is working fine.

Help? :?

---

### Post by DiSTORT3D on 2011-02-05
Are you sure you do not miss any php5 handlers?

```
LoadModule php5_module        modules/libphp5.so
AddHandler php5-script php 
```

---

