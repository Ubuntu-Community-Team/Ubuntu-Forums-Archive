---
title: "PHP Warning:  PHP Startup: Unable to load dynamic library"
date: 2009-04-16
forum: Server Platforms
---

### Post by Micronot on 2009-04-16
I'm just learning php & the lamp stack. I used tasksel. I have the lamp stack installed & have had a few problems. 

For histories sake- I recently solved a problem with the help of the online forums. All my config files were empty- this has now been fixed- for full history see-
[http://ubuntuforums.org/showthread.php?t=1125419](http://ubuntuforums.org/showthread.php?t=1125419)

My main problem now is that I can't get apache to recognize the php code.
- after reviewing my log files- I've determined that, even after reinstalling the config files, I still am missing a number of needed files of a different type. here is the list-

as listed in
	 /var/log/apache2/error.log
I'm missing-
/usr/lib/php5/20060613+lfs/pdo_mysql.so
/usr/lib/php5/20060613+lfs/mysqli.so
/usr/lib/php5/20060613+lfs/mysql.so


as listed in
	/var/log/apache2/error.PHP_test2.log
I'm missing-
~/Desktop/PHP_practice/PHP_test2/favicon.ico


While I don't understand the favicon.ico problem, I'm guessing it's some sort of configuration correction I need to make in apache2. PHP_test2 is the directory that I keep myphp.html 
I'm guessing Apache's expecting to see something other than myphp.html

**Warning:  PHP Startup: Unable to load dynamic library**
The larger problem is the missing files listed from the error.log that cause the error the thread is titled by. 

Does anyone know how I fix these problems?

---

### Post by Micronot on 2009-04-23
Hey
No one answered my post- This is rare. Usually people are pretty helpful.

Admittedly I haven't yet had a chance to fully test my reinstalled LAMP installation as I'm buried in School & real world responsibilities. Anyway, I ended up finding the solution to the missing file issue. I wanted to post it in case anyone ends up with this problem.

Make sure you have the- 
**php5-mysql** 
-package installed as it contains the missing files.

Happy Trails

---

