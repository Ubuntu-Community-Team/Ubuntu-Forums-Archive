---
title: "running phpMyAdmin setup script"
date: 2011-10-31
forum: Server Platforms
---

### Post by quadrantids on 2011-10-31
Hello

I have installed phpMyAdmin (Ubuntu 11.10) and I'm very pleased with it.

I cannot find out how to run the setup script. For example localhost/phpmyadmin/setup returns a message asking for Username and Password. When I insert my relevant details as root on the MySQL account nothing happens.

If I look inside var/www I see no phpMyAdmin files. (the config.inc.php seem to be in .etc/phpmyadmin.)

How can I run the web based setup script? (I want to change the appearance settings such that the Mainframe Browse mode just uses icons and not icons and labels which take up to much room on my screen.)

I'd be really grateful if someone could help!

---

### Post by brighty22 on 2011-10-31
Could you manually download phpMyAdmin, and use the config files included on your installation? Just an idea.

IMO the phpMyAdmin package is more trouble than it's worth... I much prefer the tarball downloads on phpmyadmin.net.

---

### Post by billschu on 2011-12-28
same issue as quadrantids (Xubuntu 11.10) 

installing from tarballs has been problematic in the past and besides, there's no way install is gonna be easier than from a deb package

deb install works fine except for setup script not permitting login of either mysql root user or phpmyadmin user

done fresh installs and tried using same password for mysql root and phpmyadmin users, no joy - guessing problem has to be with setup.php

---

### Post by sohmc on 2011-12-28
> **billschu said:**
> installing from tarballs has been problematic in the past and besides, there's no way install is gonna be easier than from a deb package

I've been using phpMyAdmin for several years and have never had problems using tarballs directly from phpMyAdmin...and why should you?  It's a self-contained web application.

I've never tried installing from apt-get, but like I said, there really is no need to since there is no special build required.

But to the question at hand, my guess is that myphpadmin config files are located somewhere within /lib/apache2.  To find the exact location, look in /etc/apache2/sites-available and find your myphpadmin location.  You should be able to edit the appropriate files from there.

---

