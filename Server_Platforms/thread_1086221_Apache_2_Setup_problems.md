---
title: "Apache 2 Setup problems"
date: 2009-03-03
forum: Server Platforms
---

### Post by brick1987 on 2009-03-03
Hi,

I am currently setting up a server with Ubuntu 8.04 and Apache2.2. This is my first Linux setup as I am used to 2k3. So if I sound ignorant, i am. At this point I am trying to move some html files from a cd i burned to /var/www. I managed to get everything transferred except for the images folder. I tryed to following to move the files, but all it did was copy the folder and not the images inside of it.
```

sudo cp -rf /media/cdrom0/website/images /var/www
```

I was also having some weird permissions issues with the other html files I transfered. I wasn't able to use them until I ran the following code

```
sudo chmod a+r /var/www/index.html
```

---

### Post by konqueror7 on 2009-03-03
why not create a separate directory instead of the default, i got tired of doing that, just edit the ***/etc/apache2/sites-available/default*** and restart apache...

---

### Post by brick1987 on 2009-03-03
> **konqueror7 said:**
> why not create a separate directory instead of the default, i got tired of doing that, just edit the ***/etc/apache2/sites-available/default*** and restart apache...

Phew, that was a fast and simple response. That did the trick. Thanks :D Any idea why to you have to give permission to /var/www

---

### Post by konqueror7 on 2009-03-04
its just that the ***/var*** folder also contains other applications configurations and data, and just to make it safe...

also, you just could change the folder permission for the ***/www ***, but then it would be better if you could just choose your root directory instead of migrating all you files to that folder...:D

---

