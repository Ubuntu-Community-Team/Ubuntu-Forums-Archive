---
title: "PHP and Unable to Run Tikiwiki or PHPmyadmin on Ubuntu 11.04"
date: 2011-06-08
forum: Server Platforms
---

### Post by mowestusa on 2011-06-08
I'm a Beginner Trying to Setup a Small Office Intranet using Ubuntu 11.04.

I did the server install and installed LAMP and Samba for our Ubuntu server. I'm having issues with the LAMP install.

- 1. Created a info.php (<?php phpinfo(); ?>) file to see if PHP was working on my server. When I try to bring up that page it says
```
Server error
The website encountered an error while retrieving http://192.168.1.80/info.php. It may be down for maintenance or configured incorrectly.
```

- I have checked the error.log, and I get the following related to this:
```
[error] [client 192.***.*.***] File does not exist: /var/www/info.ph 
```
- I have not idea why the above error has "info.ph" and says that the file is not there when clearly it is there and I did spell it out according the browser error "info.php".

- 2. I believe I may have an issue with PHP or the server set up that is preventing me from installing Tikiwiki. It sees the database and then stalls and circles back around to the beginning again, never finishing the install where it would populate the database and give me the chance to set preferences.

- 3. I also can't log into PHPmyadmin. It installed correctly, and I get the welcome screen with the log in, but then it does not let me log in with mysql root account or the user account that I created for mysql when I created my first database from the mysql command line.

I'm guessing that all of the above is because I have something messed up with my LAMP install or the PHP install in particular. Any thoughts?

---

### Post by mowestusa on 2011-06-09
SOLVED issue #1 I can see phpinfo()

> **mowestusa said:**
> I'm a Beginner Trying to Setup a Small Office Intranet using Ubuntu 11.04.

I did the server install and installed LAMP and Samba for our Ubuntu server. I'm having issues with the LAMP install.

[SOLVED] - 1. Error seeing an info.php (<?php phpinfo(); ?>) file [SOLVED]

- 2. I believe I may have an issue with PHP or the server set up that is preventing me from installing Tikiwiki. It sees the database and then stalls and circles back around to the beginning again, never finishing the install where it would populate the database and give me the chance to set preferences.

- 3. I also can't log into PHPmyadmin. It installed correctly, and I get the welcome screen with the log in, but then it does not let me log in with mysql root account or the user account that I created for mysql when I created my first database from the mysql command line.

I'm guessing that all of the above is because I have something messed up with my LAMP install or the PHP install in particular. Any thoughts?

---

