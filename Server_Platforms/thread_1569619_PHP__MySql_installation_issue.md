---
title: "PHP / MySql installation issue"
date: 2010-09-07
forum: Server Platforms
---

### Post by ubunwhat on 2010-09-07
I'm very new to Ubuntu ( day three ) and am having a very puzzling experience with the PHP / MySql installation.  I'll try to give as much detail as possible, so forgive me if I ramble.

I have apache2 / PHP5 / MySql installed and more or less working.  What I mean is that the Apache works, the MySql database works, and Php scripts are being processed.  For instance, phpinfo() renders perfectly.  Also, PhpMyAdmin works just fine.  I am able to log onto the MySql server and perform any necessary function.  But....

When I bring existing sites over I run into a very curious problem.  The .html pages work fine, as do some of the .php pages.  However, any page that calls for a database connection renders.. nothing.  Zip.  Zero.  I'm not even getting an error message even though the connection call is in an if / else loop.  It's just a blank screen.  This makes no sense.  If there were a problem with the configuration then PhpMyAdmin would not work.  The site itself, it's directory structure etc, are all fine as they work perfectly on other servers.  It's like I'm missing the mysqli module in Php, but I configured it exactly as per instructions on this site, and, I am almost certain that phpMyAdmin uses mysqli and that works so... 

Any ideas?

---

### Post by -jrosco- on 2010-09-07
Hi,
 
Its probably your db php script causing problems. You should post the code here.
 
JC

---

### Post by ubunwhat on 2010-09-08
With all due respect, I know that the problem is not in my code.  The error that is showing up in the apache log is specific to being unable to connect to the database.  i stepped back and wrote a fresh, simple, by the book file and it throws the same error.  Specifically, it is throwing the "call to member function on non-object in line #.. " error that occurs when you use a non-existent mysqli connection to prepare a statement and then try to execute it.

I am also getting an error in the log on startup saying that it was unable to load the mysql.so file, which is odd because I know that it is in there.  Either way I am unsure of the relevance as the mysqli.so file is loading fine and I am connecting via mysqli.  This truly has me puzzled as again, phpmyadmin is working flawlessly.

---

### Post by Rusty au Lait on 2010-09-08
Interesting problem. For a new person to ubuntu but not linux I suggest these two links to start with: [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
and
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Are both ubuntu installs fresh? What else is running?

---

### Post by ubunwhat on 2010-09-08
Everything is a fresh install.  I installed the Apache / Php / MySql using the specific instructions from the link you provided...

---

### Post by -jrosco- on 2010-09-08
Check if there are any errors in the mysqli log file. I'm not sure where this log is located, but for mysql its located in /var/mysql/data/hostname.err. This log may indicate a more detailed problem.
 
JC

---

### Post by ubunwhat on 2010-09-09
Efforting...

---

### Post by ubunwhat on 2010-09-09
Is there any way to uninstall PHP5 and reinstall it?  Something has to have gone wrong somewhere.  I tried to uninstall using the instruction in the link "rm php5-common" but am told that php5-common does not exist.  When I try just using "rm /etc/php5" I am told this is not possible as php5 is a directory.  Seriously, is there a reason why it is so difficult to simply uninstall something?

---

### Post by y@w on 2010-09-09
If you're still set on reinstalling, use the package manager. Don't just start rm'ing files, that'll create a bigger mess. You can use 'apt-get remove package' to delete it. But, to rm a directory, you need to do 'rm -r' (recursive). 

Anyway, you're likely just missing a PHP library somewhere. Make sure that log_errors is set to "On" in your php.ini file (default is /etc/php5/apache2/php.ini). Then, there should be errors in /var/log/apache2/error.log. Try tailing that while loading one of the pages that doesn't work. Alternatively, you can change the property display_errors and it should just spit out whatever it's catching on to the web page. You'll likely have to reload the Apache config to apply any changes to php.ini (sudo /etc/init.d/apache2 reload).

---

### Post by ubunwhat on 2010-09-09
I un-installed and re-installed php5 and modules.  No help whatsoever.  I am still having the same problem.  What is most annoying is that phpinfo shows the mysqli module as installed and working.  I just can't make a bloody connection to the database.  Well, unless I am using PhpMyAdmin, which still works flawlessly.  I am literally chasing my tail here...

---

### Post by y@w on 2010-09-09
> **ubunwhat said:**
> I un-installed and re-installed php5 and modules.  No help whatsoever.  I am still having the same problem.  What is most annoying is that phpinfo shows the mysqli module as installed and working.  I just can't make a bloody connection to the database.  Well, unless I am using PhpMyAdmin, which still works flawlessly.  I am literally chasing my tail here...

Re-installing things isn't likely to fix anything.

Have you verified that the credentials given in the application work to connect directly to the database?

---

