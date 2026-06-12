---
title: "Mapserver Apache www-data user"
date: 2010-01-15
forum: Server Platforms
---

### Post by gazz1982 on 2010-01-15
I have set up a mapserver, everyting is working except no map is displayed, it looks like a problem with the tmp folder where the images should be writing to. I have searched for a solution and it seems that the user group needs to be www-data, however on my system apache is set as root not www-data and www-data does not exist as a group. Can I simply create this group? if so how?

Then I assume I just do the following:

sudo chgrp www-data [path]/tmp
sudo chmod 755 [path]/tmp
sudo chmod g+s [path]/tmp

ls -l should then give drwxrwsr-x

then 

sudo useradd -G www-data [USERNAME]

Am I on the right lines

Thanks

Gary

---

### Post by Lars Noodén on 2010-01-15
> **gazz1982 said:**
> Can I simply create this group? 

Yes.  You can also tell Apache to run as that user and group:

[http://httpd.apache.org/docs/2.2/mod/mpm_common.html#user](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#user)
[http://httpd.apache.org/docs/2.2/mod/mpm_common.html#group](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#group)

---

