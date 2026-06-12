---
title: "Setting default folder an external USB drive - Apache2"
date: 2010-08-22
forum: Server Platforms
---

### Post by razastarr on 2010-08-22
So, i have set up my Apache2 server and i have this question. Because my netbook (eeePC 701 4g surf) has a very small SSD Drive (4GB) is it possible to set the default directory of apache to be an external USB Drive? And if it is, how?

Sorry for my bad english, English is not my native language.

---

### Post by razastarr on 2010-08-23
I changed my /etc/apache2/sites-available/default file but now i get an 403 error. I tried chmod the USB but nothing happened. So I did a small research and i found that i can't chmod FAT32 filesystem. So any ideas? If i format my usb to NTFS, will it be ok?

---

### Post by kevin11951 on 2010-08-23
Why not just mount the drive as /var/www?  You may need to update permissions, but it would work.

Example:
```
sudo mount -t auto /dev/sdb1 /var/www
```

Then:
```
chown -R www-data:www-data /var/www
chmod -R 0755 /var/www
```

And that should work, if it does, you can add a line to fstab to automount that drive as /var/www.  

Let me know if you want me to post the line for you.

---

