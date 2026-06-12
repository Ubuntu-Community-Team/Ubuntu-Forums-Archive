---
title: "phpmyadmin ownership"
date: 2012-02-09
forum: Server Platforms
---

### Post by iainjames88 on 2012-02-09
Hi guys,

I'm trying to install phpmyadmin on my Ubuntu 11.10 Server but I'm running in to a few difficulties.

During the installation it asks me to install dbconfig-common and configure apache2, but I get an error message saying:

```
An error occurred while installing the database:

mysql said: ERROR 1049 (42000): Unknown database 'phpmyadmin'
```

I think the installer tries to write the database 'phpmyadmin' to mysql during the installation but doesn't have the correct write privelages. When I chmod o+w -R /var/lib/mysql and try the installation again it works without problem, but obviously this is not the best idea as now everyone has write access.

Can anyone advise? I think the solution would be to find out what user phpmyadmin tries to install under and add it to my www-data group.

Thanks in advance for any advise! :)

---

### Post by iainjames88 on 2012-02-09
I probably should have put this in my first post but I forgot, so I'll mention it here. I'm trying to do this on Amazon Web Services where my user is 'ubuntu' and I've tried the following various combinations of owner:group

ubuntu:root
ubuntu:ubuntu
ubuntu:www-data
www-data:www-data

As you can probably guess, I'm pretty new to this and I'm using AWS as a test/learning environment! :)

Any help would be much appreciated :D

---

