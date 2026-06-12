---
title: "PHP myadmin?"
date: 2008-10-03
forum: Server Platforms
---

### Post by askyourpc.com on 2008-10-03
Can PHP Myadmin be setup on linux? Is there a version for linux? Thanks

---

### Post by condonm on 2008-10-03
It most certainly can be installed on Linux, by far the best and easiest way to go about so is to install LAMP (linux, apache, mysql and php) onto your local computer and your server: [http://wiki.vpslink.com/HOWTO:_Install_LAMP_on_Ubuntu_6.06#LAMP_Installation]("http://wiki.vpslink.com/HOWTO:_Install_LAMP_on_Ubuntu_6.06#LAMP_Installation")

If you already have everything you need but phpmyadmin running, this site is comprehensive on how to get it running on linux: [http://hostlibrary.com/installing_phpMyAdmin_on_Linux.html]("http://hostlibrary.com/installing_phpMyAdmin_on_Linux.html")

---

### Post by windependence on 2008-10-04
```
sudo apt-get install phpmyadmin
```

Would be much easier. I would try not to compile from source on Ubuntu if you can avoid it because package management will get all screwed up.

-Tim

---

