---
title: "word press is a mess"
date: 2011-05-15
forum: Server Platforms
---

### Post by boblizar on 2011-05-15
the ubuntu install has users hand symlinking to the /usr/share/wordpress to /var/www directory....
this package needs the wp-config.php toyed around with a bit.....

```

sudo chown www-data wp-config.php
sudo chgrp www-data wp-config.php
chmod 440 wp-config.php
also need to make a wp-content/uploads directory owned and grouped to www-data

```

dont show users the database password!

clearly this package is neglected because i can find wordpress jobs online :guitar: :popcorn:  im just gonna delete the wordpress from synaptic and drop in the tarball from wordpresses website.

---

### Post by tgm4883 on 2011-05-15
Did you file a bug on launchpad? I'm not sure what this post is doing here in the security forum. 

If it's a bug, it should be in launchpad. If you are asking for help I must have missed that part of your post

---

### Post by uRock on 2011-05-15
Moved to Server platforms

---

### Post by rubylaser on 2011-05-16
Using the tarball from Wordpress is a much better solution (if you want it to be up to date).  I always setup wordpress this way, and it's pretty easy.

---

