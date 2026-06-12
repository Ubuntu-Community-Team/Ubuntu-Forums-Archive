---
title: "error when go to http://localhost/moodle/admin"
date: 2008-07-12
forum: Server Platforms
---

### Post by q8ytop on 2008-07-12
hi there

i make my full installation from this site [http://schoolforge.org.uk/index.php/Installing_Moodle_on_an_Ubuntu_workstation](http://schoolforge.org.uk/index.php/Installing_Moodle_on_an_Ubuntu_workstation) step by step and the apache2 it is work but when i go to this address by using the browser

[http://localhost/moodle/admin](http://localhost/moodle/admin)

it is give me this error

> 
Error: Database connection failed.

It is possible that the database is overloaded or otherwise not running properly.

The site administrator should also check that the database details have been correctly specified in config.php


how can i fix this problem

thank you for halp

---

### Post by Thirtysixway on 2008-07-13
You need to edit the config.php file and enter your mysql database connection info.

---

### Post by q8ytop on 2008-07-13
> **Thirtysixway said:**
> You need to edit the config.php file and enter your mysql database connection info.

where can i find this config file and what i must do for it to be good config to work ?

---

