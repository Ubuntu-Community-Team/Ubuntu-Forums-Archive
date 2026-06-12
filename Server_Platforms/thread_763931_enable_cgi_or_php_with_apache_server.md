---
title: "enable cgi or php with apache server?"
date: 2008-04-23
forum: Server Platforms
---

### Post by shane2peru on 2008-04-23
Ok, I installed 8.04 server.  I had 7.10, and didn't upgrade, this is a fresh install, so I'm having to re-configure everything once again.  Anyhow, I tried installing egroupware and phplist, and whenever I try to load a php page, FireFox asks me what I want to do with the file, download, open it with a program etc.  So I'm missing something like a cgi is not enabled, or php5 is not setup to work with apache2.  I'm sorry if my question is not clear, I really don't know the lingo and how to ask.  Somehow I need cgi, or php enabled.  PHP5 and Apache are installed.  Any help would be appreciated.

Shane

---

### Post by cdenley on 2008-04-23
```
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
```

---

### Post by shane2peru on 2008-04-23
> **cdenley said:**
> ```
sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
```

hmmmm,

```

sudo a2enmod php5
This module is already enabled!

```

Must be a configuration somewhere, or something.  Also it seems I don't have access to mysql, even though I installed it.  

Shane

---

### Post by cdenley on 2008-04-23
Apparently the php5 module is enabled when installed, so the a2enmod command wasn't necessary and the message you received isn't a bad thing. Assuming you installed php5 before, and not the apache php5 module, php web scripts should be working now.

To install mysql server
```

sudo apt-get install mysql-server

```

To reset the mysql root password
```

sudo dpkg-reconfigure mysql-server-5.0

```

---

### Post by shane2peru on 2008-04-23
> **cdenley said:**
> Apparently the php5 module is enabled when installed, so the a2enmod command wasn't necessary and the message you received isn't a bad thing. Assuming you installed php5 before, and not the apache php5 module, php web scripts should be working now.

To install mysql server
```

sudo apt-get install mysql-server

```

To reset the mysql root password
```

sudo dpkg-reconfigure mysql-server-5.0

```
cdenley,  Thanks for the help, I do appreciate it.  I do have that installed to.  I just checked out a web page and found out how to check my php installation, however must be permissions or some other error, because when I open localhost/phplist/lists/index.php  it asks me if I want to save the file.  ahh, I don't know what the deal is.  When I go to localhost/egroupware/  it starts it's setup and tells me it can't connect o the mysql database.  I know I have it installed, however I'm missing some kind of configuration, or my permissions are not correct or something.  I'm not really sure what the problem is.  If you have any ideas I'm open for suggestions.  Thanks again for your help!

Shane

---

### Post by shane2peru on 2008-04-23
ok, it appears that php files only work when they are directly in my /var/www directory, if they are in a sub directory they don't work.  :(  There must be a way of configuring this.  

Shane

**edit:**  sorry for all this info, here is yet another piece to the puzzle.  If I link what I need to /var/www/phplist -> points to actuall location of the phplist it seems to work and gives me this error:
```
Fatal Error: Mysql is not supported in your PHP, recompile and try again.
```
Soooo, mysql is not setup with php, however I'm not sure that I would call that fixed, is that the way it is supposed to be?  odd.  

Shane

---

### Post by Brempie on 2008-04-23
> **shane2peru said:**
> ok, it appears that php files only work when they are directly in my /var/www directory, if they are in a sub directory they don't work.  :(  There must be a way of configuring this.

To enable PHP in subdirectories you have to add that directory to the /etc/apache2/sites-available directory

sudo vi /etc/apache2/sites-available/NameOfSite
```

NameVirtualHost *:80
<VirtualHost *:80>
ServerName WhateverYouWant
DocumentRoot /var/www/NameOfSite
</VirtualHost>

```

sudo a2ensite NameOfSite

---

### Post by cdenley on 2008-04-23
> 
Soooo, mysql is not setup with php


maybe this will help
```

sudo apt-get install php5-mysql
sudo /etc/init.d/apache2 restart

```

---

### Post by shane2peru on 2008-04-23
> **Brempie said:**
> To enable PHP in subdirectories you have to add that directory to the /etc/apache2/sites-available directory

sudo vi /etc/apache2/sites-available/NameOfSite
```

NameVirtualHost *:80
<VirtualHost *:80>
ServerName WhateverYouWant
DocumentRoot /var/www/NameOfSite
</VirtualHost>

```

sudo a2ensite NameOfSite

I have my virtual hosts setup thanks though, two of them, and they both seem to appear correctly.

> **cdenley said:**
> maybe this will help
```

sudo apt-get install php5-mysql
sudo /etc/init.d/apache2 restart

```

ahhh, This did help, I think, I mean it didn't solve the problem, but I was missing php5-mysql, so that is now installed.  mysql is still not accessible through php as I get the same error as posted before.

Shane

---

