---
title: "phpmyadmin"
date: 2006-09-24
forum: Server Platforms
---

### Post by EneWolverine on 2006-09-24
Hi all,

I've setup my server using the following tutorial:

[http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to](http://davidwinter.me.uk/articles/2006/08/09/ubuntu-dapper-web-server-how-to)

Everything seems to be working fine except the installation of phpmyadmin. I've managed to install it and setup the config file. I then setup the password for the root user through the mysql terminal prompt. Problem now is however that I can't get into phpmyadmin. I've set it up with http authentication and just filled in:

user: root
password: setpassword

where setpassword is the password I set at the prompt in the terminal

However for some reason it just doesn't log in.

So i thought maybe it was the fact that I had selected http authentication so I changed that to config to test it out and filled in the user/pass in the config file but still it doesn't give me access.

I then added a new user using INSERT in mysql.user and gave that user all priveleges. I set a password for that and again tried through both http and config auth to get into phpmyadmin but to no avail.

I don't know what's going on now. Anyone have any suggestions why I might not be able to get into phpmyadmin?

Have I missed something out?

Thanks in advance,

The Wolverine :D

---

### Post by chrisfay on 2006-09-24
This is all you need in your config.inc.php file:

```
<?

$i=0;
$i++;
$cfg['Servers'][$i]['user']          = 'usernamehere';
$cfg['Servers'][$i]['password']      = 'passwordhere'; // use here your password

?>
```

Respectively replacing 'usernamehere' with your 'username' and 'passwordhere' for your 'password'.

---

### Post by EneWolverine on 2006-09-24
I pretty much have that in my file now, but I want to get it working with http auth as I want to access it from outside. Below is my config file. It's very strange why this isn't working cause thru command-line I can log into the mysql server with my username and password but it doesn't seem to work for some reason for phpmyadmin.

The Wolverine :D

```

<?php

/* $Id: config.sample.inc.php,v 2.1.2.2 2006/08/28 08:14:14 nijel Exp $ */
// vim: expandtab sw=4 ts=4 sts=4:

/**
 * phpMyAdmin sample configuration, you can use it as base for 
 * manual configuration. For easier setup you can use scripts/setup.php
 *
 * All directives are explained in Documentation.html and on phpMyAdmin 
 * wiki <http://wiki.cihar.com>.
 */

/* 
 * This is needed for cookie based authentication to encrypt password in 
 * cookie
 */
$cfg['blowfish_secret'] = ''; /* YOU MUST FILL IN THIS FOR COOKIE AUTH! */

/* 
 * Servers configuration
 */
$i = 0;

/* 
 * First server
 */
$i++;
/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'http';
/* Server parameters */
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'tcp';
$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
$cfg['Servers'][$i]['extension'] = 'mysql';
/* User for advanced features */
$cfg['Servers'][$i]['controluser'] = 'pmausr';
$cfg['Servers'][$i]['controlpass'] = 'pmapass';
/* Advanced phpMyAdmin features */
$cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
$cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
$cfg['Servers'][$i]['relation'] = 'pma_relation';
$cfg['Servers'][$i]['table_info'] = 'pma_table_info';
$cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
$cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
$cfg['Servers'][$i]['column_info'] = 'pma_column_info';
$cfg['Servers'][$i]['history'] = 'pma_history';

/* 
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';

?>


```

---

### Post by az on 2006-09-24
That a funny tutorial.  He uses a lot of stuff from source instead of from the repos.  Maybe use this:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

