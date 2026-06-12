---
title: "apache directory permissions"
date: 2011-12-08
forum: Server Platforms
---

### Post by LBokkers on 2011-12-08
Hello everyone,

I have been developing a website on a private apache installment, no problems. Until today, I created a new directory (not as an admin or root) called "trash" in the website's folder, when my php script tries to write files to it, I got messages that it was denied permission. But it can write to other directories in the website's folder.
So I though I tried running various chown and chmod commands over the /var/www directory. But now, all the permissions are messed up as php cannot access any directory or file.

Can someone please tell me how I can allow apache/php to read/write from/to files in /var/www folder?

---

### Post by Lars Noodén on 2011-12-08
The folder that PHP will write to can, with risk, be owned by www-data.  The others should be owned by root, with group root.

---

### Post by LBokkers on 2011-12-08
Thanks a lot, it works now.
One more question. Is there a way I can allow both www-data and myself ($USER) to read/write from/to the /var/www directory?

---

### Post by Lars Noodén on 2011-12-08
You could make it owned by www-data and then set the group to one that you are a member of.

```

sudo addgroup webmasters

sudo gpasswd --add lbokkers webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

---

### Post by LBokkers on 2011-12-08
Thanks a lot, everything is working now!

---

