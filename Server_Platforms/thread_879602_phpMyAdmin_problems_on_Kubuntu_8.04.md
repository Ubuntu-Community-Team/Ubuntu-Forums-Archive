---
title: "phpMyAdmin problems on Kubuntu 8.04"
date: 2008-08-04
forum: Server Platforms
---

### Post by kenhead on 2008-08-04
Hi, I've got some problems with my phpMyAdmin. I've installed everything from this guide ( [http://rockmanx.wordpress.com/category/kubuntu/](http://rockmanx.wordpress.com/category/kubuntu/) ), but nothing comes up when I type "http://localhost/phpmyadmin" - and - guess what - the /var/www/ folder is also empty for phpMyAdmin folders and/or files. What went wrong? What do I do to fix it?

---

### Post by hvc123 on 2008-08-04
you could always type this 

ln -s /usr/share/phpmyadmin /var/www/ 

then goto [http://localhost/127.0.0.1/phpmyadmin](http://localhost/127.0.0.1/phpmyadmin)...

that will work

---

### Post by studlybw on 2008-08-06
Same problem here. The phpmyadmin folder and the apache2 folder weren't even created in the var/www directory. Apache seems to be running fine. When I go to localhost I get the "It Works" page but php is not working. I've followed all of the directions that I've found in many tutorials and all of them show those two folders being created and mine didn't so it appears that something is going wrong in Kubuntu 8.04. I used the synaptic package manager to install all of the required components.

Any help would be appreciated.

---

