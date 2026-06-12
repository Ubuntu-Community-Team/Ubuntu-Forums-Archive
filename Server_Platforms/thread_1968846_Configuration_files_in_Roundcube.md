---
title: "Configuration files in Roundcube"
date: 2012-04-29
forum: Server Platforms
---

### Post by 95yj on 2012-04-29
I just finished installing Roundcube using the instructions from Ubuntu at:  [https://help.ubuntu.com/community/Roundcube](https://help.ubuntu.com/community/Roundcube) using the distro which is pretty slick because it's set up as a quick and easy process.

The problem that I'm having now is that making changes to /usr/share/roundcube/main.inc.php (after copying that file from main.inc.php.dist) doesn't result in Roundcube acting any differently after performing "sudo service apache2 rstart".  The first parameter I am changing is to nail the server but that doesn't do anything and the login screen remains the same.

Is there something that needs to be done to force Roundcube to utilize the main.inc.php configuration file or am I doing something wrong here?

---

### Post by 95yj on 2012-04-29
Turns out that the main.inc.php.dist file is in /usr/share/roundcube but when you copy it to main.inc.php, you need to put it into the /etc/roundcube directory.  All is good then.

---

