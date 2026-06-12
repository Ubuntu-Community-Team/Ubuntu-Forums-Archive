---
title: "anyone use drupal?  I am missing 1 step I think"
date: 2009-08-23
forum: Server Platforms
---

### Post by tlarkin on 2009-08-23
Hello everyone:

I have a virtual machine of ubuntu 9.10 (or whatever the newest version is) and I am using it as a test machine to learn and develop for drupal.  I have everything setup and running but the install.php script will not run.

background:

Installed:  Apache2, PHP5, PHP5 cli, mysql (server, client and admin), and downloaded drupal and decompressed it into my web root (/var/www).

Configured:

mysql database, told mysql to use my database, created the settings.php file, configured apache to loop back for DNS (127.0.0.1), granted write access to the settings.php file.

However, when I run [http://localhost/install.php](http://localhost/install.php) from a web browser I get nothing.  It wants to download the file instead of running it.

I ran init.d to make sure all my required processes are running....

Thoughts?  Help?

I posted this on the drupal forums first but no one seems to have an answer for me.

thanks

tom

---

### Post by tlarkin on 2009-08-23
What in the heck was I thinking....

apt-get install for the win

this is why I love debian based Linux distros, the command line package manager rules the universe.

All I had to do was:

```

sudo apt-get install drupal6

```

So once you get all your ducks in row (services, and required packages) you can just run that and be done with it.

---

