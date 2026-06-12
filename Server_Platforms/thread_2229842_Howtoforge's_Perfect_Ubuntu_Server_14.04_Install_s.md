---
title: "Howtoforge's Perfect Ubuntu Server 14.04 Install script"
date: 2014-06-15
forum: Server Platforms
---

### Post by MerlinW on 2014-06-15
I made this script for myself but it could be useful for you too. If you like the [Howtoforge.com's "The Perfect Server - Ubuntu 14.04 (Apache2, PHP, MySQL, PureFTPD, BIND, Dovecot, ISPConfig 3)" ]("http://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p3") build, you can install/config that in minutes:

1. install a fresh Ubuntu 14.04 server
2. wget [http://merlinw.org/data/install.sh](http://merlinw.org/data/install.sh)
3. chmod +x install.sh
4. sudo ./install.sh
5. Follow the instructions

The script installs apache2, pure-ftpd, quota, clamav, postfix, mailman, dovecot, squirremail, mysql, phpmyadmin, openssh, mc, ISPConfig 3, bind. After the script finished, everything will work.

---

### Post by Tadaen_Sylvermane on 2014-06-16
I have no interest in that type of server but the script is a good start. If may suggest breaking it down into functions and such. Make it easier to read or debug. If you don't mind I may work on that. I'm looking for scripting projects to further my ability.

---

### Post by MerlinW on 2014-06-16
Sure, it's a good idea:)

---

### Post by nerdtron on 2014-06-17
The comments on each section would be a big help to understand what is going on. Also, it would be better if you can ask user input on which programs to install especially if the user doesn't want to install everything that the script offers.

IMO, I'd still prefer using tasksel or manually install/configuring packages myself but your script can help newbies having a hard time setting up their servers.

---

### Post by MerlinW on 2014-06-17
Yeah, as I said I wrote it for myself. About the programs; you need almost everything for ISPConfig. If you want that, I'll comment the code. BTW the script does exactly [this]("http://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p3").
I do everything manually too, but I had to install 6 servers like that, so I wrote a script:) That's the story:)

---

