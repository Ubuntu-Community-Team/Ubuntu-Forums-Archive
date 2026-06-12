---
title: "Problems with mod_python and apache2"
date: 2007-06-05
forum: Server Platforms
---

### Post by lrhaugen on 2007-06-05
Hi,

I have read a lot of threads about this subject, but I can't find a solution to my problem.

I have installed apache 2, and it works. 
Then I followed this 'tutorial' for mod_python: [http://ubuntuforums.org/showthread.php?t=91101&highlight=mod_python](http://ubuntuforums.org/showthread.php?t=91101&highlight=mod_python)

When restarting the server, I get this error message:
 * Forcing reload of web server (apache2)...                                    
grep: /etc/apache2/mods-enabled/mod_python.load: No such file or directory
grep: /etc/apache2/sites-available/mod_python.load: No such file or directory
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/mod_python.load: No such file or directory                           [fail]

Any ideas?

Thanks!

---

### Post by lrhaugen on 2007-06-05
The server is up and running :-)

---

### Post by laserdevil on 2007-06-19
Hey, what did you do to fix it?

---

### Post by alfonzo on 2007-08-05
I had the same problem and i fixed it by doing the following:

if you look under /etc/apache2/mods-enabled/ you will see that mod_python.load is a sym link to /etc/apache2/mods-available/mod_python.load

when i looked in /etc/apache2/mods-available/ there was no mod_python.load file. 



I created this file and added the following lines to the file:

LoadModule python_module /usr/lib/apache2/modules/mod_python.so


i was then able to start apache2 by running:

sudo apache2 -k start

you can check to see if apache is running by running the command

ps -e | grep apache2 

or by browsing to [http://localhost/](http://localhost/)

---

