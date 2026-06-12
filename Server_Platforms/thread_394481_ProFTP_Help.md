---
title: "ProFTP Help"
date: 2007-03-27
forum: Server Platforms
---

### Post by YellowShadow on 2007-03-27
I have installed ProFTP and I tried to configure it following the tutorial found here, but when I log on and go to /var/www to upload files or delete them it says permission denied. Can someone help me?

---

### Post by 1/0 on 2007-03-27
It sounds like you have the wrong permissions in that folder.

---

### Post by YellowShadow on 2007-03-27
So do I do

```

sudo chmod a+x /var/www

```

?

---

### Post by 1/0 on 2007-03-27
No, that would probably be:

```
sudo chmod -R a+rwx /var/www
```

R for recursive, r for reading, w for writing plus x for executing. But that all depends on what you want to do in the folder (and subfolders). Read and write?

Here's a good guide on chmod btw: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by YellowShadow on 2007-03-27
Thanks a million! Now it works.

---

