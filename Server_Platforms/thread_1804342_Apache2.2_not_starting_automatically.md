---
title: "Apache2.2 not starting automatically"
date: 2011-07-14
forum: Server Platforms
---

### Post by ktz84 on 2011-07-14
Apache2.2 always started automatically when the computer rebooted without requiring me to log in however now it will not start until I log in.

```
ls -l /etc/rc?.d/*apache2
```

has the following output:

```
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc0.d/K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc1.d/K09apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc2.d/S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc3.d/S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc4.d/S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc5.d/S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root 17 2011-07-14 20:44 /etc/rc6.d/K09apache2 -> ../init.d/apache2

```

which looking online seems to be what is expected.

Without logging to my desktop session and going to ctrl-alt F2 and running

```
sudo service apache2 status
```

says that apache2 is running.

None of my websites will run. There are no relevant errors in the error.log of either apache2 in var directories or in the virtual host logs for each site.

Any ideas.

I had installed kubutnu desktop and I have tried to remove it again however it is not removing everything as the splash screen that runs before the desktop login screen has a blue box with kubuntu 11.04 in it. I don't know whether that is relevant.

---

