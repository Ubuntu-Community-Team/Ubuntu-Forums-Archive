---
title: "field collation coming out as 'latin1_swedish_ci' in MySQL"
date: 2011-08-26
forum: Server Platforms
---

### Post by airspoon on 2011-08-26
I'm running Ubuntu 11.04 with MySQL 5.1.54, Apache 2.2.17 and PHP 5.3.5, each of which I installed and configured separately. I'm asking this question here because I was told the issue probably stems from Ubuntu. 

Anyway, I'm trying to learn MySQL and so through the terminal, I created a simple database, then a table. I then populated that DB table with various fields. Anyway, when I go to phpMyadmin and look at the structure of that table, under the field that is set to varchar(), the collation is set to latin1_swedish_ci (Swedish, case insensitive, it says).

However, when I look at some of my other databases (like those created for Drupal, PHPBB and others), the collation is set to: utf8_general_ci. I'm assuming that my collation should always be set to utf8, right?

Is there a reason that the collation for the one I created in the terminal (as opposed to a script or through phpmyadmin) is set to Swedish (as opposed to utf8/)?

The reason I'm asking here, on the Ubuntu forums, is because someone suggested that this may be due to how I have Ubuntu configured, not necessarily MySQL. 

Thanks in advance for any and all help. It would be greatly appreciated.

---

