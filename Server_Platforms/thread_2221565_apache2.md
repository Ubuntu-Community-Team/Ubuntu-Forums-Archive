---
title: "apache2"
date: 2014-05-02
forum: Server Platforms
---

### Post by kasper4 on 2014-05-02
Hi guys I'm new to linux / Ubuntu so hope that there is someone who can help me 

I have a problem with apache2 server. it will not boot up and say this. 

I run Ubuntu 12.04 LTS
"
apache2: Syntax error on line 234 of /etc/apache2/apache2.conf: Syntax error on line 43 of /etc/phpmyadmin/apache.conf: /etc/phpmyadmin/apache.conf:43: <Directory> was not closed.
Action 'start' failed.
The Apache error log may have more information.
"

---

### Post by drink1297 on 2014-05-02
You have installed PHPMyAdmin?
Were you able to login to that before the error? Did you change anything in the apache.conf files? Or are you working with 'virtual' servers in apache?

---

### Post by SeijiSensei on 2014-05-02
Time for the "give a man a fish, teach a man to fish" moment.

Let's start with the last line of those errors.  It tells you to look in "the Apache error log."  All the system-level logs in Ubuntu (and most other Linux distributions) are stored under /var/log and are usually readable only by the "root" (admin) user.  So for that you need to use something called "[sudo]("https://help.ubuntu.com/community/RootSudo")."

The Apache logs are stored in /var/log/apache2.  The access.log lists every connection to the server.  The error.log lists errors.  Let's take a look at the last ten lines of that file with a little utility called "tail" that displays the bottom of a text file:
```
sudo tail -n10 /var/log/apache2/error.log
```
That may be helpful, but it may not provide any more information than the errors already displayed.

There are actually two errors being logged, nested inside each other.  The configuration file /etc/apache2/apache2.conf includes the file /etc/phpmyadmin/apache.conf by reference, probably at line 234.  That file has an error concerning a "[<Directory>]("http://httpd.apache.org/docs/2.2/mod/core.html#directory")" container.  Those all start with a "<Directory>" and end with a "</Directory>".  That line is missing in /etc/phpadmin/apache.conf; line 43 is probably at or near the bottom of the file.  

You'll need to edit that file as root with sudo.  From a terminal prompt you can use:
```
sudo nano /etc/phpmyadmin/apache.conf
```
Nano uses Ctrl-key sequences for commands.  There's a convenient menu of them at the bottom of the editing window.  An item like "^X" means hold down the Ctrl key and type "x" to exit the program.  "X" works, too.  You'll be prompted to save the file if it was changed.  See if adding "</VirtualHost>" at line 43 is sufficient to solve the problem.  Use the command "sudo service apache2 restart" after you edit the file.

Even though errors may seem daunting at first, a little thought can often make things clear.  Always look at the logs to see if there is any information that might help, and pay attention to the line number references in any "Syntax errors" you see. Searching Google with the actual error text can also be very helpful as well.

---

### Post by kasper4 on 2014-05-02
Thanks for the quick reply:). I have since tried the uninstall myphpadmin and apache2. and now it gives me a new Faulty code. 

"
* Starting web server apache2 [Fri May 02 23:45:43 2014] [warn] The Alias &#8203;&#8203;Directive in / etc / phpmyadmin / apache.conf at line 3 will probably never match fordi overlaps an tidligere Alias&#8203;&#8203;. 
apache2: Could not reliably Determine the server's fully qualified domain name, Using 127.0.1.1 for ServerName
"

I do not know if this is any help. But have looked in / etc/apache2/apache2.conf and etc / phpmyadmin / apache.conf which is the same in both. 

:(

---

### Post by SeijiSensei on 2014-05-03
For item 2 about the ServerName see [this](https://www.google.com/search?client=ubuntu&channel=fs&q=Could+not+reliably+Determine+the+server%27s+fully+qualified+domain+name%2C+Using+127.0.1.1+for+ServerName&ie=utf-8&oe=utf-8).

For item 1, you must not have removed apache2 like you said since you are now trying to run it.

If this is a brand-new server, I suggest starting over.  Reinstall Ubuntu Server, then install "LAMP" ("Linux/Apache/MySQL/PHP") following [this guide](https://help.ubuntu.com/community/ApacheMySQLPHP) as follows:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install tasksel
sudo tasksel install lamp-server

```
Some or all of the pieces of lamp-server may already be installed, but this is the simplest method to install them all at once.

Now you'll have a server that can run PHP apps like WordPress that use MySQL as a backend.  What do you want to do with it?  On 12.04, I'd start by creating a file called /var/www/info.php like this:
```
sudo echo '<?php phpinfo()?>' > /var/www/info.php
```
Then open a browser on another machine and connect to [http://ip.addr.of.server/info.php](http://ip.addr.of.server/info.php).  You should see a report about your PHP installation.  (On a machine running 14.04, the default site directory has changed to /var/www/html, so you'd want to use that as the parent directory for info.php.)

I'd keep away from phpMyAdmin if you can.  Do you need to create and manage databases?  Or were you just following a guide that said to install phpMyAdmin?

---

