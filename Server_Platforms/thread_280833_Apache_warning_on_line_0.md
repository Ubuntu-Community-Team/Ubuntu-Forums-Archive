---
title: "Apache warning on line 0"
date: 2006-10-20
forum: Server Platforms
---

### Post by Coruba67 on 2006-10-20
Hi Guys,

Have been trying to get my Apache server to serve PHP files... though everytime I go to load one up in my brower I get this erroor




Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/html/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0




Not to sure what this means - how can there be an error on line 0
Any idea's?

Thanks in advance!

---

### Post by tomBorgia on 2006-10-20
I think you need to change permissions for the /var/www/html/ directory to www-data (the user apache2 runs with)
So open a terminal -

cd /var/www
sudo chown www-data -R *

This changes the ownership of all the files in /var/www and the "-R" bit operates on the subdirectories as well. 

This tends to happen when the php/html file you've created is created a user other than www-data.

---

### Post by Coruba67 on 2006-10-20
Cool thanks for your help!!

---

### Post by bill123 on 2006-12-11
hhhhmmm 
www-data is a user 
i like linux this thing that every thing in it works as a user, every user have its rights 
excellent man

by the way thanx for help

---

