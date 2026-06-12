---
title: "how do i change permissions in /var/www/"
date: 2007-10-18
forum: Server Platforms
---

### Post by demiurgen on 2007-10-18
i have set up apache and php.
then, in terminal,  i did: gksudo gedit /var/www/testphp.php where i entered: <?php phpinfo(); ?> and as you can see that works: [http://www.morganwaage.no/testphp.php](http://www.morganwaage.no/testphp.php)

then i did alt F2 and gksudo nautilus.
then i went to the www folder and changed the permissions and owner to me (my account).

then i created index.php where i entered: <?php phpinfo(); ?> and the result is here: [http://www.morganwaage.no/index.php](http://www.morganwaage.no/index.php)


how is that possible? what have i done wrong here??

---

### Post by James79 on 2007-10-18
Apache is run as user "www-data". If that user does not have access to the php script, apache won't be able to read and parse it.

Either make your file readable to all, or give ownership of it to www-data.

Does that make sense?

---

### Post by demiurgen on 2007-10-19
thanks! that worked.

is there a command i can run in terminal to allow every user access to all files and subfolders in a folder???

---

