---
title: "Help with Drupal installation"
date: 2008-08-17
forum: Server Platforms
---

### Post by toast4u on 2008-08-17
I have installed Drupal on my server (Ubuntu 8.04), and I get the following message when I go to "http://server/drupal5":[INDENT]Unsupported database type / The database type is unsupported. Please use either mysql for MySQL 3.x & 4.0.x databases, mysqli for MySQL 4.1.x+ databases, or pgsql for PostgreSQL databases. The database information is in your settings.php file.[/INDENT]I am running “Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch” and MySQL server version “5.0.51a-3ubuntu5.1”.  I installed the Drupal package and it setup a database called “drupal5”.  I have tried both “mysql” and “mysqli” for the database type in the settings.php file in “/etc/drupal/5/sites/default/”:

```
if (!isset($dbserver) || empty($dbserver))

        $dbserver='localhost';

$db_url = "$mysqli://root:password@localhost/drupal5";

$db_prefix = '';
```I have never used PHP or SQL before, so I really have no idea where to go from here.  I basically just want to setup Drupal so I can mess around with it on my server.  I would greatly appreciate help from anyone out there on the interweb.

Thanks in advance,
toast4u

---

### Post by windependence on 2008-08-17
How did you install Drupal? If it was from the repositories, it is an old unsupported version and is not recommended. Read the documentation below on installing Drupal 6 manually. It is very easy.

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

-Tim

---

### Post by toast4u on 2008-08-17
> **windependence said:**
> How did you install Drupal? If it was from the repositories, it is an old unsupported version and is not recommended. Read the documentation below on installing Drupal 6 manually. It is very easy.

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

-Tim

Thanks for your tip!  Initially I did use the repository to install Drupal (5).  I purged that Drupal 5 installation and all its associated packages using aptitude.  I then followed the instructions on the page you linked to, and I had no problem at all.  I now have Drupal 6 up and running with the PHP and MySQL versions I had already installed.

Thanks again,
toast4u

---

