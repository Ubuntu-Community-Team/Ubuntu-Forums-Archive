---
title: "http://localhost/index.php and white page"
date: 2010-06-13
forum: Server Platforms
---

### Post by Abera on 2010-06-13
When I am running my server and in the browser I go to the link
[http://localhost/index.php](http://localhost/index.php)
and the page comes up white. It's from my phpbb live site and doesn't want to run in LAMP. No problem when I run it on my Win system and WAMP. Any reason knowen for the problem? 

Also same server different dir [http://localhost/gjr/index.php](http://localhost/gjr/index.php) I get 

Forbidden

You don't have permission to access /gjr/index.php on this server.
Apache/2.2.14 (Ubuntu) Server at localhost Port 80

another phpbb test forum and have read and write permissions.

Thanks

---

### Post by Ryan Dwyer on 2010-06-13
If you browse to /index.php and view the page source, do you see PHP code?

If so, you need to install PHP.
sudo apt-get install libapache2-mod-php5

---

### Post by Abera on 2010-06-13
> **Ryan Dwyer said:**
> If you browse to /index.php and view the page source, do you see PHP code?

If so, you need to install PHP.
sudo apt-get install libapache2-mod-php5
I have the whole LAMP server installed.

---

### Post by rukiaEnix on 2010-06-14
check your directory permissions where you have your index

---

### Post by Ryan Dwyer on 2010-06-14
If it were a directory permissions problem then Apache would throw up a forbidden error instead of a blank page.

Again, please check the source code of the page and see if the PHP code is showing up. Just because it's installed doesn't mean it's configured to use it.

---

### Post by rukiaEnix on 2010-06-14
> **Abera said:**
> When I am running my server and in the browser I go to the link
[http://localhost/index.php](http://localhost/index.php)
and the page comes up white. It's from my phpbb live site and doesn't want to run in LAMP. No problem when I run it on my Win system and WAMP. Any reason knowen for the problem? 

Also same server different dir [http://localhost/gjr/index.php](http://localhost/gjr/index.php) I get 

[COLOR=Red]Forbidden

You don't have permission to access /gjr/index.php on this server.[/COLOR] [COLOR=Red]
Apache/2.2.14 (Ubuntu) Server at localhost Port 80
[/COLOR] 
another phpbb test forum and have read and write permissions.

Thanks

I think this HAS something to do with permissions :p

---

### Post by rukiaEnix on 2010-06-14
install phpMyAdmin and look again at your localhost/index.php

---

### Post by Abera on 2010-06-14
> **rukiaEnix said:**
> install phpMyAdmin and look again at your localhost/index.php
I have the full LAMP server installed and phpmyadmin. I need to set the Correct Chmod Values to:

    * config.php
          o 666 before installation
          o 644 after installation
    * All other files - 644
    * All directories - 755
          o There are some exceptions when it comes to directory permissions,
                + The files directory - 777
                + The cache directory - 777
                + The store directory - 777
                + The images/avatars/upload directory - 777

That would be fine, but I can't even bring Filezilla up to set them. I know that is these aren't set right they will not show. I have no idea on how to set them through the terminal, or any other way.

Thanks

---

### Post by rukiaEnix on 2010-06-14
in terminal is like this.

for example with config.php and 666 permission:

```

chmod 666 config.php 

```

---

### Post by Abera on 2010-06-14
I Had to chmod all of the files and directories individually. I can not get any FTP client to work either and new to Linux I couldn't think of any other way. The page started to come up, but I guess I need an extension., or something.     

Failed opening required './includes/acm/acm_file.php'  (include_path='.:/usr/share/php:/usr/share/pear') 


**Warning**:  require(./includes/acm/acm_file.php) [[function.require]("http://localhost/gjr/function.require")]:  failed to open stream: Permission denied in **/var/www/gjr/common.php**  on line **186**

**Fatal error**:  require() [[function.require]("http://localhost/gjr/function.require")]:  Failed opening required './includes/acm/acm_file.php'  (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/gjr/common.php**  on line **186**

When I click on the [[function.require]("http://localhost/gjr/function.require")] in another tab it says 
**Not Found**

 The requested URL /gjr/function.require was not found on this server.

What is it, where do I get it and what do I do with it?:confused:
Thanks

---

### Post by Ryan Dwyer on 2010-06-15
You seem to have screwed up your file permissions.

sudo chmod -R o+r /var/www

That will make everything in /var/www readable by other (ie. everything), which is how it should be.

---

### Post by Abera on 2010-06-15
The permissions are set to phpbb's standards.
* config.php
          o 666 before installation
          o 644 after installation
    * All other files - 644
    * All directories - 755
          o There are some exceptions when it comes to directory  permissions,
                + The files directory - 777
                + The cache directory - 777
                + The store directory - 777
                + The images/avatars/upload directory - 777
So that isn't it.
Thanks

---

