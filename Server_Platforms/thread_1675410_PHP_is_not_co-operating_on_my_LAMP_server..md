---
title: "PHP is not co-operating on my LAMP server."
date: 2011-01-25
forum: Server Platforms
---

### Post by KajiMaster on 2011-01-25
I had a working LAMP server on my old server. After a HD went out and was replaced I rebuilt my server with Ubuntu 10.10 server.  Talk about a smooth and impressive install.  I set up my Apache server and MySQL and even installed php5 just like I had done before on my old server.  The only thing different I did with this install is with Apache.  I now host 3 websites with virtual hosts.  This is the only thing different I have done than the last time.

My problem now is my website won't display PHP. I didn't know I had this problem until I installed Drupal for a friend to play around with. Drupal won't finish the installation process because it claims: 

> In your ./sites/default/settings.php file you have configured Drupal to use a server, however your PHP installation currently does not support this database type.

Know I have googled this phrase to hell and back to find a resolution and haven't.  I even talked to my local linux guru at work and he refereed me here.  I have tried reinstalling php left and right.  I'm convinced that there is an option to enable php globally that I'm missing.  I really think the virtual hosts is what is causing this trouble. What input will the mighty Ubuntu community provide me with :)

-Blake

---

### Post by wongo888 on 2011-01-25
Make a phpinfo page and ensure that you have the mysql php connectors installed. If not, install the mysql module for php:

```

$ sudo apt-get install php5-mysql

```

If php wasn't running, you wouldn't see that error.

---

### Post by KajiMaster on 2011-01-26
Thanks for the response Wango888. My website: [www.bentillusions.com](www.bentillusions.com) has the phpinfo code on the main page to demonstrate php doesn't work.  I ran that install you suggested and I already had the latest version of php5.

---

### Post by James78 on 2011-01-26
I went to your site to check something. Your homepage states "my php won't work". So I typed "index.html" in the browser and it worked. Next I typed "index.php" and it was not found. Are you sure the file is named "index.php" and not "index.html"?

---

### Post by KajiMaster on 2011-01-26
James your so right... I over looked naming the .html to .php.  Now when i got to [www.bentillusions.com/index.php](www.bentillusions.com/index.php) it shows my info.  After fixing this I managed to find a website that took me more setting manipulation regarding my Drupal.  Just for the record what I had to do to get my original problem to go away:

> In your ./sites/default/settings.php file you have configured Drupal to use a server, however your PHP installation currently does not support this database type. 

I think this message was not getting that my Database was MYSQL.  In /etc/drupal/6/sites/default/dbconfig.php this file contains all the variables used by the settings.php file to connect to the database.  I'm getting a new error with Drupal saying my database user and pass isn't working but that's a new problem that I think I know how to handle.  Regardless this issue is resolved and closed.  Thank you to those who helped.

---

