---
title: "Apache and PhpMyAdmin problem!"
date: 2008-08-27
forum: Server Platforms
---

### Post by nightmare0 on 2008-08-27
Ok I'm trying to get a testing server running tonight, but i doubt it will work. I have installed and removed apache2 and phpmyadmin multiple times due to the fact that either the phpmyadmin folder wouldn't appear, now that I got it to when i went to localhost, when i try to open it, it asks if i want to download a PHTML file? Why and how do I fix this? 

Running Ubuntu SE 8.04.1 with GUI and some CLI :)

---

### Post by windependence on 2008-08-27
<sigh>

Installing and uninstalling to fix a problem is the Windoze fix.

Now, you probably have remnants of the old installs hanging around and that may be affecting your install. 

Also, you don' have to be on the same box for phpmyadmin, in fact, it's really designed for access from other computers. Again, the Windoze way is to do everything from the server console or terminal services.

First, remove the package cleanly:

Edit the file /var/lib/dpkg/info/phpmyadmin.prerm and add the following
behind "# Package maintainer's commands follow:"


```
./usr/share/debconf/confmodule
```

Now you can do


```
sudo apt-get remove phpmyinstall
```

If this doesn't work, let me know.

After you get the clean uninstall, then install again.

```
sudo apt-get install phpmyadmin
```

Once phpMyAdmin is installed point your browser to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to start using it. You should be able to login using any users you've setup in MySQL. 

-Tim

---

