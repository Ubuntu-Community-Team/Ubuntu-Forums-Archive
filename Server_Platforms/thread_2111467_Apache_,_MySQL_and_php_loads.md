---
title: "Apache , MySQL and php loads ??"
date: 2013-02-02
forum: Server Platforms
---

### Post by oygle on 2013-02-02
I want to install Apache, MySQL and php5 on a desktop computer, as per the instructions at [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp)

Then simply install/run a 'copy' of a Wordpress site locally.

I'm concerned with the extra "load" this will place on the desktop computer. Or, can I configure Apache to not startup on boot, and only have the MySQL client and server running as needed ?

I may also install phpMyAdmin, as it has a nice interface that I'm used to.

The computer details as follows:

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-37-generic
GNOME 3.4.2

Memory: 3.9 GiB
Processor: Intel® Core™2 Quad CPU Q6600 @ 2.40GHz × 4

Available disk space: 398.8 GiB
Swap size is 1.91 Gb

Oygle

---

### Post by SeijiSensei on 2013-02-02
You won't notice much of any effect on performance unless you're actually serving a publicly-accessible website with lots of traffic.

If you want to start and stop Apache manually, use "sudo service apache2 start|stop".  When Apache and MySQL are installed, they will be configured to start automatically on boot.  You can change that with the "chkconfig" command, though you might need to fix [this bug](http://ubuntuforums.org/showthread.php?p=12479235) first.

---

